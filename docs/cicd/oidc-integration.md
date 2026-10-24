# Cloud OIDC Integration Guide

OpenID Connect (OIDC) allows GitHub Actions workflows to authenticate directly with cloud providers (AWS, Azure, GCP) using short-lived cryptographically signed tokens, completely eliminating long-lived static secrets.

## 1. Why OIDC is Mandatory
* **Zero Secret Exposure**: No AWS Access Keys or Azure Client Secrets stored in GitHub repository settings.
* **Automatic Expiration**: Tokens expire automatically after 60 minutes.
* **Granular Least Privilege**: Cloud roles restrict access based on specific GitHub claims (e.g. branch name, environment, tag).
