# ADR 002: Storage Table Format Selection

## Status
Accepted

## Context
A modern lakehouse requires an open, performant, and standardized table format to underpin the storage layer across cloud object stores (S3 / ADLS Gen2). We evaluated Delta Lake, Apache Iceberg, and Apache Hudi.

## Evaluated Table Formats

1. **Delta Lake (Linux Foundation)**
   * High performance on Spark / Photon compute engines.
   * Native Unity Catalog integration, liquid clustering, and UniForm (Universal Format) support.
2. **Apache Iceberg (Apache Software Foundation)**
   * Strong cross-engine catalog support (Snowflake, Trino, BigQuery).
   * Vendor-neutral specification with rapid ecosystem adoption.
3. **Apache Hudi (Apache Software Foundation)**
   * Optimized for near-real-time streaming upserts (Copy-on-Write and Merge-on-Read).
   * Complex configuration tuning and higher operational friction.
