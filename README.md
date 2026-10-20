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

\#chatgpt-mermaid-\_r_2ak\_{font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,Segoe UI,Helvetica,Apple Color Emoji,Arial,sans-serif,Segoe UI Emoji,Segoe UI Symbol;font-size:16px;fill:rgb(237, 237, 237);}@keyframes edge-animation-frame{from{stroke-dashoffset:0;}}@keyframes dash{to{stroke-dashoffset:0;}}#chatgpt-mermaid-\_r_2ak\_ .edge-animation-slow{stroke-dasharray:9,5!important;stroke-dashoffset:900;animation:dash 50s linear infinite;stroke-linecap:round;}#chatgpt-mermaid-\_r_2ak\_ .edge-animation-fast{stroke-dasharray:9,5!important;stroke-dashoffset:900;animation:dash 20s linear infinite;stroke-linecap:round;}#chatgpt-mermaid-\_r_2ak\_ .error-icon{fill:rgb(48, 48, 48);}#chatgpt-mermaid-\_r_2ak\_ .error-text{fill:rgb(237, 237, 237);stroke:rgb(237, 237, 237);}#chatgpt-mermaid-\_r_2ak\_ .edge-thickness-normal{stroke-width:1px;}#chatgpt-mermaid-\_r_2ak\_ .edge-thickness-thick{stroke-width:3.5px;}#chatgpt-mermaid-\_r_2ak\_ .edge-pattern-solid{stroke-dasharray:0;}#chatgpt-mermaid-\_r_2ak\_ .edge-thickness-invisible{stroke-width:0;fill:none;}#chatgpt-mermaid-\_r_2ak\_ .edge-pattern-dashed{stroke-dasharray:3;}#chatgpt-mermaid-\_r_2ak\_ .edge-pattern-dotted{stroke-dasharray:2;}#chatgpt-mermaid-\_r_2ak\_ .marker{fill:rgb(175, 175, 175);stroke:rgb(175, 175, 175);}#chatgpt-mermaid-\_r_2ak\_ .marker.cross{stroke:rgb(175, 175, 175);}#chatgpt-mermaid-\_r_2ak\_ svg{font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,Segoe UI,Helvetica,Apple Color Emoji,Arial,sans-serif,Segoe UI Emoji,Segoe UI Symbol;font-size:16px;}#chatgpt-mermaid-\_r_2ak\_ p{margin:0;}#chatgpt-mermaid-\_r_2ak\_ .label{font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,Segoe UI,Helvetica,Apple Color Emoji,Arial,sans-serif,Segoe UI Emoji,Segoe UI Symbol;color:rgb(237, 237, 237);}#chatgpt-mermaid-\_r_2ak\_ .cluster-label text{fill:rgb(237, 237, 237);}#chatgpt-mermaid-\_r_2ak\_ .cluster-label span{color:rgb(237, 237, 237);}#chatgpt-mermaid-\_r_2ak\_ .cluster-label span p{background-color:transparent;}#chatgpt-mermaid-\_r_2ak\_ .label text,#chatgpt-mermaid-\_r_2ak\_ span{fill:rgb(237, 237, 237);color:rgb(237, 237, 237);}#chatgpt-mermaid-\_r_2ak\_ .node rect,#chatgpt-mermaid-\_r_2ak\_ .node circle,#chatgpt-mermaid-\_r_2ak\_ .node ellipse,#chatgpt-mermaid-\_r_2ak\_ .node polygon,#chatgpt-mermaid-\_r_2ak\_ .node path{fill:rgb(17, 40, 19);stroke:rgb(58, 132, 63);stroke-width:1px;}#chatgpt-mermaid-\_r_2ak\_ .rough-node .label text,#chatgpt-mermaid-\_r_2ak\_ .node .label text,#chatgpt-mermaid-\_r_2ak\_ .image-shape .label,#chatgpt-mermaid-\_r_2ak\_ .icon-shape .label{text-anchor:middle;}#chatgpt-mermaid-\_r_2ak\_ .node .katex path{fill:#000;stroke:#000;stroke-width:1px;}#chatgpt-mermaid-\_r_2ak\_ .rough-node .label,#chatgpt-mermaid-\_r_2ak\_ .node .label,#chatgpt-mermaid-\_r_2ak\_ .image-shape .label,#chatgpt-mermaid-\_r_2ak\_ .icon-shape .label{text-align:center;}#chatgpt-mermaid-\_r_2ak\_ .node.clickable{cursor:pointer;}#chatgpt-mermaid-\_r_2ak\_ .root .anchor path{fill:rgb(175, 175, 175)!important;stroke-width:0;stroke:rgb(175, 175, 175);}#chatgpt-mermaid-\_r_2ak\_ .arrowheadPath{fill:rgb(175, 175, 175);}#chatgpt-mermaid-\_r_2ak\_ .edgePath .path{stroke:rgb(175, 175, 175);stroke-width:1px;}#chatgpt-mermaid-\_r_2ak\_ .flowchart-link{stroke:rgb(175, 175, 175);fill:none;}#chatgpt-mermaid-\_r_2ak\_ .edgeLabel{background-color:rgb(0, 0, 0);text-align:center;}#chatgpt-mermaid-\_r_2ak\_ .edgeLabel p{background-color:rgb(0, 0, 0);}#chatgpt-mermaid-\_r_2ak\_ .edgeLabel rect{opacity:0.5;background-color:rgb(0, 0, 0);fill:rgb(0, 0, 0);}#chatgpt-mermaid-\_r_2ak\_ .labelBkg{background-color:rgba(0, 0, 0, 0.5);}#chatgpt-mermaid-\_r_2ak\_ .cluster rect{fill:rgb(48, 48, 48);stroke:rgba(255, 255, 255, 0.15);stroke-width:1px;}#chatgpt-mermaid-\_r_2ak\_ .cluster text{fill:rgb(237, 237, 237);}#chatgpt-mermaid-\_r_2ak\_ .cluster span{color:rgb(237, 237, 237);}#chatgpt-mermaid-\_r_2ak\_ div.mermaidTooltip{position:absolute;text-align:center;max-width:200px;padding:2px;font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,Segoe UI,Helvetica,Apple Color Emoji,Arial,sans-serif,Segoe UI Emoji,Segoe UI Symbol;font-size:12px;background:rgb(48, 48, 48);border:1px solid rgba(255, 255, 255, 0.15);border-radius:2px;pointer-events:none;z-index:100;}#chatgpt-mermaid-\_r_2ak\_ .flowchartTitleText{text-anchor:middle;font-size:18px;fill:rgb(237, 237, 237);}#chatgpt-mermaid-\_r_2ak\_ rect.text{fill:none;stroke-width:0;}#chatgpt-mermaid-\_r_2ak\_ .icon-shape,#chatgpt-mermaid-\_r_2ak\_ .image-shape{background-color:rgb(0, 0, 0);text-align:center;}#chatgpt-mermaid-\_r_2ak\_ .icon-shape p,#chatgpt-mermaid-\_r_2ak\_ .image-shape p{background-color:rgb(0, 0, 0);padding:2px;}#chatgpt-mermaid-\_r_2ak\_ .icon-shape .label rect,#chatgpt-mermaid-\_r_2ak\_ .image-shape .label rect{opacity:0.5;background-color:rgb(0, 0, 0);fill:rgb(0, 0, 0);}#chatgpt-mermaid-\_r_2ak\_ .label-icon{display:inline-block;height:1em;overflow:visible;vertical-align:-0.125em;}#chatgpt-mermaid-\_r_2ak\_ .node .label-icon path{fill:currentColor;stroke:revert;stroke-width:revert;}#chatgpt-mermaid-\_r_2ak\_ .node .neo-node{stroke:rgb(58, 132, 63);}#chatgpt-mermaid-\_r_2ak\_ [data-look="neo"].node rect,#chatgpt-mermaid-\_r_2ak\_ [data-look="neo"].cluster rect,#chatgpt-mermaid-\_r_2ak\_ [data-look="neo"].node polygon{stroke:url(#chatgpt-mermaid-\_r_2ak\_-gradient);filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_2ak\_ [data-look="neo"].swimlane.cluster rect{filter:none;}#chatgpt-mermaid-\_r_2ak\_ [data-look="neo"].node path{stroke:url(#chatgpt-mermaid-\_r_2ak\_-gradient);stroke-width:1px;}#chatgpt-mermaid-\_r_2ak\_ [data-look="neo"].node .outer-path{filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_2ak\_ [data-look="neo"].node .neo-line path{stroke:rgb(58, 132, 63);filter:none;}#chatgpt-mermaid-\_r_2ak\_ [data-look="neo"].node circle{stroke:url(#chatgpt-mermaid-\_r_2ak\_-gradient);filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_2ak\_ [data-look="neo"].node circle .state-start{fill:#000000;}#chatgpt-mermaid-\_r_2ak\_ [data-look="neo"].icon-shape .icon{fill:url(#chatgpt-mermaid-\_r_2ak\_-gradient);filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_2ak\_ [data-look="neo"].icon-shape .icon-neo path{stroke:url(#chatgpt-mermaid-\_r_2ak\_-gradient);filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_2ak\_ .node text{font-size:14px;font-weight:600;letter-spacing:normal;fill:rgb(140, 223, 173);}#chatgpt-mermaid-\_r_2ak\_ .edgeLabels text{font-size:13px;font-weight:600;letter-spacing:-0.08px;fill:rgb(140, 223, 173);}#chatgpt-mermaid-\_r_2ak\_ .node tspan[font-weight="normal"],#chatgpt-mermaid-\_r_2ak\_ .edgeLabels tspan[font-weight="normal"]{font-weight:600;}#chatgpt-mermaid-\_r_2ak\_ .edgeLabel .label rect{opacity:1;rx:13px;ry:13px;fill:rgb(2, 28, 12);stroke:rgb(26, 75, 45);stroke-width:1px;}#chatgpt-mermaid-\_r_2ak\_ .node rect,#chatgpt-mermaid-\_r_2ak\_ .node circle,#chatgpt-mermaid-\_r_2ak\_ .node ellipse,#chatgpt-mermaid-\_r_2ak\_ .node polygon,#chatgpt-mermaid-\_r_2ak\_ .node path{fill:rgb(0, 55, 22);stroke:rgba(255, 255, 255, 0.1);stroke-width:1px;}#chatgpt-mermaid-\_r_2ak\_ .node rect{rx:16px;ry:16px;}#chatgpt-mermaid-\_r_2ak\_ .node.mermaid-decision .label-container{fill:rgb(2, 28, 12);stroke:rgb(26, 75, 45);stroke-dasharray:2px,2px;}#chatgpt-mermaid-\_r_2ak\_ .edgePaths .flowchart-link{stroke:rgb(175, 175, 175);stroke-width:1px;stroke-linecap:round;stroke-linejoin:round;}#chatgpt-mermaid-\_r_2ak\_ .marker{fill:rgb(175, 175, 175);stroke:rgb(175, 175, 175);}#chatgpt-mermaid-\_r_2ak\_ :root{--mermaid-font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,Segoe UI,Helvetica,Apple Color Emoji,Arial,sans-serif,Segoe UI Emoji,Segoe UI Symbol;}main branchCreate feature branchEdit SQL / PythonCommit changesPush branch to remoteOpen pull requestAutomated checks and reviewApproved and checks pass?Merge into mainBuild and testTag version and publish releaseDeploy to target environmentNoYes

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

