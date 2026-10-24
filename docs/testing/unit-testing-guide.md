# Unit Testing Guide for PySpark Pipelines

Unit testing distributed data pipelines requires isolating business logic from distributed cluster runtimes and cloud storage dependencies.

## 1. Core Testing Philosophy
* **Pure Transformation Functions**: Extract transformation logic into deterministic functions that take a `DataFrame` as input and return a `DataFrame`.
* **Zero Cloud Dependencies**: Unit tests must run locally and in GitHub Actions runners without requiring active Databricks clusters or cloud credentials.
* **Fast Execution**: Entire unit test suite must execute in under 60 seconds.
