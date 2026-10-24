# CI/CD Caching Strategy

Optimizing pipeline build and test durations is vital for maintaining high engineering velocity. This document outlines our caching architecture for Python dependencies, PySpark wheels, and pre-commit environments.

## 1. Caching Objectives
* Reduce PR validation feedback loop to < 3 minutes.
* Eliminate redundant compilation of C-extension wheels (e.g. `numpy`, `pyarrow`, `cryptography`).
* Respect GitHub Actions 10GB per repository cache quota through proactive eviction.

## 2. Multi-Layer Caching Architecture

We cache at three distinct layers:

1. **Pre-commit Cache**: Caches linters and formatters (`ruff`, `black`, `sqlfluff`).
2. **Pip / UV Dependency Cache**: Caches downloaded Python wheels matching package hashes.
3. **Databricks CLI Cache**: Caches the standalone Databricks CLI executable.

```yaml
- name: Cache Python Virtualenv
  uses: actions/cache@v4
  with:
    path: ~/.cache/pip
    key: ${{ runner.os }}-pip-${{ hashFiles('**/pyproject.toml', '**/requirements*.txt') }}
    restore-keys: |
      ${{ runner.os }}-pip-
```