[GitHub API: How to retrieve the combined pull request status from commit statuses, check runs, and GitHub Action results - DEV Community](https://images.openai.com/static-rsc-4/uX3BVuCi1mg_QyLmfUB6wdIDb7Oe9I_b8spf-Dsb80nVN6TQ7Rp-Ss6vVs_CP3YnAhfc1eLJNSqJ4x_pA04kXLcqTAZTvgp7aQ_RB6lznAH3Hnzh1HgKedkgmdO78JC35vnW-kHzpyr5U2STLstCwg6Izq1dYfQRCRcLMa88V18?purpose=inline)

Pull requests (PRs)

A proposed change from one branch into another. PRs enable code review, comments, automated validation, approvals, and controlled integration.

POC: require one reviewer, a passing test workflow, and resolution of review conversations before merging.

[The Ultimate CODEOWNERS File Guide for Better Code Reviews - Aviator Blog](https://images.openai.com/static-rsc-4/ppybe_KKjI26jIpd8JjKCTtegtnKJCA1lyIArk1AhPTbV0T56JFvQCdfOepOoxgsD_rTTEJzIUVi06R6A-rys_QQjQn2MtY2NnVYvPij7m2KVMdDnpGlOLjvmJdja9PGsTG5a0xFYfVZp8-N9hrWtiYaC_T1Lawv4EVsNCD05pg?purpose=inline)

Merge strategies and branch rules

Learn merge commits, squash merges, and rebase merges. Configure protected branches or repository rulesets, required reviews, required status checks, and ownership-based reviews.

POC: demonstrate that a failing SQL test blocks a merge into `main`.

[Quickstart for GitHub Actions - GitHub Docs](https://images.openai.com/static-rsc-4/6ACUCBGn-4X25SKeYcdMCLol6oABSdzjA__y5S22ybNY7dP1rDgySFJwl_fGp8qI7xVJ6pwNVLSO1kle-JvES9hMyjvLiH3hrp3KiVeRLPto10N2d-i4BMmFL6PHb3uKpfi3a5D0h7kRLtuNSzrlLG0PF-VjxoxjlW0qaIX7s7s?purpose=inline)

GitHub Actions

A workflow is triggered by an event and contains jobs that run on runners. Jobs contain steps, which run commands or reusable actions.

POC: lint Python and SQL, run unit tests, produce a test report, and fail the workflow when a check fails.

[Azure Cost Estimator - automated cost estimations for ARM Templates, Bicep and Terraform](https://images.openai.com/static-rsc-4/495mM6p37VR5wz-KHEUIMs8Zh-6DhCG4DXsWnB2KYinVF-AZJ4W97LoIQvABvUb5QuHNzzHtrq3bYc_iyRjaVwPHeEPVm_mSIuqv4-ZMFGMyLd7edcptpWS1nVCzeZK5f6UFp17I7q7iwPQb8OUDFKLptvWjksmzN_M6_9m7vgg?purpose=inline)

Tags and releases

Tags identify versions in Git history. A GitHub Release associates a version tag with release notes and optional downloadable assets.

POC: publish `v1.0.0` with changelog, deployment bundle, and a documented rollback version.

[GitHub Packages | Christos Galanopoulos](https://images.openai.com/static-rsc-4/BjxIHa8JYPbVnYuoqwockHanOY9gPBHGu8JnO-gr1vIGbDFiMIXH6LHhwD1A5X9dWDTj6LsQfuvJYVQaN0xTV3h8mm8IPA9_KTspM1TNEWAsGykARuN7UxwzdLpMbbpi6KbETya-yMimnkKZWCCoj_OYdFHeaMkRonRh5rSb7Fk?purpose=inline)

Packages and artifacts

Packages distribute reusable software such as Python libraries, npm packages, NuGet packages, or container images. Build artifacts can also be stored as pipeline outputs.

POC: package a reusable Python data-quality library, version it, publish it, and install it in a separate project.

[Webhooks vs APIs: Data Ingestion Strategies for Engineering](https://images.openai.com/static-rsc-4/WoALMJBrUnAHiDPdnsxzoemuAqgts3c7PUP3DZpZw-zTLkNLHCmjMwLtfnakwvBBY-M17yfbR0UxhBA6IiY7dqaECWj7FwcMoXS01dWiORDi0zIpMmOKWU2OILs6-EWZguOuk__a7R7r5PXY-Pl_b7wuV7rsMAqXvhC7doMzGw0?purpose=inline)

Webhooks and APIs

A webhook sends an HTTP request when an event occurs. APIs let an application query or change platform resources. They are complementary, not interchangeable.

POC: a PR event triggers a service that validates metadata, records an audit event, and sends a notification.

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

1\. Source code

The SQL, Python, YAML, notebooks, and configuration files maintained in Git.

Example: the code for your provider-matching pipeline.

2\. Build artifact

An output produced from source code or a build process.

Example: a versioned wheel file, a deployment bundle, or a packaged set of SQL migration scripts.

3\. Package

A distributable, versioned unit that consumers can install or retrieve from a registry.

Example: `data_quality_lib==1.2.0` published to a Python package registry.

4\. Release

A named version of a project, often linked to a Git tag, release notes, and downloadable assets.

Example: `v1.2.0`, documenting new validation rules and breaking changes.

5\. Deployment

Installing or applying a specific version to an environment.

Example: deploying the tested release to Databricks DEV, then UAT, then PROD.

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

Event

push, pull_request, release, schedule, manual dispatch

Workflow

YAML file in `.github/workflows/`

Job 1

Lint and static checks

Job 2

Unit and data tests

Runner executes steps

Shell commands, scripts, or reusable actions

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

Notification ServiceAudit StoreValidation ServiceWebhook ReceiverGitHubNotification ServiceAudit StoreValidation ServiceWebhook ReceiverGitHub#chatgpt-mermaid-\_r_2e7\_{font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,Segoe UI,Helvetica,Apple Color Emoji,Arial,sans-serif,Segoe UI Emoji,Segoe UI Symbol;font-size:16px;fill:rgb(237, 237, 237);}@keyframes edge-animation-frame{from{stroke-dashoffset:0;}}@keyframes dash{to{stroke-dashoffset:0;}}#chatgpt-mermaid-\_r_2e7\_ .edge-animation-slow{stroke-dasharray:9,5!important;stroke-dashoffset:900;animation:dash 50s linear infinite;stroke-linecap:round;}#chatgpt-mermaid-\_r_2e7\_ .edge-animation-fast{stroke-dasharray:9,5!important;stroke-dashoffset:900;animation:dash 20s linear infinite;stroke-linecap:round;}#chatgpt-mermaid-\_r_2e7\_ .error-icon{fill:rgb(48, 48, 48);}#chatgpt-mermaid-\_r_2e7\_ .error-text{fill:rgb(237, 237, 237);stroke:rgb(237, 237, 237);}#chatgpt-mermaid-\_r_2e7\_ .edge-thickness-normal{stroke-width:1px;}#chatgpt-mermaid-\_r_2e7\_ .edge-thickness-thick{stroke-width:3.5px;}#chatgpt-mermaid-\_r_2e7\_ .edge-pattern-solid{stroke-dasharray:0;}#chatgpt-mermaid-\_r_2e7\_ .edge-thickness-invisible{stroke-width:0;fill:none;}#chatgpt-mermaid-\_r_2e7\_ .edge-pattern-dashed{stroke-dasharray:3;}#chatgpt-mermaid-\_r_2e7\_ .edge-pattern-dotted{stroke-dasharray:2;}#chatgpt-mermaid-\_r_2e7\_ .marker{fill:rgb(175, 175, 175);stroke:rgb(175, 175, 175);}#chatgpt-mermaid-\_r_2e7\_ .marker.cross{stroke:rgb(175, 175, 175);}#chatgpt-mermaid-\_r_2e7\_ svg{font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,Segoe UI,Helvetica,Apple Color Emoji,Arial,sans-serif,Segoe UI Emoji,Segoe UI Symbol;font-size:16px;}#chatgpt-mermaid-\_r_2e7\_ p{margin:0;}#chatgpt-mermaid-\_r_2e7\_ .actor{stroke:rgb(58, 132, 63);fill:rgb(17, 40, 19);stroke-width:1;}#chatgpt-mermaid-\_r_2e7\_ rect.actor.outer-path[data-look="neo"]{filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_2e7\_ rect.note[data-look="neo"]{stroke:rgb(172, 79, 35);fill:rgb(48, 48, 48);filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_2e7\_ text.actor>tspan{fill:rgb(237, 237, 237);stroke:none;}#chatgpt-mermaid-\_r_2e7\_ .actor-line{stroke:rgb(175, 175, 175);}#chatgpt-mermaid-\_r_2e7\_ .innerArc{stroke-width:1.5;stroke-dasharray:none;}#chatgpt-mermaid-\_r_2e7\_ .messageLine0{stroke-width:1.5;stroke-dasharray:none;stroke:rgb(175, 175, 175);}#chatgpt-mermaid-\_r_2e7\_ .messageLine1{stroke-width:1.5;stroke-dasharray:2,2;stroke:rgb(175, 175, 175);}#chatgpt-mermaid-\_r_2e7\_ [id$="-arrowhead"] path{fill:rgb(175, 175, 175);stroke:rgb(175, 175, 175);}#chatgpt-mermaid-\_r_2e7\_ .sequenceNumber{fill:#505050;}#chatgpt-mermaid-\_r_2e7\_ [id$="-sequencenumber"]{fill:rgb(175, 175, 175);}#chatgpt-mermaid-\_r_2e7\_ [id$="-crosshead"] path{fill:rgb(175, 175, 175);stroke:rgb(175, 175, 175);}#chatgpt-mermaid-\_r_2e7\_ .messageText{fill:rgb(237, 237, 237);stroke:none;}#chatgpt-mermaid-\_r_2e7\_ .labelBox{stroke:rgba(255, 255, 255, 0.15);fill:rgb(0, 0, 0);filter:none;}#chatgpt-mermaid-\_r_2e7\_ .labelText,#chatgpt-mermaid-\_r_2e7\_ .labelText>tspan{fill:rgb(237, 237, 237);stroke:none;}#chatgpt-mermaid-\_r_2e7\_ .loopText,#chatgpt-mermaid-\_r_2e7\_ .loopText>tspan{fill:rgb(237, 237, 237);stroke:none;}#chatgpt-mermaid-\_r_2e7\_ .sectionTitle,#chatgpt-mermaid-\_r_2e7\_ .sectionTitle>tspan{fill:rgb(237, 237, 237);stroke:none;}#chatgpt-mermaid-\_r_2e7\_ .loopLine{stroke-width:2px;stroke-dasharray:2,2;stroke:rgba(255, 255, 255, 0.15);fill:rgba(255, 255, 255, 0.15);}#chatgpt-mermaid-\_r_2e7\_ .note{stroke:rgb(172, 79, 35);fill:rgb(48, 48, 48);}#chatgpt-mermaid-\_r_2e7\_ .noteText,#chatgpt-mermaid-\_r_2e7\_ .noteText>tspan{fill:rgb(237, 237, 237);stroke:none;font-weight:normal;}#chatgpt-mermaid-\_r_2e7\_ .activation0{fill:rgb(48, 48, 48);stroke:hsl(0, 0%, 8.8235294118%);}#chatgpt-mermaid-\_r_2e7\_ .activation1{fill:rgb(48, 48, 48);stroke:hsl(0, 0%, 8.8235294118%);}#chatgpt-mermaid-\_r_2e7\_ .activation2{fill:rgb(48, 48, 48);stroke:hsl(0, 0%, 8.8235294118%);}#chatgpt-mermaid-\_r_2e7\_ .actorPopupMenu{position:absolute;}#chatgpt-mermaid-\_r_2e7\_ .actorPopupMenuPanel{position:absolute;fill:rgb(17, 40, 19);box-shadow:0px 8px 16px 0px rgba(0,0,0,0.2);filter:drop-shadow(3px 5px 2px rgb(0 0 0 / 0.4));}#chatgpt-mermaid-\_r_2e7\_ .actor-man circle,#chatgpt-mermaid-\_r_2e7\_ line{fill:rgb(17, 40, 19);stroke-width:2px;}#chatgpt-mermaid-\_r_2e7\_ g rect.rect{filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));stroke:rgb(58, 132, 63);}#chatgpt-mermaid-\_r_2e7\_ .node .neo-node{stroke:rgb(58, 132, 63);}#chatgpt-mermaid-\_r_2e7\_ [data-look="neo"].node rect,#chatgpt-mermaid-\_r_2e7\_ [data-look="neo"].cluster rect,#chatgpt-mermaid-\_r_2e7\_ [data-look="neo"].node polygon{stroke:url(#chatgpt-mermaid-\_r_2e7\_-gradient);filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_2e7\_ [data-look="neo"].swimlane.cluster rect{filter:none;}#chatgpt-mermaid-\_r_2e7\_ [data-look="neo"].node path{stroke:url(#chatgpt-mermaid-\_r_2e7\_-gradient);stroke-width:1px;}#chatgpt-mermaid-\_r_2e7\_ [data-look="neo"].node .outer-path{filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_2e7\_ [data-look="neo"].node .neo-line path{stroke:rgb(58, 132, 63);filter:none;}#chatgpt-mermaid-\_r_2e7\_ [data-look="neo"].node circle{stroke:url(#chatgpt-mermaid-\_r_2e7\_-gradient);filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_2e7\_ [data-look="neo"].node circle .state-start{fill:#000000;}#chatgpt-mermaid-\_r_2e7\_ [data-look="neo"].icon-shape .icon{fill:url(#chatgpt-mermaid-\_r_2e7\_-gradient);filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_2e7\_ [data-look="neo"].icon-shape .icon-neo path{stroke:url(#chatgpt-mermaid-\_r_2e7\_-gradient);filter:drop-shadow( 1px 2px 2px rgba(185,185,185,1));}#chatgpt-mermaid-\_r_2e7\_ :root{--mermaid-font-family:-apple-system-body,ui-sans-serif,-apple-system,system-ui,Segoe UI,Helvetica,Apple Color Emoji,Arial,sans-serif,Segoe UI Emoji,Segoe UI Symbol;}Pull request event + payloadVerify signatureCheck delivery IDReturn HTTP 2xxQueue eventValidate repository and PR metadataRecord event and outcomeNotify on failure or success

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

Architecture

You can explain repository boundaries, environment separation, shared libraries, deployment dependencies, and why the system is designed that way.

Governance and security

You know how to prevent unauthorized changes, protect production credentials, restrict CI permissions, and create an auditable release process.

Reliability

You test failure scenarios, understand retries and idempotency, can recover a failed deployment, and know how to detect data corruption.

Engineering leadership

You establish review standards, explain decisions clearly, mentor others, and choose appropriate levels of process rather than imposing maximum process everywhere.

Measurable impact

You can demonstrate improvements in deployment lead time, failure rates, recovery time, testing coverage, or engineering effort. You measure the baseline instead of inventing impressive percentages.

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
