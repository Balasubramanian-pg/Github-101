# ADR 001: Orchestration Architecture Selection

## Status
Accepted

## Context
The platform requires an orchestrator to manage CI/CD pipelines, automated testing, Databricks Asset Bundle deployments, and scheduled data ingestion workflows. We evaluated whether to maintain a standalone workflow orchestrator (Apache Airflow / MWAA) or leverage GitHub Actions combined with Databricks Workflows.

## Evaluated Alternatives

1. **Apache Airflow (Managed MWAA / Astro)**
   * *Pros*: Rich Python DAG ecosystem, mature backfill capabilities.
   * *Cons*: High fixed operational cost ($400+/month base), separate repository for DAGs, complex local development, distinct IAM credentials required.
2. **Prefect / Dagster**
   * *Pros*: Modern Python-centric abstractions, dynamic task mapping.
   * *Cons*: Requires separate control plane, additional licensing, organizational overhead.
3. **GitHub Actions + Databricks Workflows (Selected Architecture)**
   * *Pros*: Native integration with source code, zero server maintenance, OIDC security, native Databricks Asset Bundle support, pay-as-you-go execution.

## Decision Drivers & Evaluation Matrix

| Criterion (Weight: 1-5) | Airflow | GitHub Actions + Databricks Workflows |
| :--- | :--- | :--- |
| **Operational Overhead (5)** | 2/5 (Requires VM management / upgrades) | **5/5 (Fully serverless)** |
| **CI/CD Integration (5)** | 2/5 (Decoupled from code push) | **5/5 (Native PR triggers & checks)** |
| **Identity & Security (4)** | 3/5 (Static credentials / IAM roles) | **5/5 (Keyless OIDC federation)** |
| **Cost Efficiency (4)** | 2/5 (Always-on worker instances) | **5/5 (Zero idle cost)** |
| **Spark Native Orchestration (4)** | 3/5 (External API polling) | **5/5 (Databricks Workflows native)** |

## Decision
We adopt a **Two-Tier Orchestration Architecture**:
1. **GitHub Actions**: Serves as the primary deployment and verification orchestrator. Handles linting, unit testing, contract assertions, container builds, and Databricks Asset Bundle deployment (`databricks bundle deploy`).
2. **Databricks Workflows**: Serves as the internal DAG scheduler for distributed Spark pipelines, multi-task dependencies, and continuous streaming jobs.
