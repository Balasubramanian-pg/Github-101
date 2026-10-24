# Runbook: Incident Response & Escalation Protocol

This runbook defines the operational protocol for triaging, communicating, mitigating, and conducting post-incident reviews for production data platform failures.

## 1. Incident Severity Definitions

| Severity | Impact Criteria | Response SLA | Escalation Target |
| :--- | :--- | :--- | :--- |
| **P0 - Blocker** | Production pipelines halted; Gold SLA breached; executive dashboards empty | **< 15 minutes** | VP Engineering, Lead Data Engineer, Platform SRE |
| **P1 - Critical** | Data corruption in partition; delayed downstream reporting; degraded latency | **< 30 minutes** | Lead Data Engineer, Domain Product Owner |
| **P2 - Major** | Pipeline retried successfully; non-critical batch delayed | **< 2 hours** | On-Call Data Engineer |
| **P3 - Minor** | Cosmetic reporting issue; internal log formatting bug | **< 24 hours** | Next sprint triage |
