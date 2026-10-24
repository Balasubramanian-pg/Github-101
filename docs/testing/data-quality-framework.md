# Data Quality Framework

Data quality is an architectural contract. Incomplete, delayed, or corrupt data must be caught and quarantined at pipeline boundaries before polluting downstream analytical layers.

## 1. Quality Framework Objectives
* **Shift-Left Quality**: Execute assertions during ingestion rather than discovering defects in executive dashboards.
* **Machine-Enforceable Contracts**: Programmatic assertions defined in declarative YAML and tested in CI.
* **Actionable Telemetry**: Centralized quality metrics tracking null rates, distribution shifts, and row volume anomalies.
