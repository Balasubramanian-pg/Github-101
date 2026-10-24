# ADR 001: Orchestration Architecture Selection

## Status
Accepted

## Context
The platform requires an orchestrator to manage CI/CD pipelines, automated testing, Databricks Asset Bundle deployments, and scheduled data ingestion workflows. We evaluated whether to maintain a standalone workflow orchestrator (Apache Airflow / MWAA) or leverage GitHub Actions combined with Databricks Workflows.
