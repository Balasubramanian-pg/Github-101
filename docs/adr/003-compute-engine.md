# ADR 003: Distributed Compute Engine Architecture

## Status
Accepted

## Context
The platform requires a scalable distributed compute engine capable of handling high-volume ETL transformations, streaming ingest, and complex dimensional modeling with predictable costs and strict SLA compliance.

## Evaluated Compute Engines

1. **Databricks (Photon & Serverless Compute)**
   * Managed Spark platform with vectorized C++ Photon execution engine.
   * Auto-scaling, rapid cluster spin-up, and native Unity Catalog governance.
2. **AWS EMR / Google Cloud Dataproc**
   * Traditional managed Hadoop/Spark clusters.
   * Requires cluster sizing, bootstrapping scripts, and manual patch management.
3. **Snowflake**
   * Excellent for SQL transformations and data warehousing.
   * Higher cost for heavy unstructured/semi-structured file processing and custom Python logic.

## Evaluation Criteria

* **Execution Performance**: Vectorized execution capability for complex aggregations.
* **Cold-Start Latency**: Time required to provision ephemeral compute.
* **Developer Experience**: Local testing, CI integration, and Asset Bundle deployments.
* **Cost Governance**: Cluster policies, auto-termination, and spot instance utilization.

## Decision
We select **Databricks with Photon Acceleration and Serverless Compute**:
* **ETL & Ingestion**: Ephemeral Single-Node or Autoscaling Job Clusters running Photon Runtime.
* **CI/CD & Integration Testing**: Serverless Compute for near-instant cold-start execution (< 15 seconds).
* **Ad-hoc & BI Serving**: Databricks Serverless SQL Warehouses.
