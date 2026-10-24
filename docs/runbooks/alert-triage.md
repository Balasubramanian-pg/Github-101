# Runbook: Alert Triage & Diagnostics

This runbook guides on-call engineers through triaging alerts, differentiating actionable failures from transient cloud noise, and diagnosing Spark and Delta Lake runtime errors rapidly.

## 1. Golden Rules of Alert Triage
* **Every Alert Must Be Actionable**: If an alert does not require immediate human intervention, delete or downgrade it.
* **Verify Customer Impact First**: Check downstream BI dashboards and customer APIs before diving into low-level logs.
* **Do Not Restart Blindly**: Always capture diagnostic stack traces before restarting failed clusters.

## 2. Common Data Platform Failures Matrix

| Alert Message | Root Cause | Immediate Action |
| :--- | :--- | :--- |
| **`ConcurrentAppendException`** | Two jobs writing to identical Delta partition concurrently | Verify job schedules; Delta OCC will retry automatically |
| **`SparkException: Job aborted due to stage failure`** | Worker node failure or memory leak | Inspect Spark UI executor tab for Out of Memory (OOM) |
| **`DeltaConcurrentModificationException`** | Conflicting file compaction / update | Check if OPTIMIZE job collided with batch write |
| **`CloudFilesSourceException`** | Corrupt JSON/Parquet file in landing storage | Move file to quarantine storage; unblock stream |
