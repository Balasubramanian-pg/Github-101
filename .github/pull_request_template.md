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
