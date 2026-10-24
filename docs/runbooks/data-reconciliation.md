# Runbook: Data Reconciliation & Backfill

Data reconciliation verifies integrity, row-count completeness, and attribute fidelity across pipeline stages following outages, upstream source retries, or emergency rollbacks.

## 1. When to Perform Reconciliation
* Immediately following an [Emergency Rollback](emergency-rollback.md).
* When upstream Kafka / API producers report replayed or duplicate event batches.
* When data quality telemetry indicates a drift breach > 5% in historical partitions.

## 2. Reconciliation Methodologies

We employ three validation techniques:
1. **Row Count & Volume Parity**: Verifying Bronze vs Silver row counts after accounting for filtered quarantine records.
2. **Cryptographic Checksumming**: Hashing conjoined primary keys and critical business values to verify zero mutation.
3. **Aggregated Financial Rollup Comparison**: Recomputing daily revenue metrics in Gold and comparing against source ledger totals.
