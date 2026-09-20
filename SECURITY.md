# Security Policy

This repository is the public issue intake for the open-source tooling
around Algenta and for the Codna GitHub App. It holds issue templates,
community documents, and the GitHub Actions workflows that maintain them —
no application code, no packages, no running service. We still take its
security seriously and appreciate responsible disclosure from the community.

## Supported versions

There are no releases here. Everything in this repository lives on `main`
and fixes land there directly.

| Channel | Supported |
| --- | --- |
| `main` | :white_check_mark: |

## Reporting a vulnerability

**Please do not open a public issue, pull request, or discussion for
security problems.** Public disclosure before a fix is available puts other
users at risk. That includes vulnerabilities in the products this repository
takes reports for: the issue forms are public, so a vulnerability filed
through them is a public disclosure, not a report.

Report privately through either channel:

1. **GitHub Security Advisories** (preferred) — open a private report from
   this repository's **Security → Report a vulnerability** tab.
2. **Email** — `security@algenta.ai`.

Please include, where possible: a description of the issue and its impact,
the affected file (which template, workflow, or document) or product and
version, and steps to reproduce or a proof of concept.

## What to expect

- Acknowledgement within 3 business days.
- An initial assessment and severity triage within 7 business days.
- Regular updates as we work on a fix, and credit in the published advisory
  (unless you prefer to remain anonymous).
- Coordinated disclosure: we agree on a timeline with you and publish a
  GitHub Security Advisory once a fix is available.

## Scope

**In scope** — this repository's own contents:

- The GitHub Actions workflows under `.github/workflows/`: a permission
  broader than the job needs, an action that is not pinned to a full commit
  SHA or whose pin does not match its version comment, or a way to make a
  workflow act on untrusted input
- The issue forms under `.github/ISSUE_TEMPLATE/` and their `config.yml`,
  for example a contact link that sends reporters somewhere they should not
  go
- The documents in this repository, where an error would lead a reporter to
  disclose privately-reportable information in public

**Vulnerabilities in the products belong with the products.** This
repository holds none of their code. Use the owning repository's policy for
the open-source products; for the proprietary ones, whose source is not
public, this repository's private channels above are the way in:

| Product | Where to report |
| --- | --- |
| Algenta SDK (Python and TypeScript) | [thyn-ai/algenta-sdk — SECURITY.md](https://github.com/thyn-ai/algenta-sdk/blob/main/SECURITY.md) |
| Algenta framework integrations | [thyn-ai/algenta-integrations — SECURITY.md](https://github.com/thyn-ai/algenta-integrations/blob/main/SECURITY.md) |
| mojo-kernels (`bm25-mojo`, `cclib-mojo`, `fuse-mojo`) | [thyn-ai/mojo-kernels — SECURITY.md](https://github.com/thyn-ai/mojo-kernels/blob/main/SECURITY.md) |
| security-toolchain | [thyn-ai/security-toolchain — SECURITY.md](https://github.com/thyn-ai/security-toolchain/blob/main/SECURITY.md) |
| The Algenta engine, Codna (GitHub App, CLI, MCP server), Telys, Sqai, the accounts portal | Privately, through this repository's **Security → Report a vulnerability** tab or `security@algenta.ai` |

**Also out of scope:** third-party dependencies (report those upstream; we
still want to hear how they affect Algenta), and social-engineering,
physical, or denial-of-service testing against any hosted environment.

Thank you for helping keep Algenta and its users safe.
