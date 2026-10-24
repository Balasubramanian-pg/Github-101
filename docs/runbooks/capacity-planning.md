# Runbook: Capacity Planning & Infrastructure Sizing

Capacity planning ensures the data platform proactively accommodates data volume expansion, query throughput growth, and storage lifecycle transitions without unexpected performance degradation or budget overruns.

## 1. Objectives of Capacity Planning
* Forecast compute and storage consumption over 6-month and 12-month horizons.
* Identify compute bottlenecks before they breach production SLAs.
* Transition aging raw data to cold storage to optimize lakehouse economics.

## 2. Growth Forecasting Metrics & Key Indicators

We track four core capacity indicators:

| Indicator | Tracking Source | Warning Threshold | Action Triggered |
| :--- | :--- | :--- | :--- |
| **Daily Ingest Volume** | Cloud Storage metrics | > 20% month-over-month growth | Review worker node autoscaling bounds |
| **Shuffle Spill to Disk** | Spark UI executor metrics | > 10 GB spill per batch | Increase worker memory or repartition keys |
| **Delta Log Size** | `_delta_log` metadata | > 100,000 files in log | Review checkpoint and VACUUM frequencies |
| **Job Duration Drift** | Databricks Job Run telemetry | Duration > 80% of SLA window | Rightsizing cluster or enable Photon |
