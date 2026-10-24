# Integration Testing Architecture

Integration testing validates interactions between the PySpark compute engine, Delta Lake transactional storage, Unity Catalog metadata, and cloud object stores.

## 1. Scope of Integration Testing
While unit tests validate transformation logic in memory, integration tests verify:
* Atomic commits and concurrent writes to Delta Lake tables.
* Auto Loader (`cloudFiles`) ingestion behavior against realistic cloud storage file streams.
* Schema evolution and constraint enforcement in Unity Catalog.
* End-to-end Medallion data flow from Bronze raw landing to Gold dimensional views.
