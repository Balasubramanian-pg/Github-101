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
