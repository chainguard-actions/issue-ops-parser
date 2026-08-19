<!-- markdownlint-disable -->

# Hardening Report: issue-ops--parser/v4.1.0

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **issue-ops--parser/v4.1.0** was hardened automatically. 1 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

All `uses:` references across every workflow file use mutable version tags instead of pinned 40-character SHA digests. This exposes the action to supply-chain attacks where a compromised or updated tag could silently execute malicious code. Affected references:

**check-dist.yml**: `actions/checkout@v4`, `actions/setup-node@v4`, `actions/upload-artifact@v4`
**codeql.yml**: `actions/checkout@v4`, `github/codeql-action/init@v3`, `github/codeql-action/autobuild@v3`, `github/codeql-action/analyze@v3`
**continuous-delivery.yml**: `actions/checkout@v4`, `issue-ops/semver@v2`, `issue-ops/releaser@v2`
**continuous-integration.yml**: `actions/checkout@v4`, `actions/setup-node@v4`
**linter.yml**: `actions/checkout@v4`, `actions/setup-node@v4`, `oxsecurity/megalinter/flavors/javascript@v8`

All should be pinned to full 40-character commit SHAs (e.g., `actions/checkout@11bd71901bbe5b1630ceea73d27597364c9af683 # v4`).

Locations:

- `.github/workflows/check-dist.yml:25`
- `.github/workflows/check-dist.yml:29`
- `.github/workflows/check-dist.yml:52`
- `.github/workflows/codeql.yml:28`
- `.github/workflows/codeql.yml:33`
- `.github/workflows/codeql.yml:39`
- `.github/workflows/codeql.yml:44`
- `.github/workflows/continuous-delivery.yml:26`
- `.github/workflows/continuous-delivery.yml:31`
- `.github/workflows/continuous-delivery.yml:38`
- `.github/workflows/continuous-integration.yml:18`
- `.github/workflows/continuous-integration.yml:23`
- `.github/workflows/linter.yml:20`
- `.github/workflows/linter.yml:25`
- `.github/workflows/linter.yml:38`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses

**Notes:**

Pinned all 15 unpinned `uses:` references across 5 workflow files to full 40-character commit SHAs:

**check-dist.yml**:
- `actions/checkout@v4` → `actions/checkout@11d5960a326750d5838078e36cf38b85af677262 # v4`
- `actions/setup-node@v4` → `actions/setup-node@49933ea5288caeca8642d1e84afbd3f7d6820020 # v4`
- `actions/upload-artifact@v4` → `actions/upload-artifact@ea165f8d65b6e75b540449e92b4886f43607fa02 # v4`

**codeql.yml**:
- `actions/checkout@v4` → `actions/checkout@11d5960a326750d5838078e36cf38b85af677262 # v4`
- `github/codeql-action/init@v3` → `github/codeql-action/init@b7351df727350dca84cb9d725d57dcf5bc82ba26 # v3`
- `github/codeql-action/autobuild@v3` → `github/codeql-action/autobuild@b7351df727350dca84cb9d725d57dcf5bc82ba26 # v3`
- `github/codeql-action/analyze@v3` → `github/codeql-action/analyze@b7351df727350dca84cb9d725d57dcf5bc82ba26 # v3`

**continuous-delivery.yml**:
- `actions/checkout@v4` → `actions/checkout@11d5960a326750d5838078e36cf38b85af677262 # v4`
- `issue-ops/semver@v2` → `issue-ops/semver@5b8bb084b6834d03ddb5c7c96c683a588a2072ca # v2`
- `issue-ops/releaser@v2` → `issue-ops/releaser@e6768024642153d17c157995e2684a3ebcae14e7 # v2`

**continuous-integration.yml**:
- `actions/checkout@v4` → `actions/checkout@11d5960a326750d5838078e36cf38b85af677262 # v4`
- `actions/setup-node@v4` → `actions/setup-node@49933ea5288caeca8642d1e84afbd3f7d6820020 # v4`

**linter.yml**:
- `actions/checkout@v4` → `actions/checkout@11d5960a326750d5838078e36cf38b85af677262 # v4`
- `actions/setup-node@v4` → `actions/setup-node@49933ea5288caeca8642d1e84afbd3f7d6820020 # v4`
- `oxsecurity/megalinter/flavors/javascript@v8` → `oxsecurity/megalinter/flavors/javascript@e08c2b05e3dbc40af4c23f41172ef1e068a7d651 # v8`

Note: check-dist.yml was rewritten entirely after an edit corruption was detected during verification.

