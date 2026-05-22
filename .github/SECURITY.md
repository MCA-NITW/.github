# Security Policy

This policy applies to **all repositories under the [`mca-nitw`](https://github.com/MCA-NITW) organisation**. Individual repos may add a stricter `SECURITY.md` on top of this baseline.

## Reporting a vulnerability

**Please do not open a public issue for security problems.**

Instead, use one of:

1. **Private vulnerability reporting** on the affected repo — go to *Security → Report a vulnerability* (this is the preferred channel).
2. **Email** the org admins listed in the org profile.

Include:

- A description of the vulnerability and its impact.
- Steps to reproduce (proof of concept welcome).
- Affected versions / commit SHAs.
- Suggested fix if you have one.

We aim to acknowledge within **3 working days** and resolve / mitigate within **30 days** for critical issues.

## Scope

In scope:

- Source code in any public `mca-nitw/*` repo.
- Deployment configurations and infrastructure-as-code committed to those repos.
- The org's automation workflows under `mca-nitw/.github`.

Out of scope:

- Third-party dependencies (report upstream — we'll prioritise mitigations once disclosed).
- Social-engineering attacks against members.
- Volumetric DoS testing against any deployed app.

## Supported versions

The latest commit on `main` of each repo is supported. Older tags receive security fixes only on a best-effort basis.

## Recognition

We don't currently run a paid bug-bounty programme, but we're happy to credit reporters in release notes or PR descriptions on request.
