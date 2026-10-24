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

## 3. Pre-Commit Configuration (`.pre-commit-config.yaml`)

```yaml
repos:
  - repo: https://github.com/astral-sh/ruff-pre-commit
    rev: v0.3.4
    hooks:
      - id: ruff
        args: [--fix]
      - id: ruff-format

  - repo: https://github.com/psf/black
    rev: 24.3.0
    hooks:
      - id: black
        args: [--line-length=100]

  - repo: https://github.com/sqlfluff/sqlfluff
    rev: 3.0.1
    hooks:
      - id: sqlfluff-lint
        args: [--dialect, databricks]
      - id: sqlfluff-fix
        args: [--dialect, databricks]

  - repo: https://github.com/pre-commit/pre-commit-hooks
    rev: v4.5.0
    hooks:
      - id: check-added-large-files
        args: ['--maxkb=1000']
      - id: check-yaml
      - id: end-of-file-fixer
      - id: trailing-whitespace
```
