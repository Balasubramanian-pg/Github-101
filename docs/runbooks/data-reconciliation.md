# Runbook: Data Reconciliation & Backfill

Data reconciliation verifies integrity, row-count completeness, and attribute fidelity across pipeline stages following outages, upstream source retries, or emergency rollbacks.

## 1. When to Perform Reconciliation
* Immediately following an [Emergency Rollback](emergency-rollback.md).
* When upstream Kafka / API producers report replayed or duplicate event batches.
* When data quality telemetry indicates a drift breach > 5% in historical partitions.
