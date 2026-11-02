# Project Map

This map distinguishes repositories that exist from ideas that have not passed a creation gate. Repository presence does not imply stable status, independent review, or production readiness.

## Current portfolio

| Project | Status | Purpose | Boundary |
|---|---|---|---|
| [Open Source AI Independence](https://github.com/HuffmanRepositories/Open-Source-AI-Independence) | Mission hub | Coordination, mission, roadmap, community onboarding | Not a software product or guarantee of maturity |
| [Open Agent Compatibility (OAC)](https://github.com/HuffmanRepositories/Open-Agent-Compatibility) | Research | Version-pinned mapping and compatibility analysis across agent protocols | No universal protocol, runtime, or certification |
| [OAC Fixtures](https://github.com/HuffmanRepositories/Open-Agent-Compatibility-Fixtures) | Draft fixture corpus | Reproducible mapping/interoperability examples | Fixture validation is not protocol conformance |
| [Open Agent Run Metrics Interop (OARMI)](https://github.com/HuffmanRepositories/Open-Agent-Run-Metrics-Interop) | Draft fixture corpus | Usage/accounting interchange questions and test vectors | Not billing, pricing, budget enforcement, or a standard |
| [Agent Memory Portability Tests](https://github.com/HuffmanRepositories/Agent-Memory-Portability-Tests) | Draft fixture corpus | Export/import, migration, provenance, retention, deletion, loss cases | Not a memory protocol, database, SDK, or certification |
| [Agent Evaluation Oracle Integrity Fixtures](https://github.com/HuffmanRepositories/Agent-Evaluation-Oracle-Integrity-Fixtures) | Draft fixture corpus | Integrity risks and toy expected observations for evaluation systems | Not a benchmark, exploit kit, or security certification |
| [Agent Tool Retry & Idempotency Fixtures](https://github.com/HuffmanRepositories/Agent-Tool-Retry-Idempotency-Fixtures) | Draft fixture corpus | Side-effect retries, idempotency, ambiguous outcomes, reconciliation | Not a retry engine or exactly-once guarantee |
| [Agent Delegation Scope Boundary Fixtures](https://github.com/HuffmanRepositories/Agent-Delegation-Scope-Boundary-Fixtures) | Draft fixture corpus | Parent/child authority constraints, nested grants, revocation, scope | Not an auth protocol, policy engine, or runtime |
| [Agent Delegated Budget Enforcement Fixtures](https://github.com/HuffmanRepositories/Agent-Delegated-Budget-Enforcement-Fixtures) | Draft fixture corpus | Hierarchical reservation, allocation, settlement, and budget edge cases | Not a budget manager, billing service, or standard |

**Maturity note:** the fixture repositories are synthetic draft research artifacts. Passing CI verifies only their current structural checks and tests. No stable release, independent semantic review, or production conformance claim is implied.

| [HuffmanRepositories profile README](https://github.com/HuffmanRepositories/HuffmanRepositories) | Account profile / discovery | Account-level portfolio links and broader research identity | Not a technical implementation |


## Portfolio automation and security baseline

- **Gitleaks full-history scan:** configured in all 11 account repositories. It checks out all history, downloads Gitleaks CLI v8.30.1, verifies the release SHA-256, and runs a redacted scan over all reachable refs/commits. The first completed full-history pass reported no leaks.
- **CodeQL Python analysis:** configured for the seven public repositories containing Python validators. Latest observed CodeQL workflows completed successfully and uploaded analysis results; review any alerts in each repository's GitHub Security tab.
- **Dependabot:** weekly GitHub Actions dependency update checks are configured in all 11 repositories.
- **Workflow supply-chain hygiene:** GitHub Actions are pinned to immutable commit SHAs and checkout uses `persist-credentials: false` with read-only repository permissions where applicable.

**Security scope:** these checks cover secret patterns in reachable Git history and CodeQL-supported Python source. They do not replace runtime testing, dependency-alert review, branch-protection verification, or an independent security audit. GitHub-native Dependabot alert, push-protection, secret-scanning, and branch-protection settings still require owner-side verification. See [Security posture](security-posture.md).

## Deferred / proposed work

| Workstream | Purpose | Gate before creating another repository |
|---|---|---|
| Open infrastructure index | Discover/connect projects and standards | Demonstrate a differentiated discovery problem; avoid registry duplication |
| AI discovery metadata | Help humans and AI tools navigate project information | Coordinate with existing manifests/registries |
| Human/system coordination | Handoff, approvals, communication, auditability | Identify a concrete unmet workflow |
| Decentralized control | Local-first, federated, and P2P patterns | Specify use case and tradeoffs |
| Evidence reliability | Claim status and provenance | Avoid duplicating existing OSINT/evidence tools |
| System verification | Compatibility tests and safe differential analysis | Define a narrow verification target |
| Reliability benchmark | Reproducible evaluation of failure modes | Identify a unique metric and methodology |

Do not create a repository simply to increase repository count. Require validated need, a maintainer, distinct scope, a testable first milestone, and an explicit overlap review.
