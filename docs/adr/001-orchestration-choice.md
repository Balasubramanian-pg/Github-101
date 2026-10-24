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
