# Self-Hosted Runners Architecture

While GitHub-hosted runners handle standard linting and unit testing, specialized data platform tasks require private network access to internal databases, cloud VPCs, and on-premises storage.

## 1. When to Use Self-Hosted Runners
* **Private Network Egress**: Deploying to Databricks workspaces enclosed in private subnets with no public IP.
* **On-Premise Ingest Validation**: Running integration tests against private Oracle/SQL Server data sources.
* **Cost Optimization for High-Compute CI**: Executing GPU or high-memory data generation benchmarks.
