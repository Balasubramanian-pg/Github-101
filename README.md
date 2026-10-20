# Github-101
How Do You Really Use Github??
You have mastered the fundamentals of Git and why we use Git. I am confident that you would also know where to Git, but have you ever thought about the different MOCs (Map of Contents) of Github that you should be aware of? Be it Github as an enterprise account or In Azure Devops or in other formats? What are certain POCs (Proof of concepts) you should definitely know so that life becomes easier?

We can start here.

| |
| :---: |
| <img width="814" height="693" alt="Architecture diagram" src="https://github.com/user-attachments/assets/510923b0-927b-4a9f-8627-ffbb9fdbbba4" /> |
| <small><sup>1</sup> This is a reference architecture, not a mandatory sequence. For example, a package may be published before production approval, and a release may be created before deployment or after deployment, depending on the team's release model.</small> |

Git stores a history of changes. GitHub and Azure Repos provide remote hosting and collaboration on top of that history.
<img width="828" height="512" alt="image" src="https://github.com/user-attachments/assets/6584abf8-fd6c-4762-b0f1-b236fe19a2ac" />


You need to understand how engineering teams build, review, test, release, deploy, secure, and maintain software and data systems. GitHub is one part of that system, not the whole thing.

Your POC should prove that you can design an engineering workflow, automate it, control access, handle failures, and explain why the architecture works. That is the difference between knowing a tool and being able to lead a team using it.

# 1. The ecosystem you need to understand

