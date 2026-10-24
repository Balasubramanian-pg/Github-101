# Data Quality Framework

Data quality is an architectural contract. Incomplete, delayed, or corrupt data must be caught and quarantined at pipeline boundaries before polluting downstream analytical layers.

## 1. Quality Framework Objectives
* **Shift-Left Quality**: Execute assertions during ingestion rather than discovering defects in executive dashboards.
* **Machine-Enforceable Contracts**: Programmatic assertions defined in declarative YAML and tested in CI.
* **Actionable Telemetry**: Centralized quality metrics tracking null rates, distribution shifts, and row volume anomalies.

## 2. Tri-Tier Quality Severity Model

We categorize data quality assertions into three operational tiers:

| Tier | Severity | Action on Breach | Example Assertions |
| :--- | :--- | :--- | :--- |
| **Tier 1: Fatal** | Critical | **Halt pipeline immediately**; quarantine batch; page on-call engineer | Duplicate primary key, NULL foreign key, invalid schema |
| **Tier 2: Warning** | High | **Route records to quarantine**; continue pipeline; post Slack alert | Value outside expected historical range, unusual null percentage |
| **Tier 3: Drift** | Informational | Record metric to telemetry table; trigger automated trend analysis | Row count variance > 15% vs 7-day rolling average |

## 3. Data Quality Gate Architecture

```mermaid
flowchart TD
    A["Bronze Cleaned Stream"] --> B["Tier 1: Fatal Assertions (Primary Keys, Schema)"]
    B --> C{"Fatal Checks Pass?"}
    C -- No --> D["HALT PIPELINE & Page On-Call (PagerDuty)"]
    C -- Yes --> E["Tier 2: Semantic Assertions (Business Rules, Contracts)"]
    E --> F{"Record Valid?"}
    F -- No --> G["Route to quarantine.orders_dq_breach"]
    F -- Yes --> H["Silver Merge Destination"]
    E --> I["Tier 3: Emit DQ Metrics to metadata.dq_telemetry"]
    G --> I
    H --> I
```
