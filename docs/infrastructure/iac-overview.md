# Infrastructure as Code (IaC) Architecture

Modern lakehouse infrastructure is provisioned and governed exclusively through Infrastructure as Code (IaC). Manual configuration via cloud consoles is strictly forbidden.

## 1. Guiding Principles
* **Declarative Cloud Architecture**: Entire infrastructure declared in Terraform and Databricks Asset Bundles.
* **Separation of Concerns**: Cloud foundational infrastructure (networking, storage, IAM) is decoupled from data pipeline workloads (jobs, clusters, DLT pipelines).
* **Automated Drift Detection**: Weekly automated jobs detect and alert on unauthorized out-of-band changes.
