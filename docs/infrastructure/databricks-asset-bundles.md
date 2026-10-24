# Databricks Asset Bundles (DABs) Architecture

Databricks Asset Bundles (DABs) provide standard software engineering practices for Databricks projects, enabling declarative configuration, testing, and continuous deployment of data pipelines.

## 1. Why Databricks Asset Bundles?
* Replaces custom shell deployment scripts and legacy `dbx` tooling.
* Native integration with Databricks CLI (`databricks bundle`).
* Declarative YAML resources for Workflows, Delta Live Tables (DLT), and Notebooks.
* Deterministic multi-environment target resolution (`dev`, `staging`, `prod`).
