# External API Authentication & Rate Limiting

Data pipelines frequently extract data from or synchronize results with external third-party REST APIs (e.g. Stripe, Salesforce, Workday, ServiceNow). This document specifies authentication protocols, secret management, and rate-limiting resilience.

## 1. Authentication Standards
* **Zero Hardcoded Secrets**: All API tokens, client secrets, and private keys reside in Azure Key Vault / AWS Secrets Manager.
* **OAuth 2.0 Machine-to-Machine (M2M)**: Preferred authentication mechanism using Client Credentials Grant.
* **Token Caching**: Bearer tokens are cached locally in memory until expiration to minimize authentication overhead.
