# Linting, Formatting & Code Style Architecture

Consistent style and automated static analysis preserve repository cleanliness, catch logical bugs early, and eliminate trivial formatting debates during code reviews.

## 1. Guiding Philosophy
* **Zero Debates in Code Reviews**: Formatting is completely automated. PR comments discussing whitespace, import order, or quotes are strictly prohibited.
* **Fast Feedback**: Local pre-commit linting must complete in under 5 seconds.
* **Unified Enforcement**: Identical linting rules execute locally via git hooks and in CI pipelines via GitHub Actions.

## 2. Selected Linting & Formatting Tooling Stack

| Tool | Focus | Target Dialect | Performance Characteristics |
| :--- | :--- | :--- | :--- |
| **Ruff** | Python Linting & Import Sorting | Python 3.11+ | Written in Rust; **10x-50x faster than Flake8/isort** |
| **Black** | Python Formatting | Python 3.11+ (100 char limit) | Deterministic AST formatting |
| **Mypy** | Static Type Checking | Python Type Hints | Validates PySpark DataFrame annotations |
| **SQLFluff** | SQL Linting & Formatting | Databricks / Spark SQL Dialect | Enforces uppercase keywords & 4-space indentation |
