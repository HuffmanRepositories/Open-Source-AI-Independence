# Portfolio Security Posture — 2026-11-02

This document describes automated security checks actually configured in the HuffmanRepositories portfolio. It is not a security certification or claim of production readiness.

## Secret scanning

All 11 repositories now contain `.github/workflows/secret-scan.yml`.

- Triggers: pushes, pull requests, manual dispatch, and weekly schedule.
- Checkout: complete history (`fetch-depth: 0`) with checkout credentials not persisted.
- Scanner: Gitleaks CLI 8.30.1.
- Supply-chain verification: release archive SHA-256 is pinned and checked before execution.
- Coverage: `gitleaks git --redact --log-opts=--all`, scanning all reachable commits/ref history.
- Permissions: `contents: read`; no write token or secret required.
- Logs: redacted; scan report artifact upload is not enabled.

The first completed full-history scan pass across the 11 repositories reported no leaks in the scanned history. Subsequent pushes re-run the scan. A finding should be treated as a credential exposure: revoke/rotate first, then coordinate history remediation.

## CodeQL

SHA-pinned CodeQL Python analysis is configured for these repositories with Python validator code:

- OAC Fixtures
- OARMI
- P10 Memory Portability
- P11 Oracle Integrity
- P12 Retry / Idempotency
- P13 Delegation Scope
- P14 Delegated Budget

The latest observed CodeQL runs completed successfully and uploaded their analysis results to GitHub Code Scanning. **A successful upload is not the same as “zero alerts”; review the Security → Code scanning view for each repository.** The base OAC, mission hub, account-profile README, and private Blueprint are primarily protocol docs/fixtures/coordination rather than Python application code and are not included in the CodeQL Python matrix.

## Dependency update automation

All 11 repositories have `.github/dependabot.yml` with weekly GitHub Actions dependency update checks. The repos currently contain no conventional Python dependency manifest, so the config focuses on Actions. Gitleaks CLI itself is pinned by version and checksum in the scan workflow and requires deliberate periodic version updates.

## Current boundaries and settings that need owner-side verification

The available GitHub connector does not expose the needed security-alert and repository-admin endpoints for this account. As a result, the following are not confirmed:
- GitHub Dependabot security-alert status and alert inventory;
- GitHub native secret scanning and push protection status;
- classic branch protection and required status-check settings;
- private Blueprint ruleset / private repository security settings.

The public rulesets endpoint returned no rulesets for the public repositories. Classic branch protection reads were denied by the integration, so that does **not** prove whether classic protections are set.

## Recommendations

1. Review CodeQL findings from GitHub Security → Code scanning for all seven Python repos.
2. Review GitHub native Dependabot alerts and secret scanning/push protection in repo Settings → Security.
3. Require PR review and CI checks on each main branch after adding an independent maintainer.
4. Keep full-history secret scans enabled; rotate any real credential immediately if a finding appears.
5. Keep all projects marked research/draft until protocol/runtime conformance is separately established.
