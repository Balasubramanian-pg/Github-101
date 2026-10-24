# Contributing to the Lead Data Engineering Platform

Thank you for your interest in contributing to the Lead Data Engineering Reference Platform! We maintain the highest standards of code quality, architectural consistency, and operational safety.

## 1. Guiding Principles
* **Code is Ephemeral, Data is Forever**: Pipeline code must prioritize data integrity, deterministic outputs, and idempotent execution above speed of delivery.
* **Shift-Left Validation**: Catch syntax, type, data quality, and schema compatibility errors during local development and CI before compute reaches cloud clusters.
* **Document Every Architectural Tradeoff**: Significant design decisions must be captured in an Architectural Decision Record (ADR) under `docs/adr/`.

## 2. Code of Conduct
We adhere to the Contributor Covenant Code of Conduct. Respectful, collaborative, and constructive feedback during PR reviews is mandatory.

## 3. Branching Strategy & Git Workflow

We follow a strict Trunk-Based Development model with short-lived feature branches:

* `main`: Protected production branch. Direct pushes are blocked.
* Branch Naming Conventions:
  * `feature/<ticket-id>-<short-description>`: New pipelines, transforms, or capabilities.
  * `fix/<ticket-id>-<short-description>`: Bug fixes in logic, transformations, or configs.
  * `data-patch/<ticket-id>-<table-name>`: Emergency schema migrations or backfill scripts.
  * `infra/<ticket-id>-<resource>`: Changes to Terraform, DABs, or cluster policies.
  * `docs/<topic>`: Documentation enhancements.

### Commit Message Standards
We follow [Conventional Commits](https://www.conventionalcommits.org/):
```
<type>(<scope>): <subject>

[optional body]

[optional footer(s)]
```
* **Types**: `feat`, `fix`, `docs`, `style`, `refactor`, `perf`, `test`, `build`, `ci`, `chore`, `revert`.
* **Scopes**: `spark`, `delta`, `dabs`, `iac`, `dq`, `catalog`, `security`, `runbook`.
* **Example**: `feat(spark): implement vectorized bronze ingestion for orders telemetry`
