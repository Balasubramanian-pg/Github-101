# Mock Data Generation Architecture

Testing distributed data pipelines requires realistic, high-volume, and structurally sound datasets without exposing sensitive customer PII or violating data privacy regulations.

## 1. Motivation & Regulatory Compliance
* **Zero Production Data in Non-Prod**: GDPR, CCPA, and HIPAA prohibit copying live customer data into dev/test environments.
* **Deterministic Reproducibility**: Unit and integration tests must produce identical results on every test run.
* **Stress & Skew Simulation**: Ability to synthesize millions of rows with configurable data skew, null bursts, and late-arriving events.

## 2. Tooling Landscape

We leverage two complementary tools for mock data generation:
1. **Faker / Mimesis**: Ideal for generating realistic scalar entity attributes (names, addresses, UUIDs) for unit test fixtures.
2. **Databricks Labs Data Generator (`dbldatagen`)**: Native distributed data synthesis on Spark for multi-million row integration and performance tests.

## 3. High-Volume Synthetic Data Generation Recipe

Using `dbldatagen`, we synthesize millions of realistic order transactions directly on Spark:

```python
import dbldatagen as dg
from pyspark.sql import SparkSession

def generate_mock_orders(spark: SparkSession, row_count: int = 1_000_000):
    data_spec = (
        dg.DataGenerator(spark, rows=row_count, partitions=8, randomSeed=42)
        .withIdForTable()
        .withColumn("order_id", "string", template="ORD-%08d")
        .withColumn("customer_id", "string", template="CUST-%06d", random=True)
        .withColumn("order_status", "string", values=["PENDING", "CONFIRMED", "SHIPPED", "DELIVERED", "CANCELLED"], 
                    weights=[0.1, 0.2, 0.4, 0.25, 0.05])
        .withColumn("total_amount", "decimal(10,2)", minValue=5.00, maxValue=2500.00, random=True)
        .withColumn("order_date", "date", begin="2026-01-01", end="2026-10-24", random=True)
    )
    return data_spec.build()
```

## 4. Controlled Anomaly & Edge Case Injection

Synthetic data generators support controlled defect injection to test pipeline resilience:

```python
def inject_anomalies(clean_df):
    """Inject synthetic corruption to validate data quality quarantine gates."""
    import pyspark.sql.functions as F
    
    return clean_df.withColumn(
        "order_status",
        F.when(F.rand() < 0.02, "INVALID_STATUS_CODE") # 2% corrupt status
        .otherwise(F.col("order_status"))
    ).withColumn(
        "total_amount",
        F.when(F.rand() < 0.01, -99.99)               # 1% negative amounts
        .otherwise(F.col("total_amount"))
    )
```

## 5. Test Dataset Seeding & Clean Air Gap Policy

### Deterministic Seeding Rule
All synthetic generation scripts must specify a fixed integer seed (`randomSeed=42` / `Faker.seed(42)`). Randomness without fixed seeds creates non-deterministic test failures in CI.

### Air Gap Audit
Every test artifact directory is audited pre-merge to verify zero un-redacted PII (Social Security numbers, credit card numbers, email addresses) using automated regex scanners (`trufflehog` and `git-secrets`).
