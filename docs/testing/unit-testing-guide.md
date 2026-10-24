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

## 3. Transformation Testing Pattern

Transformations are asserted using column-level and schema equality:

```python
# tests/test_orders_transform.py
from pyspark.sql import types as T
from chispa import assert_df_equality
from src.transformations.orders import conform_orders

def test_conform_orders_cleanses_status_and_timestamps(spark):
    # 1. Arrange: Define synthetic input DataFrame
    input_schema = T.StructType([
        T.StructField("order_id", T.StringType(), True),
        T.StructField("status", T.StringType(), True),
        T.StructField("amount", T.DoubleType(), True),
    ])
    input_data = [("101", " pending ", 49.99), ("102", "SHIPPED", 120.00)]
    input_df = spark.createDataFrame(input_data, schema=input_schema)

    # 2. Act: Execute pure transformation function
    result_df = conform_orders(input_df)

    # 3. Assert: Verify results against expected DataFrame
    expected_data = [("101", "PENDING", 49.99), ("102", "SHIPPED", 120.00)]
    expected_df = spark.createDataFrame(expected_data, schema=input_schema)
    assert_df_equality(result_df, expected_df, ignore_row_order=True)
```

## 4. Edge Case Matrix & Code Coverage Thresholds

Unit tests must explicitly assert edge cases:
* **Nullability**: Columns containing all `NULL` or mixed `NULL` values.
* **Empty DataFrames**: Pipelines must handle 0-row inputs gracefully without raising exceptions.
* **String Edge Cases**: Leading/trailing whitespace, non-ASCII characters, and empty strings.
* **Numeric Extremes**: Negative amounts, divide-by-zero scenarios, and decimal precision overflows.

### Code Coverage Gate
Coverage is measured using `pytest-cov` and enforced at **≥85%**:
```bash
pytest --cov=src --cov-report=term-missing --cov-fail-under=85 tests/unit/
```

## 5. Unit Testing Anti-Patterns to Avoid

| Anti-Pattern | Why It Fails | Lead Engineer Best Practice |
| :--- | :--- | :--- |
| **Connecting to S3/ADLS in unit tests** | Causes flakiness, latency, and requires credentials | Use synthetic in-memory DataFrames |
| **Using `time.sleep()` in tests** | Slows CI builds indeterministically | Use deterministic condition polling or mocks |
| **Testing multiple transformations in one test** | Hard to locate exact failure causes | Write single-assertion, focused unit tests |
| **Calling `.collect()` on large datasets** | Causes local JVM OOM errors | Use `.limit(10)` or small mock datasets |
