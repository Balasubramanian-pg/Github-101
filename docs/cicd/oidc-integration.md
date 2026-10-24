# Cloud OIDC Integration Guide

OpenID Connect (OIDC) allows GitHub Actions workflows to authenticate directly with cloud providers (AWS, Azure, GCP) using short-lived cryptographically signed tokens, completely eliminating long-lived static secrets.

## 1. Why OIDC is Mandatory
* **Zero Secret Exposure**: No AWS Access Keys or Azure Client Secrets stored in GitHub repository settings.
* **Automatic Expiration**: Tokens expire automatically after 60 minutes.
* **Granular Least Privilege**: Cloud roles restrict access based on specific GitHub claims (e.g. branch name, environment, tag).

## 2. Token Exchange Protocol

The OIDC exchange follows a three-step cryptographic validation:

```
1. GitHub Runner requests OIDC Token from GitHub Token Service.
2. GitHub issues a signed JSON Web Token (JWT) containing repository metadata.
3. Runner presents JWT to Cloud STS (AssumeRoleWithWebIdentity).
4. Cloud STS validates GitHub's public certificate and issues temporary credentials.
```

### Claims in the GitHub OIDC JWT:
```json
{
  "iss": "https://token.actions.githubusercontent.com",
  "sub": "repo:Balasubramanian-pg/Github-101:ref:refs/heads/main",
  "aud": "https://github.com/Balasubramanian-pg",
  "repository": "Balasubramanian-pg/Github-101",
  "repository_owner": "Balasubramanian-pg",
  "ref": "refs/heads/main",
  "environment": "prod"
}
```
