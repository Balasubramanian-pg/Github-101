# Reusable Workflows Architecture

Reusable workflows allow engineering teams to define standard CI/CD logic in a centralized location, preventing duplicate YAML files across repositories and enforcing uniform quality gates.

## 1. Motivation
In multi-repository data organizations, duplicating GitHub Actions workflows leads to:
* Configuration drift between domain data pipelines.
* Inconsistent linting and testing standards.
* Security vulnerabilities when secrets or deployment scripts are updated in one repo but missed in others.

## 2. Reusable Workflow Interface Specification

Reusable workflows utilize GitHub Actions `workflow_call` trigger:

```yaml
# .github/workflows/reusable-pyspark-test.yml
name: Reusable PySpark Test Suite

on:
  workflow_call:
    inputs:
      python-version:
        required: false
        type: string
        default: "3.11"
      coverage-threshold:
        required: false
        type: number
        default: 85
    secrets:
      DATABRICKS_HOST:
        required: false
      DATABRICKS_TOKEN:
        required: false

jobs:
  run-tests:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - name: Set up Python
        uses: actions/setup-python@v5
        with:
          python-version: ${{ inputs.python-version }}
      - name: Run PyTest
        run: |
          pip install pytest pytest-cov pyspark
          pytest --cov=src --cov-fail-under=${{ inputs.coverage-threshold }} tests/
```
