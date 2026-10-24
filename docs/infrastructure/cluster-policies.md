# Cluster Policies Architecture

Cluster policies enforce operational guardrails, cost controls, security requirements, and architectural standards on user-created and automated compute clusters in Databricks.

## 1. Objectives of Cluster Policies
* Prevent developers from inadvertently provisioning massive, high-cost multi-node GPU clusters.
* Enforce automatic termination on all interactive compute.
* Standardize on Long-Term Support (LTS) Databricks Runtimes.
* Mandate cost attribution tags across all clusters.
