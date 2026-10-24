# Identity & Access Management (IAM) in Unity Catalog

Unified data governance requires fine-grained access control across data, metadata, and compute clusters using Unity Catalog.

## 1. Governance Principles
* **Principle of Least Privilege (PoLP)**: Users and service principals receive only the minimal permissions required.
* **Group-Based Access**: Permissions are granted exclusively to Entra ID / Okta directory groups, never to individuals.
* **Decoupled Storage Credentials**: End users never receive direct cloud IAM keys to S3/ADLS storage accounts.
