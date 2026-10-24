# Unit Testing Guide for PySpark Pipelines

Unit testing distributed data pipelines requires isolating business logic from distributed cluster runtimes and cloud storage dependencies.

## 1. Core Testing Philosophy
* **Pure Transformation Functions**: Extract transformation logic into deterministic functions that take a `DataFrame` as input and return a `DataFrame`.
* **Zero Cloud Dependencies**: Unit tests must run locally and in GitHub Actions runners without requiring active Databricks clusters or cloud credentials.
* **Fast Execution**: Entire unit test suite must execute in under 60 seconds.

## 2. Local PySpark Test Fixture Configuration

We configure a lightweight, local-mode `SparkSession` using Pytest fixtures:

```python
# tests/conftest.py
import pytest
from pyspark.sql import SparkSession

@pytest.fixture(scope="session")
def spark() -> SparkSession:
    """Provide a lightweight, local-mode SparkSession for unit testing."""
    return (
        SparkSession.builder
        .master("local[2]")
        .appName("unit-tests")
        .config("spark.sql.shuffle.partitions", "1")
        .config("spark.default.parallelism", "1")
        .config("spark.ui.enabled", "false")
        .config("spark.sql.session.timeZone", "UTC")
        .getOrCreate()
    )
```
