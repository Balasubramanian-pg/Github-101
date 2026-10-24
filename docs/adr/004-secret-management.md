# ADR 004: Secrets Management and Keyless Authentication

## Status
Accepted

## Context
Data engineering pipelines must securely interact with cloud providers, storage buckets, external REST APIs, and database sinks without exposing long-lived credentials in code repositories or environment variables.
