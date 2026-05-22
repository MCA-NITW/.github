# Contributing to MCA-NITW

Thanks for taking the time to contribute! This file is auto-applied to every MCA-NITW repo that doesn't have its own `CONTRIBUTING.md`. Each repo may add a more specific guide on top of this baseline.

## Quick start

1. **Fork the repo** and clone your fork.
2. **Create a feature branch** from `main`: `git checkout -b feat/short-description`.
3. **Install dependencies** (most of our repos use `pnpm` — see the repo's README for stack-specific commands).
4. **Make your change** with a focused commit history.
5. **Push and open a PR** against `main`. Bots will run lint, build, and security scans automatically.

## Branch and commit conventions

- **Branch names:** `feat/...`, `fix/...`, `chore/...`, `docs/...`, `refactor/...`, `test/...`.
- **Commit messages:** Conventional Commits — `feat:`, `fix:`, `chore:`, etc. Keep the subject under 70 chars; use the body for context.
- **One PR per logical change.** Don't bundle a refactor with a feature in the same PR.
- **Never force-push to `main`.** Feature branches you own are fine to force-push (with `--force-with-lease`).

## What our CI checks

Every PR runs reusable workflows from `mca-nitw/.github`:

- **`node-ci`** — install / lint / build / test (auto-detects pnpm vs npm).
- **`format-check`** — Prettier formatting (`npx prettier --check .`).
- **`security-scan`** — Trivy filesystem scan + GitHub Dependency Review (fails on high-severity vulns).
- **CodeQL** (per repo where applicable) — static analysis.
- **SonarCloud** (per repo where configured) — quality gate.

## Renovate

Dependency updates are managed by **Renovate**:

- Non-major weekly updates are grouped and auto-merged when CI passes (Mondays at 03:00 IST).
- Security advisories trigger immediate PRs and bypass the weekly schedule.
- Major bumps require manual approval from the dependency dashboard.
- The shared config lives in `mca-nitw/.github/renovate.json5` — repos extend it via `"extends": ["github>mca-nitw/.github"]`.

## Reporting issues

- **Security vulnerabilities:** see [SECURITY.md](SECURITY.md). Do not open public issues for vulns.
- **Bugs / feature requests:** open an issue in the relevant repo with a clear repro or use-case.
- **Want to join the org?** Open a `[Join Request]` issue in [`mca-nitw/.github`](https://github.com/MCA-NITW/.github/issues/new/choose) — automated invites trigger from there.

## Code of Conduct

By participating you agree to our [CODE_OF_CONDUCT.md](CODE_OF_CONDUCT.md).
