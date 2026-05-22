# MCA-NITW/.github

Organization-level configuration for [MCA-NITW](https://github.com/MCA-NITW).

## What's in here

| Path | Purpose |
|------|---------|
| `profile/README.md` | Org profile shown on github.com/MCA-NITW |
| `.github/workflows/auto-invite.yml` | Automated member invitations via issue form |
| `.github/workflows/label-management.yml` | Creates/syncs org-wide issue labels |
| `.github/workflows/node-ci.yml` | Reusable CI: install + lint + build + test (pnpm/npm/yarn) |
| `.github/workflows/format-check.yml` | Reusable: Prettier --check |
| `.github/workflows/security-scan.yml` | Reusable: Trivy + Dependency Review |
| `.github/workflows/markdown-check.yml` | Reusable: markdownlint + dead-link check |
| `.github/ISSUE_TEMPLATE/` | Join-request form |
| `.github/CONTRIBUTING.md` | Inherited by all repos without their own |
| `.github/SECURITY.md` | Inherited security policy |
| `.github/CODE_OF_CONDUCT.md` | Inherited code of conduct |
| `.github/PULL_REQUEST_TEMPLATE.md` | Inherited PR checklist |
| `.github/dependabot.yml` | Keeps our reusable workflow actions up to date |
| `renovate.json` | Shared Renovate preset (repos extend via `"extends": ["github>mca-nitw/.github"]`) |
| `INVITATION_SYSTEM.md` | Docs for the auto-invite workflow |

## For admins

- **Add a new reusable workflow:** create it in `.github/workflows/`, use `on: workflow_call`.
- **Update Renovate config for all repos:** edit `renovate.json` here — all repos inherit.
- **Approve a join request manually:** comment `/approve` on the issue.

## For consumer repos

Replace your per-repo CI with a thin caller:

```yaml
# .github/workflows/ci.yml
name: CI
on:
  push:
    branches: [main]
  pull_request:
    branches: [main]

jobs:
  build:
    uses: mca-nitw/.github/.github/workflows/node-ci.yml@main
  format:
    uses: mca-nitw/.github/.github/workflows/format-check.yml@main
  security:
    uses: mca-nitw/.github/.github/workflows/security-scan.yml@main
    permissions:
      contents: read
      security-events: write
```

And reduce `renovate.json` to:

```json
{ "extends": ["github>mca-nitw/.github"] }
```
