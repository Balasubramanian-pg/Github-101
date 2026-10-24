# Schema Evolution & Backward Compatibility

Managing schema changes safely across large-scale distributed datasets is critical. Unplanned schema modifications can break downstream ETL pipelines, reporting dashboards, and machine learning models.

## 1. Guiding Principles
* **Schema Enforcement by Default**: Reject unexpected columns and mismatched data types at ingestion boundaries.
* **Controlled Evolution**: Enable `mergeSchema` exclusively for planned, backward-compatible additions.
* **Zero Breaking Changes Without Notice**: Modifications that break consumers require a 30-day deprecation cycle.
