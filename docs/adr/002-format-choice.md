# ADR 002: Storage Table Format Selection

## Status
Accepted

## Context
A modern lakehouse requires an open, performant, and standardized table format to underpin the storage layer across cloud object stores (S3 / ADLS Gen2). We evaluated Delta Lake, Apache Iceberg, and Apache Hudi.
