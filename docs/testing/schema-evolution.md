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
