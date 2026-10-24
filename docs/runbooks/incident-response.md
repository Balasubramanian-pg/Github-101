# Runbook: Incident Response & Escalation Protocol

This runbook defines the operational protocol for triaging, communicating, mitigating, and conducting post-incident reviews for production data platform failures.

## 1. Incident Severity Definitions

| Severity | Impact Criteria | Response SLA | Escalation Target |
| :--- | :--- | :--- | :--- |
| **P0 - Blocker** | Production pipelines halted; Gold SLA breached; executive dashboards empty | **< 15 minutes** | VP Engineering, Lead Data Engineer, Platform SRE |
| **P1 - Critical** | Data corruption in partition; delayed downstream reporting; degraded latency | **< 30 minutes** | Lead Data Engineer, Domain Product Owner |
| **P2 - Major** | Pipeline retried successfully; non-critical batch delayed | **< 2 hours** | On-Call Data Engineer |
| **P3 - Minor** | Cosmetic reporting issue; internal log formatting bug | **< 24 hours** | Next sprint triage |

## 2. Incident Command Roles

During a P0/P1 incident, three distinct roles are appointed:
* **Incident Commander (IC)**: Owns the operational response, assigns investigation streams, and makes go/no-go rollback decisions.
* **Technical Lead (TL)**: Drives root-cause debugging, code fixes, and technical mitigation.
* **Communications Lead (CL)**: Posts status updates to stakeholders every 30 minutes and shields engineers from distraction.
