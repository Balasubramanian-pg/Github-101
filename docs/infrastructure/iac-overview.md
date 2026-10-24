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

## 3. Terraform Directory Layout

```text
terraform/
├── modules/
│   ├── networking/          # VPC, Private Subnets, Route Tables
│   ├── storage/             # ADLS Gen2 / AWS S3 buckets, KMS encryption
│   ├── unity_catalog/       # Metastore, storage credentials, external locations
│   └── iam_roles/           # OIDC federated trust roles, service principals
└── environments/
    ├── dev/                 # Development environment state & variables
    ├── staging/             # Pre-production environment state & variables
    └── prod/                # Production environment state & variables
```

## 4. State Management & Concurrency Locking

Terraform remote state is stored securely in encrypted cloud storage with distributed locking:
* **Storage Backend**: AWS S3 with AES-256 server-side encryption and bucket versioning / Azure Blob Storage.
* **State Locking**: DynamoDB table locking / Azure Blob lease prevents concurrent conflicting executions.
* **Access Control**: State buckets require MFA and exclude direct human write permissions.

## 5. Automated CI/CD Pipeline for IaC

Every Terraform pull request undergoes automated scanning:
1. `terraform fmt -check`: Verifies code formatting.
2. `tflint`: Validates cloud provider syntax and best practices.
3. `trivy config .`: Scans for security misconfigurations and exposed ports.
4. `terraform plan`: Generates execution plan and posts formatted diff directly to PR comments.
5. `terraform apply`: Executed only upon merge to `main` via automated OIDC runners.
