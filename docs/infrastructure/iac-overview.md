# Infrastructure as Code (IaC) Architecture

Modern lakehouse infrastructure is provisioned and governed exclusively through Infrastructure as Code (IaC). Manual configuration via cloud consoles is strictly forbidden.

## 1. Guiding Principles
* **Declarative Cloud Architecture**: Entire infrastructure declared in Terraform and Databricks Asset Bundles.
* **Separation of Concerns**: Cloud foundational infrastructure (networking, storage, IAM) is decoupled from data pipeline workloads (jobs, clusters, DLT pipelines).
* **Automated Drift Detection**: Weekly automated jobs detect and alert on unauthorized out-of-band changes.

## 2. Tooling Scope & Boundaries

We establish a clear boundary between Terraform and Databricks Asset Bundles (DABs):

| Layer | Primary Tool | Managed Cloud Resources | Deployment Cadence |
| :--- | :--- | :--- | :--- |
| **Cloud Foundation** | **Terraform** | VPCs, Subnets, NAT Gateways, Storage Accounts, Cloud IAM Roles, KMS Keys | Monthly / As Needed |
| **Workspace Governance** | **Terraform** | Databricks Workspaces, Unity Catalog Metastores, Cloud Storage Credentials | Bi-Weekly |
| **Data Pipelines & Jobs**| **Databricks Asset Bundles**| Workflows, Pipelines, Notebooks, Spark Tasks, Cluster Policies | Daily / Per PR |
