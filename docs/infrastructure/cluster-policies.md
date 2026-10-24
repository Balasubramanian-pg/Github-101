# Cluster Policies Architecture

Cluster policies enforce operational guardrails, cost controls, security requirements, and architectural standards on user-created and automated compute clusters in Databricks.

## 1. Objectives of Cluster Policies
* Prevent developers from inadvertently provisioning massive, high-cost multi-node GPU clusters.
* Enforce automatic termination on all interactive compute.
* Standardize on Long-Term Support (LTS) Databricks Runtimes.
* Mandate cost attribution tags across all clusters.

## 2. Standard Policy Taxonomy

We enforce three core cluster policies across the enterprise:

| Policy Name | Target Workload | Max Nodes | Auto-Termination | Worker Instance Family |
| :--- | :--- | :--- | :--- | :--- |
| **Personal Interactive** | Ad-hoc EDA & notebook testing | Single-Node (0 workers) | **15 minutes** | General purpose (8-16 GB RAM) |
| **Team Collaborative** | Shared departmental development | 4 workers | **30 minutes** | Memory optimized (32 GB RAM) |
| **Automated Batch Job** | Production pipelines & CI/CD | Autoscaling (1-8 nodes) | Immediate on completion | Compute optimized (Photon enabled) |
