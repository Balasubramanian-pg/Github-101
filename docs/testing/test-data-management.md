# Test Data Lifecycle & Fixture Management

Managing test data across hundreds of pipeline runs requires strict lifecycle controls, automated cleanup procedures, and clear segregation between golden test baselines and ephemeral run artifacts.

## 1. Principles of Test Data Management
* **Immutability of Golden Fixtures**: Golden reference datasets are read-only and version-controlled.
* **Hermetic Sandbox Isolation**: Each test execution creates an isolated storage prefix and Unity Catalog namespace.
* **Automated Ephemeral Teardown**: Test assets are destroyed immediately following test execution.

## 2. Test Fixture Hierarchy

```text
tests/
├── fixtures/
│   ├── contracts/                    # Schema contract YAMLs
│   │   └── orders_contract_v1.yml
│   ├── golden/                       # Minimal, immutable golden test files
│   │   ├── bronze_orders_sample.parquet
│   │   └── reference_customers.csv
│   └── synthetic/                    # Generation scripts for large fixtures
│       └── generate_performance_suite.py
```
