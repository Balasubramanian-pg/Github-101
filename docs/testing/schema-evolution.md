# Schema Evolution & Backward Compatibility

Managing schema changes safely across large-scale distributed datasets is critical. Unplanned schema modifications can break downstream ETL pipelines, reporting dashboards, and machine learning models.

## 1. Guiding Principles
* **Schema Enforcement by Default**: Reject unexpected columns and mismatched data types at ingestion boundaries.
* **Controlled Evolution**: Enable `mergeSchema` exclusively for planned, backward-compatible additions.
* **Zero Breaking Changes Without Notice**: Modifications that break consumers require a 30-day deprecation cycle.

## 2. Schema Change Compatibility Matrix

| Schema Operation | Compatibility Classification | Evolution Strategy | Downstream Impact |
| :--- | :--- | :--- | :--- |
| **Add Nullable Column** | **Backward-Compatible** | Auto-evolve via `mergeSchema` | Safe; consumers ignore new column |
| **Add Non-Nullable Column**| **BREAKING** | Forbidden without default value | Fails inserts without default value |
| **Rename Column** | **BREAKING** | Dual-write pattern with deprecation | Breaks queries referencing old name |
| **Drop Column** | **BREAKING** | 30-day deprecation notice required | Queries referencing column fail |
| **Widen Type (`INT` -> `BIGINT`)** | **Backward-Compatible** | Safe promotion | Downstream readers handle wider type |
| **Narrow Type (`BIGINT` -> `INT`)**| **BREAKING** | Forbidden | Data truncation / runtime exceptions |

## 3. Safe Column Renaming / Deprecation Flow

```mermaid
sequenceDiagram
    autonumber
    participant DEV as Data Engineer
    participant PR as Pull Request & CI Check
    participant BRZ as Bronze / Silver Table
    participant CON as Downstream Readers / BI

    DEV->>PR: Propose renaming 'user_name' to 'customer_name'
    PR-->>DEV: Flag BREAKING CHANGE: Trigger 3-Stage Migration
    rect rgb(240, 248, 255)
        note over DEV,CON: Phase 1: Dual-Write (Week 1 - 4)
        DEV->>BRZ: Write to both 'user_name' AND 'customer_name'
        DEV->>CON: Notify consumers to migrate to 'customer_name'
    end
    rect rgb(255, 250, 240)
        note over DEV,CON: Phase 2: Deprecation Notice (Week 4)
        CON->>CON: Update all SQL queries to reference 'customer_name'
    end
    rect rgb(255, 240, 245)
        note over DEV,CON: Phase 3: Column Retirement (Week 5)
        DEV->>BRZ: Stop writing to 'user_name' (Set to NULL or drop)
    end
```

## 4. Controlled Evolution Implementation in PySpark

To safely ingest additive columns into Delta Lake:

```python
# Controlled schema evolution write configuration
(conformed_df.write
    .format("delta")
    .mode("append")
    .option("mergeSchema", "true")  # Allows additive nullable columns
    .saveAsTable("silver.orders"))
```

### Pre-Merge CI Schema Compatibility Test
A dedicated CI test verifies PR schema compatibility against production schemas:
```python
def test_schema_backward_compatibility(spark):
    prod_schema = spark.read.table("prod_lakehouse.silver.orders").schema
    pr_schema = get_current_pipeline_schema()
    
    # Assert all prod columns exist in PR schema with matching data types
    for field in prod_schema.fields:
        assert field.name in pr_schema.fieldNames(), f"Breaking: Column {field.name} was removed!"
        pr_field = pr_schema[field.name]
        assert pr_field.dataType == field.dataType, f"Breaking: Type changed for {field.name}"
```

## 5. Governance Checklist for Breaking Schema Changes

Before merging any PR flagged with breaking schema modifications:
- [ ] Schema impact analysis completed in `.github/pull_request_template.md`.
- [ ] Downstream consumer stakeholders notified across Slack and email.
- [ ] Unity Catalog column tags updated (`status: deprecated`, `eol_date: 2026-12-01`).
- [ ] Written approval granted by the Lead Platform Architect.
