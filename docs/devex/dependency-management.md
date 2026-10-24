# Dependency Management & Supply Chain Architecture

Managing third-party Python packages across distributed data platforms requires strict lockfiles, cryptographic hash validation, and Databricks Runtime compatibility to guarantee reproducibility and prevent supply chain attacks.

## 1. Guiding Principles
* **Strict Lockfiles**: Every dependency and transitive dependency is pinned to an exact version and SHA-256 hash.
* **Zero Direct `pip install` on Clusters**: Libraries are packaged into wheel artifacts or deployed via Databricks Asset Bundles.
* **Automated Vulnerability Auditing**: Automated PR scans detect outdated or vulnerable packages before merge.
