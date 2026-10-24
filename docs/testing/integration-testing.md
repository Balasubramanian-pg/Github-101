# Integration Testing Architecture

Integration testing validates interactions between the PySpark compute engine, Delta Lake transactional storage, Unity Catalog metadata, and cloud object stores.

## 1. Scope of Integration Testing
While unit tests validate transformation logic in memory, integration tests verify:
* Atomic commits and concurrent writes to Delta Lake tables.
* Auto Loader (`cloudFiles`) ingestion behavior against realistic cloud storage file streams.
* Schema evolution and constraint enforcement in Unity Catalog.
* End-to-end Medallion data flow from Bronze raw landing to Gold dimensional views.

## 2. Ephemeral Sandbox Execution Pattern

Integration tests run against isolated, ephemeral Unity Catalog schemas provisioned dynamically during CI:

```python
# tests/integration/test_pipeline_e2e.py
import uuid
import pytest
from databricks.sdk import WorkspaceClient

@pytest.fixture(scope="module")
def ephemeral_schema(spark):
    schema_name = f"test_ci_{uuid.uuid4().hex[:8]}"
    spark.sql(f"CREATE SCHEMA dev_lakehouse.{schema_name}")
    yield schema_name
    spark.sql(f"DROP SCHEMA dev_lakehouse.{schema_name} CASCADE")
```
