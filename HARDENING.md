<!-- markdownlint-disable -->

# Hardening Report: issue-ops--parser/v4.2.0

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **issue-ops--parser/v4.2.0** was hardened automatically. 1 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

All `uses:` references across all workflow files use mutable version tags instead of pinned full-length SHA commit hashes. This exposes the workflows to supply-chain attacks where a compromised or updated tag could execute malicious code.

check-dist.yml: actions/checkout@v4, actions/setup-node@v4, actions/upload-artifact@v4
codeql.yml: actions/checkout@v4, github/codeql-action/init@v3, github/codeql-action/autobuild@v3, github/codeql-action/analyze@v3
continuous-delivery.yml: actions/checkout@v4, issue-ops/semver@v2, issue-ops/releaser@v2
continuous-integration.yml: actions/checkout@v4, actions/setup-node@v4
linter.yml: actions/checkout@v4, actions/setup-node@v4, oxsecurity/megalinter/flavors/javascript@v8

All should be pinned to a full 40-character commit SHA (e.g. `actions/checkout@11bd71901bbe5b1630ceea73d27597364c9af683 # v4`).

Locations:

- `.github/workflows/check-dist.yml:20`
- `.github/workflows/check-dist.yml:26`
- `.github/workflows/check-dist.yml:47`
- `.github/workflows/codeql.yml:24`
- `.github/workflows/codeql.yml:29`
- `.github/workflows/codeql.yml:35`
- `.github/workflows/codeql.yml:39`
- `.github/workflows/continuous-delivery.yml:24`
- `.github/workflows/continuous-delivery.yml:30`
- `.github/workflows/continuous-delivery.yml:37`
- `.github/workflows/continuous-integration.yml:19`
- `.github/workflows/continuous-integration.yml:25`
- `.github/workflows/linter.yml:21`
- `.github/workflows/linter.yml:27`
- `.github/workflows/linter.yml:33`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses

**Notes:**

Pinned all 15 unpinned `uses:` references across 5 workflow files:
- check-dist.yml: actions/checkout@v4 → @11d5960a326750d5838078e36cf38b85af677262, actions/setup-node@v4 → @49933ea5288caeca8642d1e84afbd3f7d6820020, actions/upload-artifact@v4 → @ea165f8d65b6e75b540449e92b4886f43607fa02
- codeql.yml: actions/checkout@v4 → @11d5960a326750d5838078e36cf38b85af677262, github/codeql-action/init@v3, autobuild@v3, analyze@v3 → all @4187e74d05793876e9989daffde9c3e66b4acd07
- continuous-delivery.yml: actions/checkout@v4 → @11d5960a326750d5838078e36cf38b85af677262, issue-ops/semver@v2 → @5b8bb084b6834d03ddb5c7c96c683a588a2072ca, issue-ops/releaser@v2 → @e6768024642153d17c157995e2684a3ebcae14e7
- continuous-integration.yml: actions/checkout@v4 → @11d5960a326750d5838078e36cf38b85af677262, actions/setup-node@v4 → @49933ea5288caeca8642d1e84afbd3f7d6820020
- linter.yml: actions/checkout@v4 → @11d5960a326750d5838078e36cf38b85af677262, actions/setup-node@v4 → @49933ea5288caeca8642d1e84afbd3f7d6820020, oxsecurity/megalinter/flavors/javascript@v8 → @sha256:c9ff53d369ffbf186465bad77c469337667da19dd944d6473a2f62b99a0a94e7
All original version tags preserved as inline comments (e.g., # v4).

