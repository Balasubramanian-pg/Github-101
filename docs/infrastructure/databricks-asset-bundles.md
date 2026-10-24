# Databricks Asset Bundles (DABs) Architecture

Databricks Asset Bundles (DABs) provide standard software engineering practices for Databricks projects, enabling declarative configuration, testing, and continuous deployment of data pipelines.

## 1. Why Databricks Asset Bundles?
* Replaces custom shell deployment scripts and legacy `dbx` tooling.
* Native integration with Databricks CLI (`databricks bundle`).
* Declarative YAML resources for Workflows, Delta Live Tables (DLT), and Notebooks.
* Deterministic multi-environment target resolution (`dev`, `staging`, `prod`).

## 2. Bundle Structure & Resource Declaration

```yaml
# databricks.yml
bundle:
  name: order-lakehouse-pipeline

include:
  - resources/*.yml

targets:
  dev:
    mode: development
    default: true
    workspace:
      host: https://adb-dev.azuredatabricks.net
    variables:
      catalog: dev_lakehouse

  prod:
    mode: production
    workspace:
      host: https://adb-prod.azuredatabricks.net
    variables:
      catalog: prod_lakehouse
```

```yaml
# resources/orders_job.yml
resources:
  jobs:
    orders_etl_job:
      name: "[${bundle.target}] Orders Medallion Ingest"
      job_clusters:
        - job_cluster_key: photon_job_cluster
          new_cluster:
            spark_version: 14.3.x-photon-scala2.12
            node_type_id: i3.xlarge
            num_workers: 2
      tasks:
        - task_key: bronze_ingest
          job_cluster_key: photon_job_cluster
          python_wheel_task:
            package_name: lakehouse_orders
            entry_point: ingest_bronze
```

## 3. Bundle Deployment Lifecycle Diagram

```mermaid
flowchart TD
    A["Developer / CI Runner"] --> B["databricks bundle validate"]
    B --> C{"YAML Syntax & Variables Valid?"}
    C -- No --> D["Fail Build with Diagnostic Errors"]
    C -- Yes --> E["databricks bundle build (Package Wheels)"]
    E --> F["databricks bundle deploy -t [target]"]
    F --> G["Upload Artifacts to Workspace Files"]
    G --> H["Sync Jobs & DLT Pipelines to Databricks Workspace"]
    H --> I["databricks bundle run (Smoke Test Run)"]
```
