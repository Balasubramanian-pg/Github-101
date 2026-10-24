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

## 3. OAuth2 Token Exchange & Caching Flow Diagram

```mermaid
sequenceDiagram
    autonumber
    participant DBR as Databricks Spark Worker
    participant CACHE as In-Memory Token Cache
    participant IDP as External Identity Provider (Okta / Entra)
    participant API as External SaaS REST API

    DBR->>CACHE: Request Bearer Token for 'salesforce-ingest'
    alt Valid Token in Cache (Expires in > 5 min)
        CACHE-->>DBR: Return cached JWT
    else Cache Miss or Expired
        CACHE->>IDP: POST /oauth/token (grant_type=client_credentials)
        IDP-->>CACHE: Return Access Token (expires_in=3600)
        CACHE-->>DBR: Store in memory and return Token
    end
    DBR->>API: GET /v1/records (Authorization: Bearer <token>)
    alt API Responds HTTP 200 OK
        API-->>DBR: Return JSON batch
    else API Responds HTTP 429 Too Many Requests
        API-->>DBR: Return Retry-After: 30
        DBR->>DBR: Exponential Backoff with Jitter
        DBR->>API: Retry request after backoff pause
    end
```
