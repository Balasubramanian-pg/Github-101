---
name: Bug Report
about: Create a standardized report for pipeline defects, data discrepancies, or infrastructure failures
title: "[BUG]: "
labels: ["bug", "triage"]
assignees: ""
---

### Bug Description
<!-- A clear and concise description of the failure or defect -->

### Severity Level
- [ ] **P0 - Blocker**: Production pipeline halted; Gold data delayed; SLA breached
- [ ] **P1 - Critical**: Corrupted partition; downstream data discrepancies
- [ ] **P2 - Major**: Pipeline retry succeeded; performance degradation
- [ ] **P3 - Minor**: Non-critical metric discrepancy or logging error

### Pipeline & Runtime Context

* **Affected Pipeline**: <!-- e.g., orders_ingest_bronze, customer_360_silver -->
* **Target Environment**:
  - [ ] Production (`prod`)
  - [ ] Staging (`staging`)
  - [ ] Development (`dev`)
* **Databricks Runtime (DBR)**: <!-- e.g., 14.3 LTS (Apache Spark 3.5.0, Scala 2.12) -->
* **Compute Engine**:
  - [ ] Databricks Photon Job Cluster
  - [ ] Databricks Serverless Compute
  - [ ] Single-Node Interactive Cluster
* **Orchestrator Run URL**: <!-- GitHub Actions run URL or Databricks Job Run URL -->

### Reproduction Steps & Minimal Test Script

Steps to reproduce the behavior:
1. Trigger pipeline with input parameter `...`
2. Run transformation step `...`
3. Check table `...` at partition `...`

```python
# Minimal PySpark reproduction script
from pyspark.sql import SparkSession
spark = SparkSession.builder.getOrCreate()
# Reproducible snippet here
```

### Expected Behavior
<!-- What the data or pipeline was expected to produce -->

### Actual Behavior
<!-- What actually happened (e.g. AnalysisException, SchemaMismatchException, incorrect row count) -->

### Data Blast Radius & Impact Analysis

* **Affected Tables**: <!-- list fully-qualified table names: catalog.schema.table -->
* **Impacted Partition(s)**: <!-- e.g., date=2026-10-24 -->
* **Estimated Corrupt Record Count**: <!-- e.g., 50,000 rows -->
* **Downstream Consumers Impacted**:
  - [ ] Power BI / Tableau Executive Dashboards
  - [ ] Customer Feature Store (ML Models)
  - [ ] External Regulatory Reporting Feeds
