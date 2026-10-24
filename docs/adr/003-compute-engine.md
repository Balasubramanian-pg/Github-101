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
