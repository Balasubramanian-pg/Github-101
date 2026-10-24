# Runbook: Alert Triage & Diagnostics

This runbook guides on-call engineers through triaging alerts, differentiating actionable failures from transient cloud noise, and diagnosing Spark and Delta Lake runtime errors rapidly.

## 1. Golden Rules of Alert Triage
* **Every Alert Must Be Actionable**: If an alert does not require immediate human intervention, delete or downgrade it.
* **Verify Customer Impact First**: Check downstream BI dashboards and customer APIs before diving into low-level logs.
* **Do Not Restart Blindly**: Always capture diagnostic stack traces before restarting failed clusters.
