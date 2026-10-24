# External API Authentication & Rate Limiting

Data pipelines frequently extract data from or synchronize results with external third-party REST APIs (e.g. Stripe, Salesforce, Workday, ServiceNow). This document specifies authentication protocols, secret management, and rate-limiting resilience.

## 1. Authentication Standards
* **Zero Hardcoded Secrets**: All API tokens, client secrets, and private keys reside in Azure Key Vault / AWS Secrets Manager.
* **OAuth 2.0 Machine-to-Machine (M2M)**: Preferred authentication mechanism using Client Credentials Grant.
* **Token Caching**: Bearer tokens are cached locally in memory until expiration to minimize authentication overhead.

## 2. Authentication Protocol Landscape

| Provider Type | Standard Mechanism | Credential Storage | Refresh Strategy |
| :--- | :--- | :--- | :--- |
| **Enterprise SaaS (Salesforce, Workday)** | OAuth 2.0 Client Credentials | Cloud Key Vault (Client ID + Secret) | Auto-refresh 5 min before JWT expiration |
| **Financial / Payment APIs (Stripe)** | Restricted API Keys | Cloud Key Vault / Databricks Secret Scope | Static with quarterly automated rotation |
| **High-Security Banking Partners** | Mutual TLS (mTLS) + Client Certificate | Azure Key Vault Certificate Store | Annual certificate renewal |
