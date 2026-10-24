# Runbook: Standard Production Deployment

This runbook outlines the step-by-step operational procedure for deploying code changes, pipeline configurations, and Databricks Asset Bundles to the production lakehouse environment.

## 1. Deployment Windows & Pre-Conditions
* **Approved Release Window**: Tuesday through Thursday, 10:00 - 15:00 UTC. Deployments outside this window require explicit approval from the Engineering Director.
* **Freeze Windows**: Zero production deployments during enterprise quarter-end financial processing or retail peak sale events.
* **Pre-requisite Approvals**: At least two pull request approvals, including at least one designated Lead Data Engineer.
