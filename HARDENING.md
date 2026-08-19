<!-- markdownlint-disable -->

# Hardening Report: issue-ops--parser/v5.0.0

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **issue-ops--parser/v5.0.0** was hardened automatically. 1 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

All `uses:` references across the workflow files use mutable version tags instead of pinned 40-character SHA commit digests, making the action vulnerable to supply-chain attacks if any referenced action is compromised or its tag is moved. Failing references:

- `actions/checkout@v6` (check-dist.yml, codeql.yml, continuous-delivery.yml, continuous-integration.yml, linter.yml)
- `actions/setup-node@v6` (check-dist.yml, continuous-integration.yml, linter.yml)
- `actions/upload-artifact@v5` (check-dist.yml)
- `github/codeql-action/init@v4` (codeql.yml)
- `github/codeql-action/autobuild@v4` (codeql.yml)
- `github/codeql-action/analyze@v4` (codeql.yml)
- `issue-ops/semver@v2` (continuous-delivery.yml)
- `issue-ops/releaser@v2` (continuous-delivery.yml)
- `oxsecurity/megalinter/flavors/javascript@v9` (linter.yml)

Each should be pinned to a full SHA, e.g. `actions/checkout@11bd71901bbe5b1630ceea73d27597364c9af683 # v4`.

Locations:

- `.github/workflows/check-dist.yml:25`
- `.github/workflows/check-dist.yml:29`
- `.github/workflows/check-dist.yml:52`
- `.github/workflows/codeql.yml:31`
- `.github/workflows/codeql.yml:35`
- `.github/workflows/codeql.yml:41`
- `.github/workflows/codeql.yml:45`
- `.github/workflows/continuous-delivery.yml:26`
- `.github/workflows/continuous-delivery.yml:31`
- `.github/workflows/continuous-delivery.yml:38`
- `.github/workflows/continuous-integration.yml:19`
- `.github/workflows/continuous-integration.yml:23`
- `.github/workflows/linter.yml:26`
- `.github/workflows/linter.yml:30`
- `.github/workflows/linter.yml:40`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses

**Notes:**

Pinned all 9 unpinned action references across 5 workflow files to their full 40-character SHA commit digests, preserving the original version tag as an inline comment for readability. Actions pinned: actions/checkout@v6, actions/setup-node@v6, actions/upload-artifact@v5, github/codeql-action/init@v4, github/codeql-action/autobuild@v4, github/codeql-action/analyze@v4, issue-ops/semver@v2, issue-ops/releaser@v2, oxsecurity/megalinter/flavors/javascript@v9.

