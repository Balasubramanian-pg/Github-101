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

## Technical Comparison

| Feature | Delta Lake | Apache Iceberg | Apache Hudi |
| :--- | :--- | :--- | :--- |
| **Spark/Photon Optimization** | **Excellent (Native)** | Good | Moderate |
| **ACID Guarantees** | Serializable / WriteSerializable | Snapshot Isolation | Snapshot Isolation |
| **Liquid Clustering** | **Yes (Automatic)** | Partition Evolution | Clustering Service |
| **Cross-Format Read (UniForm)** | **Yes (Generates Iceberg metadata)**| No | No |
| **Governance Integration** | **Native Unity Catalog** | External Catalogs | External Catalogs |

## Decision
We select **Delta Lake with Universal Format (UniForm)** enabled as our primary storage format.

By configuring Delta UniForm, the storage layer writes Delta transaction logs while automatically generating Apache Iceberg metadata in the background. This delivers top-tier performance on Databricks Photon while preserving cross-engine read capabilities for Trino and external query engines without duplicating Parquet data files.

## Consequences

### Positive
* 2x-4x faster write and upsert throughput on Databricks clusters using Photon native vectorization.
* Seamless time travel, schema evolution (`mergeSchema`), and zero-copy cloning.
* Future-proof: UniForm eliminates vendor lock-in by providing Iceberg compatibility.

### Negative & Mitigations
* Writes incur slight overhead when generating dual metadata catalogs.
  * *Mitigation*: Enable UniForm selectively on tables requiring external cross-engine consumption.
