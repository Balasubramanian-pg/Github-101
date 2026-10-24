# Linting, Formatting & Code Style Architecture

Consistent style and automated static analysis preserve repository cleanliness, catch logical bugs early, and eliminate trivial formatting debates during code reviews.

## 1. Guiding Philosophy
* **Zero Debates in Code Reviews**: Formatting is completely automated. PR comments discussing whitespace, import order, or quotes are strictly prohibited.
* **Fast Feedback**: Local pre-commit linting must complete in under 5 seconds.
* **Unified Enforcement**: Identical linting rules execute locally via git hooks and in CI pipelines via GitHub Actions.
