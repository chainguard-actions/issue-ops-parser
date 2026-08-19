<!-- markdownlint-disable -->

# Hardening Report: issue-ops--parser/v4.0.0

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **issue-ops--parser/v4.0.0** was hardened automatically. 1 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

All `uses:` references across the workflow files use mutable version tags instead of full 40-character SHA commit digests, making the workflows vulnerable to supply-chain attacks if a tag is moved or a dependency is compromised.

Failing references in .github/workflows/check-dist.yml:
- `uses: actions/checkout@v4` (line 23)
- `uses: actions/setup-node@v4` (line 27)
- `uses: actions/upload-artifact@v4` (line 50)

Failing references in .github/workflows/codeql.yml:
- `uses: actions/checkout@v4` (line 30)
- `uses: github/codeql-action/init@v3` (line 34)
- `uses: github/codeql-action/autobuild@v3` (line 39)
- `uses: github/codeql-action/analyze@v3` (line 43)

Failing references in .github/workflows/continuous-delivery.yml:
- `uses: actions/checkout@v4` (line 26)
- `uses: issue-ops/semver@v2` (line 31)
- `uses: issue-ops/releaser@v2` (line 37)

Failing references in .github/workflows/continuous-integration.yml:
- `uses: actions/checkout@v4` (line 18)
- `uses: actions/setup-node@v4` (line 22)

Failing references in .github/workflows/linter.yml:
- `uses: actions/checkout@v4` (line 21)
- `uses: actions/setup-node@v4` (line 26)
- `uses: oxsecurity/megalinter/flavors/javascript@v8` (line 37)

All should be pinned to their full SHA, e.g. `uses: actions/checkout@11bd71901bbe5b1630ceea73d27597364c9af683 # v4`.

Locations:

- `.github/workflows/check-dist.yml:23`
- `.github/workflows/check-dist.yml:27`
- `.github/workflows/check-dist.yml:50`
- `.github/workflows/codeql.yml:30`
- `.github/workflows/codeql.yml:34`
- `.github/workflows/codeql.yml:39`
- `.github/workflows/codeql.yml:43`
- `.github/workflows/continuous-delivery.yml:26`
- `.github/workflows/continuous-delivery.yml:31`
- `.github/workflows/continuous-delivery.yml:37`
- `.github/workflows/continuous-integration.yml:18`
- `.github/workflows/continuous-integration.yml:22`
- `.github/workflows/linter.yml:21`
- `.github/workflows/linter.yml:26`
- `.github/workflows/linter.yml:37`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses

**Notes:**

Pinned all 15 unpinned `uses:` references across 5 workflow files to full SHA digests:
- actions/checkout@v4 → @11d5960a326750d5838078e36cf38b85af677262 (used in check-dist.yml, codeql.yml, continuous-delivery.yml, continuous-integration.yml, linter.yml)
- actions/setup-node@v4 → @49933ea5288caeca8642d1e84afbd3f7d6820020 (used in check-dist.yml, continuous-integration.yml, linter.yml)
- actions/upload-artifact@v4 → @ea165f8d65b6e75b540449e92b4886f43607fa02 (check-dist.yml)
- github/codeql-action/init@v3 → @4187e74d05793876e9989daffde9c3e66b4acd07 (codeql.yml)
- github/codeql-action/autobuild@v3 → @4187e74d05793876e9989daffde9c3e66b4acd07 (codeql.yml)
- github/codeql-action/analyze@v3 → @4187e74d05793876e9989daffde9c3e66b4acd07 (codeql.yml)
- issue-ops/semver@v2 → @5b8bb084b6834d03ddb5c7c96c683a588a2072ca (continuous-delivery.yml)
- issue-ops/releaser@v2 → @e6768024642153d17c157995e2684a3ebcae14e7 (continuous-delivery.yml)
- oxsecurity/megalinter/flavors/javascript@v8 → @e08c2b05e3dbc40af4c23f41172ef1e068a7d651 (linter.yml)
All original version tags preserved as inline comments.

