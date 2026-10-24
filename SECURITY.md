# Security Policy

The Lead Data Engineering Platform manages enterprise analytical assets, metadata, and data pipelines. We maintain a zero-trust security architecture across compute, storage, and identity layers.

## 1. Supported Versions
Security updates are continuously applied to active branches:

| Version Branch | Supported | Security Patch Delivery |
| :--- | :--- | :--- |
| `main` (Production) | :white_check_mark: | Immediate hotfix (< 24 hours for Critical) |
| `release/v2.*` (Staging) | :white_check_mark: | Next deployment cycle (< 48 hours) |
| `release/v1.*` (Legacy) | :x: | End-of-Life. Please upgrade to v2.x |
