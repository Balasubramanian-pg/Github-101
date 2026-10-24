## Pull Request Summary

### Description
<!-- Provide a concise summary of the changes and the architectural motivation -->

### Related Issue(s)
* Closes #<!-- issue number -->
* Relates to ADR: `docs/adr/<!-- number -->`

### Type of Change
- [ ] `feat`: New data transformation / pipeline capability
- [ ] `fix`: Bug fix in existing pipeline logic
- [ ] `schema`: Delta Lake schema evolution or migration
- [ ] `infra`: Cloud resource / Databricks Asset Bundle change
- [ ] `perf`: Pipeline performance optimization
- [ ] `docs`: Documentation update

---

## Schema Impact Analysis

*Does this PR alter Delta Lake schemas, table contracts, or SQL views?*
- [ ] **No schema changes**
- [ ] **Yes, backward-compatible** (e.g. added nullable columns)
- [ ] **Yes, BREAKING CHANGE** (requires coordination & approval)

| Target Table Name | Layer (Bronze/Silver/Gold) | Column Name | Change Type (Add/Modify/Drop) | Data Type | Nullable? | Downstream Impact |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `silver.orders` | Silver | `customer_tier` | Add | `STRING` | Yes | None (Additive) |

---

## Data Quality & Testing Evidence

Please confirm that required validation suites have been executed:
- [ ] Local unit tests passed (`pytest tests/unit/`)
- [ ] Great Expectations / Soda Core data contract suite executed
- [ ] Tested on synthetic mock dataset (no production PII used)
- [ ] PySpark query execution plan (`explain()`) reviewed for broadcast joins and partition skew

### Test Output Snippet
```text
<!-- Paste terminal output from pytest or contract suite here -->
```

---

## Deployment & Rollback Strategy

* **Deployment Target**:
  - [ ] Development (`dev`)
  - [ ] Staging (`staging`)
  - [ ] Production (`prod`)

* **Execution Mechanism**:
  - [ ] Automated DABs bundle deployment (`databricks bundle deploy`)
  - [ ] Manual backfill workflow execution required

* **Rollback Plan**:
  <!-- State exact steps to restore previous state if deployment fails -->
  * Revert commit via git.
  * Delta Lake time travel restore command: `RESTORE TABLE <table_name> TO VERSION AS OF <version>`