[Git Flow Made Easy With This Complete Walkthrough | Stephen Vinouze](https://images.openai.com/static-rsc-4/k_0esLKbqFGSiP5J2XoCyQz9tyz7kcWA0lCy0Uf9jMSD_bjxnAzYAHWvjO5x0CkUeCoZDor1PAHpLJ2jF6vzvphhvQgRlSKPJ1pV-xHJR0qqLBsOd9Fs_mgTJ9HnbBKBKpr-IHVSx8AHbxO0ODKrhKXhkjS6B7yZcE7rSJh5UIA?purpose=inline)

Git: version control

The foundation. Commits, branches, tags, diffs, merges, rebases, conflicts, history, and recovery.

Git works independently of GitHub, Azure DevOps, or any other hosting platform.

[How to Use Git and GitHub in a Team like a Pro – Featuring Harry and Hermione 🧙](https://images.openai.com/static-rsc-4/GTIwuorCLk7HcYU99kcveGCFz0Rb4kac2BNFins2TGb9p9MRl6wjOw9d-3Dfm8S0clV2b01hOh7rCcIy3gboMc_-FRqRuoCaEoOztyg3NKmG0QCyACME4Qd_uAgVUczFj4CL9trs23g7ii6k4a53N8ZcveSMPL7ncK9x9Yjoqe4?purpose=inline)

GitHub or Azure Repos: collaboration

Repositories, pull requests, reviews, branch protection, issues, permissions, CODEOWNERS, and auditability.

These platforms host Git repositories and provide team workflows around them.

[Supercharging your CICD game with Self-hosted Runners from GitHub Actions | by Achintha Reemal | Sysco LABS Sri Lanka | Medium](https://images.openai.com/static-rsc-4/nZ2QaqGJdp0pLQiKmLy9aVheQrPQt9UFgNf7__Ov7qi4rI4AWdbTKAsFxWGm2aTB5_k6JbP0mfSIwyYCvT5VUC1YIObgNieBK3mX7xCJwCfmb2gW7DHhi4UVHbX7W5Frts4-xsbqn6RuIsps2yYdAZbIzro_KwBCYks-Xb-cqBI?purpose=inline)

CI/CD: automated engineering

GitHub Actions, Azure Pipelines, runners, build jobs, tests, artifacts, deployment approvals, and rollback.

CI validates changes. CD delivers them to the right environment.

[Docker Image Build and Promotion Pipeline: A Production Guide](https://images.openai.com/static-rsc-4/t0m1J_QZgoblC8zsU3z3nnIlTnGml2QNc6LMWu93lVgrHMHKAierIVOM34w6xChrpzo_mHsuNQdIppagbEt9u0jMwdXvx6_BA6eNpNy6UZck2bfxGNcL46Q3foTUsgFr30zpXlIQz1vsKA8f5Vs_z_wby5iNwhvVoZsixTIkCS0?purpose=inline)

Artifacts and distribution

Packages, container registries, release assets, versioned libraries, dependency management, and provenance.

Source code is not the same thing as a built or deployable artifact.

[Worldpay Developer Hub](https://images.openai.com/static-rsc-4/sAJMeg5LtyNsrYComONQgz7DKj-flV2DdHR-dHbFmi-jq3wwQyC-9NEKjHYAdOLd6-MLH4z1egVLYiNarol4nitwE-pS4mENpDqPoAodicciEx4O2y_G_NNS9m7q8HPZ_z_ee0Icdug0Lrm6LIxw5ipgAaXq2yKtwUvFVD15qM0?purpose=inline)

Integration and governance

Webhooks, REST APIs, GitHub Apps, secrets, OIDC, identity, policies, observability, and incident response.

These let your engineering system interact with the rest of the organization.

The key distinction: Git is the version-control engine. GitHub is a collaboration and automation platform built around Git. Azure DevOps offers a comparable ecosystem, but its repositories, pipelines, artifacts, and permissions have their own implementation and terminology.

# 2. The complete concept map

This is the landscape I would expect a future Lead Data Engineer to understand. You do not need to master every product equally. You need to understand how the pieces fit together and build at least one working example of each important capability.

## Source control

Git · Repository · Branch · Commit · Tag

Collaboration and governance

Pull requests · Reviews · CODEOWNERS · Branch rules · Issues

Continuous integration

Actions / Pipelines · Linters · Unit tests · SQL tests · Security scans

Build and publish

Versioned artifacts · Packages · Container images · Releases

DEV

Test changes

UAT

Validate and approve

PROD

Deploy safely

Cross-cutting controls

Identity and access · Secrets · Audit logs · Webhooks · APIs · Monitoring · Rollback · Cost controls

This is a reference architecture, not a mandatory sequence. For example, a package may be published before production approval, and a release may be created before deployment or after deployment, depending on the team's release model.

# 3. Git fundamentals: the part you cannot skip

Git stores a history of changes. GitHub and Azure Repos provide remote hosting and collaboration on top of that history.

Repository

A project containing files and Git history. A data engineering repository might contain PySpark jobs, SQL transformations, tests, deployment configuration, and documentation.

Commit

A snapshot of tracked project content plus metadata and links to parent commits. Commits give you traceability and a way to inspect or recover previous versions.

Branch

A movable reference to a commit, used to develop changes independently. A feature branch lets you work without immediately changing the main branch.

Merge and rebase

Merge integrates histories, usually preserving their branch structure. Rebase replays commits onto a different base, creating new commit identities. Both are useful, but they solve different history-management problems.

Tag

A named reference to a specific commit, often used to identify a release such as `v1.2.0`. A Git tag is not the same thing as a GitHub Release.

## The workflow you must be able to execute
```mermaid

flowchart TD
    A["main branch"] --> B["Create feature branch"]
    B --> C["Edit SQL / Python"]
    C --> D["Commit changes"]
    D --> E["Push branch to remote"]
    E --> F["Open pull request"]
    F --> G["Automated checks and review"]
    G --> H{"Approved and checks pass?"}
    H -- No --> C
    H -- Yes --> I["Merge into main"]
    I --> J["Build and test"]
    J --> K["Tag version and publish release"]
    K --> L["Deploy to target environment"]
```

A practical command sequence:

```
git clone <repository-url>
cd <repository-folder>

git switch -c feature/add-data-quality-checks

# Edit your files
git status
git diff

git add .
git commit -m "feat: add data quality checks"
git push -u origin feature/add-data-quality-checks
```

Then open a pull request on your hosting platform, get it reviewed, and merge it using the team's approved strategy.

Learn these commands properly:

| Command                     | Why you need it                                                  |
| --------------------------- | ---------------------------------------------------------------- |
| `git status`                | Understand your working tree                                     |
| `git diff`                  | Review changes before committing                                 |
| `git log --oneline --graph` | Inspect commit history                                           |
| `git fetch`                 | Retrieve remote history without integrating it                   |
| `git pull`                  | Fetch and integrate remote changes                               |
| `git switch -c`             | Create and switch to a branch                                    |
| `git merge`                 | Integrate another branch                                         |
| `git rebase`                | Replay commits on a new base                                     |
| `git revert`                | Undo a change through a new commit                               |
| `git reset`                 | Move a reference and potentially alter staged or working changes |
| `git cherry-pick`           | Apply a selected commit elsewhere                                |
| `git stash`                 | Temporarily save uncommitted changes                             |

The leadership-level requirement is not memorizing commands. It is knowing what state the repository is in, which operation changes that state, and how to recover without losing someone else's work.

# 4. GitHub concepts you need to know in depth

These are the concepts I would turn into individual POCs, rather than studying as isolated definitions.

<img width="712" height="886" alt="image" src="https://github.com/user-attachments/assets/7a72a7db-1181-4028-b800-04249b65df58" />


## Other concepts you should cover

| Concept                | What a lead should understand                                                     |
| ---------------------- | --------------------------------------------------------------------------------- |
| Issues and Projects    | Work tracking, priorities, dependencies, milestones                               |
| Labels and milestones  | Categorizing work and grouping it into delivery targets                           |
| CODEOWNERS             | Automatically requesting review from the responsible team                         |
| Environments           | Separate deployment targets, protection rules, and environment-scoped secrets     |
| Secrets and variables  | Credentials versus non-sensitive configuration                                    |
| GitHub Apps and tokens | Application identity, permissions, token lifetimes, least privilege               |
| Dependabot             | Dependency updates and vulnerability alerts                                       |
| Code scanning          | Static analysis for security defects                                              |
| Audit logs             | Who performed an action and when, subject to platform retention and permissions   |
| Reusable workflows     | Standardized CI/CD across repositories                                            |
| Self-hosted runners    | Running jobs on infrastructure you manage, including its security implications    |
| Git LFS                | Managing large files that are unsuitable for ordinary Git history                 |
| Submodules             | Referencing another repository from a repository                                  |
| Monorepos              | Managing many components in one repository with path-aware testing and deployment |

The official [GitHub Actions workflow documentation](https://docs.github.com/en/actions/concepts/workflows-and-actions/workflows?utm_source=chatgpt.com) explains the workflow, job, runner, and step model.&#x20;

[image](https://www.google.com/s2/favicons?domain=https://docs.github.com\&sz=32)

GitHub Docs



# 5. Releases, packages, artifacts, and deployments are not the same thing

This distinction trips up many engineers because the terms are often used loosely.

<img width="725" height="447" alt="image" src="https://github.com/user-attachments/assets/adc8358a-8e15-4beb-9483-6d2913470186" />

One version may have multiple artifacts. A release may contain multiple packages or deployment assets. A deployment should identify the exact artifact version it uses, not merely whatever code happens to be on `main`.

For data engineering, I would extend this with data migrations and rollback. Reverting a Python commit does not automatically reverse a SQL schema change or undo data already written to a production Delta table.

## Semantic versioning

Understand the pattern `MAJOR.MINOR.PATCH`.

| Version change | Meaning                     | Example           |
| -------------- | --------------------------- | ----------------- |
| Major          | Incompatible change         | `1.4.2` → `2.0.0` |
| Minor          | Backward-compatible feature | `1.4.2` → `1.5.0` |
| Patch          | Backward-compatible fix     | `1.4.2` → `1.4.3` |

This is a convention, not an automatic guarantee. Your team must define what counts as a breaking change for a data pipeline, SQL interface, Python library, or published dataset contract.

# 6. GitHub Actions: your first serious automation POC

The fundamental hierarchy is:

<img width="734" height="390" alt="image" src="https://github.com/user-attachments/assets/e83a8d76-e024-4c14-bd6c-c387ac204aa9" />


A starter workflow for a Python data engineering repository could look like this:

```

name: Data Engineering CI

on:
  pull_request:
    branches: [main]
  push:
    branches: [main]

permissions:
  contents: read

jobs:
  validate:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout source
        uses: actions/checkout@v4

      - name: Set up Python
        uses: actions/setup-python@v5
        with:
          python-version: "3.12"

      - name: Install dependencies
        run: |
          python -m pip install --upgrade pip
          pip install ruff pytest
          if [ -f requirements.txt ]; then
            pip install -r requirements.txt
          fi

      - name: Lint Python
        run: ruff check .

      - name: Run unit tests
        run: pytest -q

```

This is a learning example. For production, pin third-party actions to reviewed immutable commit SHAs, manage dependency versions, configure the correct Python version, and review the security of all scripts and dependencies.

To make this a proper POC:

- Add a deliberately failing test and confirm the workflow fails.
- Fix the test and confirm the workflow passes.
- Configure the workflow as a required PR check.
- Attempt a merge while the check is failing.
- Confirm that repository rules prevent the merge.
- Save the test output as an artifact.
- Add a separate deployment workflow with restricted permissions and explicit environment approval.

A crucial detail: a workflow running successfully does not, by itself, protect your branch. The repository's branch rules must require the appropriate check.

## Advanced Actions topics

Learn these after the first workflow works:

- Triggers and filters: branch filters, path filters, tags, schedules, and manual runs.
- Dependencies: `needs`, job conditions, matrices, and parallel jobs.
- Artifacts and caching: passing build outputs between jobs versus caching dependencies to speed up execution.
- Reusable workflows: shared CI/CD standards across many repositories.
- Environments: deployment protection, approvals, and environment-scoped configuration.
- OIDC: short-lived identity-based access to cloud services without storing long-lived cloud credentials.
- Concurrency: preventing competing deployments from interfering with one another.
- Security: untrusted pull-request code, token permissions, third-party action pinning, and secret exposure.
- Self-hosted runners: network access to internal systems, runner isolation, patching, and cleanup.

# 7. Webhooks, APIs, and event-driven automation

Since you mentioned webhooks specifically, build a POC that proves you understand the entire event lifecycle, not just how to configure a URL.

```mermaid

sequenceDiagram
    participant G as GitHub
    participant W as Webhook Receiver
    participant V as Validation Service
    participant D as Audit Store
    participant N as Notification Service

    G->>W: Pull request event + payload
    W->>W: Verify signature
    W->>W: Check delivery ID
    W-->>G: Return HTTP 2xx
    W->>V: Queue event
    V->>V: Validate repository and PR metadata
    V->>D: Record event and outcome
    V->>N: Notify on failure or success
```

The production-oriented details matter:

| Mechanism                  | Purpose                                                         |
| -------------------------- | --------------------------------------------------------------- |
| Webhook event              | Notifies your service that something happened                   |
| HTTP payload               | Carries event data                                              |
| Signature verification     | Checks authenticity using the configured webhook secret         |
| Delivery ID                | Helps identify duplicate deliveries                             |
| Idempotency                | Prevents processing the same logical event twice                |
| Queue or durable store     | Protects against lost work when processing is delayed           |
| Retry and failure handling | Deals with timeouts, transient failures, and downstream outages |
| REST API                   | Fetches additional details or performs authorized operations    |
| Fine-grained permissions   | Limits what the integration can read or modify                  |

GitHub webhooks are not guaranteed to be delivered exactly once, and your receiver should not assume every event arrives in order. A robust design acknowledges the HTTP request promptly, persists the event, and processes it asynchronously when appropriate.

Build the first version with a small Python API service, such as FastAPI, and a local webhook-testing tool. Then add duplicate-event handling, persistent storage, structured logs, and retry behavior.

Azure DevOps has a similar event-integration model called Service Hooks. Microsoft documents how subscriptions connect project events to external services and actions.&#x20;

[image](https://www.google.com/s2/favicons?domain=https://learn.microsoft.com\&sz=32)

Microsoft Learn



# 8. GitHub versus Azure DevOps versus GitLab

You should understand all three ecosystems, but do not attempt to master all three simultaneously.

[GitHub official Logo PNG Vector (EPS) Free Download](https://images.openai.com/static-rsc-4/j6DnFoGR1MfnOBr9lIK962EQdYyxmY8SyJ9-28a69vOkM2BzMHwDekYl2JG6WLr8JTUKKPjN98M-z-HFImt0j5nyukd1e120mDGQLqeLKnLZ8JVrrifApGVGwSFY2cM3RpPDf7Km3KmgvbycYPvr2t5PuRLGFKmpzE2a9ikOtUk?purpose=inline)

GitHub

Best starting point for your POC portfolio.

GitHub Repositories, Pull Requests, Actions, Releases, Packages, GitHub Apps, webhooks, rulesets, and security tooling.

[Official documentation](https://docs.github.com/?utm_source=chatgpt.com)

[Creditsafe Technology](https://images.openai.com/static-rsc-4/obrracwH8DRL7ExWjl8scv5Yok5lQAC-Q-h4Hgq9VKLeWfAeuolp0N3nV-D0AWC1iBo2GfG2dcC6IGqKpV6McryLMPwDrCwfykBpe9H5gmjDtUyFRG4K4zMeWkWqBHPo9dLEx2NUOdM2idZs5u2fmc4gxJdmvqHdaV3OL4zY0wQ?purpose=inline)

Azure DevOps

Particularly relevant for enterprise delivery and Microsoft-centric environments.

Azure Repos, Azure Pipelines, Azure Artifacts, Boards, Test Plans, service connections, service hooks, and branch policies.

[Official documentation](https://learn.microsoft.com/en-us/azure/devops/?utm_source=chatgpt.com)

[Contribute through the eyes of a new GitLabber](https://images.openai.com/static-rsc-4/GVQNLBNUt4I6mhhZzvpbjWLBpysfjXEOMSZEZ9PlPOVqP0BUjqD-Nh95iT-Duyo52M2v4O6VPqfvj0Lmdqrklbl4BC8B-nV2T_Q7Luzsr5fHpvhQzF_gOQ_8XXeLvk-Zu7BGxPA3eD6YlwEvrS4FjKTiTze4KwzLg0wsrLMq5mQ?purpose=inline)

GitLab

An integrated alternative with its own repository, CI/CD, security, and release workflows.

Repositories, merge requests, GitLab CI/CD, runners, package and container registries, environments, and deployment controls.

[Official documentation](https://docs.gitlab.com/?utm_source=chatgpt.com)

| Capability         | GitHub              | Azure DevOps    | GitLab                    |
| ------------------ | ------------------- | --------------- | ------------------------- |
| Source hosting     | GitHub Repositories | Azure Repos     | GitLab repositories       |
| Code review        | Pull requests       | Pull requests   | Merge requests            |
| CI/CD              | GitHub Actions      | Azure Pipelines | GitLab CI/CD              |
| Work tracking      | Issues and Projects | Azure Boards    | Issues and planning tools |
| Package registry   | GitHub Packages     | Azure Artifacts | Package Registry          |
| Event integrations | Webhooks and Apps   | Service Hooks   | Webhooks and integrations |

One important correction to the terminology in your question: Azure DevOps does not simply use GitHub. They are separate platforms that can integrate. Azure Pipelines can build GitHub-hosted repositories, and GitHub Actions can deploy to Azure services.&#x20;

[image](https://www.google.com/s2/favicons?domain=https://github.com\&sz=32)

GitHub

+1



Learn the underlying concepts first, then learn the platform-specific implementation.

# 9. The POC portfolio I would build in your position

Do not create 20 disconnected demos. Build one realistic data engineering platform and progressively add engineering capabilities to it.

Use a fictional healthcare analytics pipeline with Python, SQL, PySpark, Delta Lake, and Databricks-style deployment scripts. It is close enough to real data engineering work to be credible, but it does not require access to production data or infrastructure.

Select any POC to see what it should demonstrate and how you can prove it works.

## POC tracker

0 / 10 complete

Git and repository workflowFoundation1 weekPull request governanceFoundation1 weekAutomated CI pipelineCore1 to 2 weeksRun Python linting, SQL validation, unit tests, data-quality tests, and test reporting on every PR.Definition of doneSuccessful and intentionally failing runs, required status checks, and retained test artifacts.Packages and releasesCore1 to 2 weeksEnvironment-aware CDAdvanced2 weeksWebhook-driven integrationAdvanced1 to 2 weeksSecurity and identityAdvanced2 weeksMulti-repository engineering platformLead-level2 to 3 weeksProduction operationsLead-level2 weeksAzure DevOps implementationLead-level2 to 3 weeksCopy complete POC plan

These time estimates are rough effort estimates, not deadlines. Start with the first three and build working examples before moving to the next layer.

## 10. Your two-year roadmap to Lead Data Engineer

You have roughly two years until the five-year experience mark. I would use that time to build both technical depth and evidence that you can own engineering outcomes.

### Phase 1: Months 1 to 3

Fundamentals

- Git internals, branching, merge conflicts, tags, and recovery.
- GitHub repositories, pull requests, reviews, and branch rules.
- One CI workflow with automated tests.
- Basic Linux shell, HTTP, JSON, YAML, and REST APIs.

Exit criterion: You can explain and demonstrate a complete reviewed code change from branch creation through merge.

### Phase 2: Months 4 to 6

Delivery

- Packages, artifacts, semantic versioning, and releases.
- DEV/UAT/PROD deployment workflows.
- Environment approvals, secrets, and rollback.
- SQL, Python, and data-quality validation in CI.

Exit criterion: You can release a tested data pipeline version and promote it safely between environments.

### Phase 3: Months 7 to 12

Platform engineering

- Webhooks, API integrations, reusable workflows, and multi-repository architecture.
- Cloud identity, OIDC, least privilege, dependency security, and auditability.
- Databricks asset deployment, infrastructure as code, and environment drift.
- Azure Pipelines integration and platform comparison.

Exit criterion: Another engineer can use your shared pipeline framework without copying and independently maintaining all its logic.

### Phase 4: Months 13 to 18

Reliability

- Failure recovery, incident response, monitoring, and data reconciliation.
- Deployment safety, backward-compatible schema evolution, and idempotent jobs.
- Performance and cloud-cost controls.
- Technical design documents, tradeoff analysis, and architecture reviews.

Exit criterion: You can explain how the platform behaves during failures, not just when everything works.

### Phase 5: Months 19 to 24

Leadership evidence

- Standardize engineering practices across multiple repositories.
- Mentor another engineer through a PR and release workflow.
- Lead a design review and defend architectural tradeoffs.
- Measure deployment failure rate, lead time, recovery time, and test effectiveness.
- Document a complete platform architecture and operational runbook.

Exit criterion: You can demonstrate ownership of a production-oriented engineering system and show how you improved the team's delivery process.

## 11. What will actually make you lead-ready?

Be careful about a common trap: collecting tools and certificates can create the appearance of progress without proving that you can lead engineering work.

For your target role, I would prioritize these five capabilities.
<img width="803" height="500" alt="image" src="https://github.com/user-attachments/assets/ece181ff-9450-4910-87ba-85370d5bba5e" />


## 12. Your first POC should be this

Build a Data Engineering CI/CD Reference Platform with one GitHub repository containing:

- `src/`: Python data transformation and validation logic.
- `sql/`: SQL transformations and schema migrations.
- `tests/`: unit tests and data-quality tests.
- `configs/`: environment-specific, non-secret configuration.
- `deploy/`: deployment scripts.
- `.github/workflows/`: CI and deployment workflows.
- `docs/`: architecture, setup instructions, release process, and recovery runbook.

Then add the features in this order:

1. Branch-based development and reviewed pull requests.
2. Automated linting and tests.
3. Required PR checks and ownership rules.
4. Versioned package or deployment artifact.
5. Tagged release with release notes.
6. DEV/UAT/PROD deployment controls.
7. Secure cloud authentication and environment secrets.
8. Webhook-driven notifications and audit logging.
9. Failure injection, rollback, and incident documentation.
10. Reusable workflows for a second repository.

The second repository is important. A single repository with a successful pipeline proves that you can configure CI/CD. Two or more repositories consuming a shared engineering standard start to demonstrate that you can design a platform for a team.

My recommendation is to use GitHub as your learning environment, Python and SQL as your workload, and Azure/Databricks as your deployment target. Later, reproduce the essential workflow in Azure DevOps. That gives you both transferable knowledge and a credible portfolio for enterprise data engineering roles.
