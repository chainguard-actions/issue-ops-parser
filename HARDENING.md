<!-- markdownlint-disable -->

# Hardening Report: issue-ops--parser/v3.0.0

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **issue-ops--parser/v3.0.0** was hardened automatically. 1 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

All workflow files reference GitHub Actions using mutable version tags instead of pinned full 40-character SHA commit hashes. This exposes the workflows to supply-chain attacks where a tag could be silently moved to point to malicious code. Failing references include: check-dist.yml: actions/checkout@v4, actions/setup-node@v4, actions/upload-artifact@v4; codeql.yml: actions/checkout@v4, github/codeql-action/init@v3, github/codeql-action/autobuild@v3, github/codeql-action/analyze@v3; continuous-delivery.yml: actions/checkout@v4, issue-ops/semver@v2, issue-ops/releaser@v2; continuous-integration.yml: actions/checkout@v4, actions/setup-node@v4; linter.yml: actions/checkout@v4, actions/setup-node@v4, oxsecurity/megalinter/flavors/javascript@v7.

Locations:

- `.github/workflows/check-dist.yml:19`
- `.github/workflows/check-dist.yml:25`
- `.github/workflows/check-dist.yml:44`
- `.github/workflows/codeql.yml:22`
- `.github/workflows/codeql.yml:27`
- `.github/workflows/codeql.yml:32`
- `.github/workflows/codeql.yml:37`
- `.github/workflows/continuous-delivery.yml:22`
- `.github/workflows/continuous-delivery.yml:27`
- `.github/workflows/continuous-delivery.yml:33`
- `.github/workflows/continuous-integration.yml:17`
- `.github/workflows/continuous-integration.yml:23`
- `.github/workflows/linter.yml:20`
- `.github/workflows/linter.yml:26`
- `.github/workflows/linter.yml:35`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses

**Notes:**

Pinned all 15 unpinned action references across 5 workflow files to full 40-character SHA commit hashes:

- check-dist.yml: actions/checkout@v4 → @34e114876b0b11c390a56381ad16ebd13914f8d5, actions/setup-node@v4 → @49933ea5288caeca8642d1e84afbd3f7d6820020, actions/upload-artifact@v4 → @ea165f8d65b6e75b540449e92b4886f43607fa02
- codeql.yml: actions/checkout@v4 → @34e114876b0b11c390a56381ad16ebd13914f8d5, github/codeql-action/init@v3 → @b7351df727350dca84cb9d725d57dcf5bc82ba26, github/codeql-action/autobuild@v3 → @b7351df727350dca84cb9d725d57dcf5bc82ba26, github/codeql-action/analyze@v3 → @b7351df727350dca84cb9d725d57dcf5bc82ba26
- continuous-delivery.yml: actions/checkout@v4 → @34e114876b0b11c390a56381ad16ebd13914f8d5, issue-ops/semver@v2 → @5b8bb084b6834d03ddb5c7c96c683a588a2072ca, issue-ops/releaser@v2 → @e6768024642153d17c157995e2684a3ebcae14e7
- continuous-integration.yml: actions/checkout@v4 → @34e114876b0b11c390a56381ad16ebd13914f8d5, actions/setup-node@v4 → @49933ea5288caeca8642d1e84afbd3f7d6820020
- linter.yml: actions/checkout@v4 → @34e114876b0b11c390a56381ad16ebd13914f8d5, actions/setup-node@v4 → @49933ea5288caeca8642d1e84afbd3f7d6820020, oxsecurity/megalinter/flavors/javascript@v7 → @bacb5f8674e3730b904ca4d20c8bd477bc51b1a7

All original version tags are preserved as inline comments (e.g., # v4) for readability.

