# Contributing to the Lead Data Engineering Platform

Thank you for your interest in contributing to the Lead Data Engineering Reference Platform! We maintain the highest standards of code quality, architectural consistency, and operational safety.

## 1. Guiding Principles
* **Code is Ephemeral, Data is Forever**: Pipeline code must prioritize data integrity, deterministic outputs, and idempotent execution above speed of delivery.
* **Shift-Left Validation**: Catch syntax, type, data quality, and schema compatibility errors during local development and CI before compute reaches cloud clusters.
* **Document Every Architectural Tradeoff**: Significant design decisions must be captured in an Architectural Decision Record (ADR) under `docs/adr/`.

## 2. Code of Conduct
We adhere to the Contributor Covenant Code of Conduct. Respectful, collaborative, and constructive feedback during PR reviews is mandatory.

## 3. Branching Strategy & Git Workflow

We follow a strict Trunk-Based Development model with short-lived feature branches:

* `main`: Protected production branch. Direct pushes are blocked.
* Branch Naming Conventions:
  * `feature/<ticket-id>-<short-description>`: New pipelines, transforms, or capabilities.
  * `fix/<ticket-id>-<short-description>`: Bug fixes in logic, transformations, or configs.
  * `data-patch/<ticket-id>-<table-name>`: Emergency schema migrations or backfill scripts.
  * `infra/<ticket-id>-<resource>`: Changes to Terraform, DABs, or cluster policies.
  * `docs/<topic>`: Documentation enhancements.

### Commit Message Standards
We follow [Conventional Commits](https://www.conventionalcommits.org/):
```
<type>(<scope>): <subject>

[optional body]

[optional footer(s)]
```
* **Types**: `feat`, `fix`, `docs`, `style`, `refactor`, `perf`, `test`, `build`, `ci`, `chore`, `revert`.
* **Scopes**: `spark`, `delta`, `dabs`, `iac`, `dq`, `catalog`, `security`, `runbook`.
* **Example**: `feat(spark): implement vectorized bronze ingestion for orders telemetry`

## 4. Coding & Engineering Standards

### Python & PySpark Guidelines
* **Type Annotations**: All functions must have complete type hints validated with `mypy`.
* **Pure Transformation Functions**: Isolate PySpark transformations into pure functions accepting and returning `DataFrame`. Avoid side effects.
* **Avoid Python UDFs**: Use native Spark SQL functions or Pandas UDFs (vectorized with Arrow) when custom scalar logic is unavoidable.
* **Linting & Formatting**: Enforced via `ruff` and `black`. Line length is set to 100 characters.

```python
# Standard Pure Transformation Signature
from pyspark.sql import DataFrame
import pyspark.sql.functions as F

def transform_silver_orders(bronze_df: DataFrame) -> DataFrame:
    """Conform and enrich orders from bronze to silver layer."""
    return (
        bronze_df
        .filter(F.col("order_id").isNotNull())
        .withColumn("processed_at", F.current_timestamp())
    )
```

### SQL Standards
* Use ANSI SQL standards validated via `sqlfluff` configured for Databricks / Spark SQL dialect.
* All keywords must be UPPERCASE. Indentation is 4 spaces.

## 5. Testing & Quality Assurance Gates

Every PR must pass automated CI checks before review:
1. **Unit Tests**: Minimum 85% code coverage for Python transformation modules using `pytest`.
2. **Data Quality Assertions**: Data contracts verified with Great Expectations or Soda Core suites.
3. **Synthetic Test Data**: Use `dbldatagen` or synthetic generators (`docs/testing/mock-data-generation.md`). Never commit real customer data or PII to the repository.
4. **Schema Evolution Check**: Run `pytest tests/test_schema_evolution.py` to assert backward compatibility against baseline Delta schemas.
