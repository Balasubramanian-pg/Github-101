# Mock Data Generation Architecture

Testing distributed data pipelines requires realistic, high-volume, and structurally sound datasets without exposing sensitive customer PII or violating data privacy regulations.

## 1. Motivation & Regulatory Compliance
* **Zero Production Data in Non-Prod**: GDPR, CCPA, and HIPAA prohibit copying live customer data into dev/test environments.
* **Deterministic Reproducibility**: Unit and integration tests must produce identical results on every test run.
* **Stress & Skew Simulation**: Ability to synthesize millions of rows with configurable data skew, null bursts, and late-arriving events.
