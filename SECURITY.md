# Security Policy

The Lead Data Engineering Platform manages enterprise analytical assets, metadata, and data pipelines. We maintain a zero-trust security architecture across compute, storage, and identity layers.

## 1. Supported Versions
Security updates are continuously applied to active branches:

| Version Branch | Supported | Security Patch Delivery |
| :--- | :--- | :--- |
| `main` (Production) | :white_check_mark: | Immediate hotfix (< 24 hours for Critical) |
| `release/v2.*` (Staging) | :white_check_mark: | Next deployment cycle (< 48 hours) |
| `release/v1.*` (Legacy) | :x: | End-of-Life. Please upgrade to v2.x |

## 2. Reporting a Vulnerability

**DO NOT file public GitHub issues for security vulnerabilities.**

To report a vulnerability privately:
1. Navigate to the **Security** tab of this repository.
2. Click **Report a vulnerability** to open a draft GitHub Security Advisory.
3. Alternatively, email the Platform Security Team at `security-data-platform@example.com` encrypted with our PGP Key:
   ```
   Key ID: 0x9B4E6F21C8A34D12
   Fingerprint: 4E92 A1D8 B720 C549 33E1  820F 9B4E 6F21 C8A3 4D12
   ```

### Report Information Required
* Detailed description of the vulnerability.
* Affected components (e.g. Databricks Asset Bundle, cluster policy, OIDC workflow, Delta table).
* Proof of concept or reproduction script.
* Assessment of blast radius and data exposure risk.

## 3. Vulnerability Response Timeline & SLAs

We adhere to rigorous incident response timelines based on CVSS v3.1 severity scores:

| Severity Level | CVSS Range | Initial Acknowledgment | Triage & Assessment | Remediation SLA |
| :--- | :--- | :--- | :--- | :--- |
| **Critical** | 9.0 - 10.0 | < 2 hours | < 12 hours | < 24 hours |
| **High** | 7.0 - 8.9 | < 6 hours | < 24 hours | < 72 hours |
| **Medium** | 4.0 - 6.9 | < 24 hours | < 48 hours | < 14 calendar days |
| **Low** | 0.1 - 3.9 | < 48 hours | < 5 business days | < 30 calendar days |

## 4. Platform Threat Model & Security Controls

Our security framework addresses critical data platform threat vectors:

* **Credential Compromise**: Static long-lived tokens are strictly forbidden. All CI/CD pipelines authenticate to cloud providers via OIDC Workload Identity Federation (`docs/cicd/oidc-integration.md`).
* **Data Exfiltration**: Databricks workspaces and cloud storage accounts enforce Private Link / Private Endpoints without public internet egress (`docs/infrastructure/network-topology.md`).
* **PII & Data Masking**: All sensitive columns (SSN, credit card, email) are tokenized at the Bronze ingestion boundary using Unity Catalog Column-Level Masking.
* **Dependency Poisoning**: All Python dependencies are pinned with SHA-256 hashes and audited using Trivy and Dependabot (`docs/security/vulnerability-scanning.md`).

## 5. Coordinated Disclosure & Hall of Fame

* We follow coordinated vulnerability disclosure principles. We request researchers allow 90 days before disclosing details publicly.
* Verified security contributors who report novel vulnerabilities adhering to this policy will be recognized in our Security Hall of Fame.
* For credential rotation procedures following a confirmed compromise, refer to [Secret Rotation Runbook](docs/security/secret-rotation.md).
