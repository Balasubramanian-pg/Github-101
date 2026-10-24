# Identity & Access Management (IAM) in Unity Catalog

Unified data governance requires fine-grained access control across data, metadata, and compute clusters using Unity Catalog.

## 1. Governance Principles
* **Principle of Least Privilege (PoLP)**: Users and service principals receive only the minimal permissions required.
* **Group-Based Access**: Permissions are granted exclusively to Entra ID / Okta directory groups, never to individuals.
* **Decoupled Storage Credentials**: End users never receive direct cloud IAM keys to S3/ADLS storage accounts.

## 2. Unity Catalog Three-Level Namespace & Securable Hierarchy

```text
Metastore (Single per Cloud Region)
└── Catalog (e.g. prod_lakehouse)
    └── Schema (e.g. silver, gold, quarantine)
        ├── Table (e.g. orders, customers)
        ├── View (e.g. v_daily_revenue)
        ├── Volume (e.g. unstructured_landing)
        └── Function (e.g. mask_ssn)
```

### Securable Object Roles
* **Metastore Admin**: Cloud platform team managing top-level catalogs and storage credentials.
* **Catalog Owner**: Domain lead data engineer managing schemas and table creation rights.
* **Data Steward**: Senior engineer managing data quality and column masking policies.
* **Data Analyst / BI**: Read-only access to curated Gold schemas.
