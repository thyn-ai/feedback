<div align="center">

# thyn-ai feedback

**Public issue intake for the Algenta family and the Codna GitHub App — one place to report a bug, request a feature, or ask a question about any thyn-ai product.**

[![CodeQL](https://github.com/thyn-ai/feedback/actions/workflows/codeql.yml/badge.svg)](https://github.com/thyn-ai/feedback/actions/workflows/codeql.yml)
[![OpenSSF Scorecard](https://api.scorecard.dev/projects/github.com/thyn-ai/feedback/badge)](https://scorecard.dev/viewer/?uri=github.com/thyn-ai/feedback)
[![License: Apache-2.0](https://img.shields.io/badge/license-Apache--2.0-blue.svg)](./LICENSE)

[Report a bug](../../issues/new?template=bug_report.yml) · [Request a feature](../../issues/new?template=feature_request.yml) · [Ask a question](../../issues/new?template=question.yml) · [Discussions](../../discussions) · [Contributing](./CONTRIBUTING.md) · [Support](./SUPPORT.md) · [Security](./SECURITY.md)

</div>

---

One place to report a bug, request a feature, or ask a question about any thyn-ai product:
**Algenta**, **Codna**, **Telys**, **Sqai**, or the accounts portal.

This repo holds only issues — there's no code here. Product source lives in each product's own
repo (some private); this is the public front door regardless of where the code lives.

## What belongs here — and what does not

**Belongs here**

- Bug reports, feature requests, and usage questions about any thyn-ai product — Algenta (the
  engine, the SDKs, the framework integrations, mojo-kernels), Codna (the GitHub App, the CLI, the
  MCP server), Telys, Sqai, the accounts portal, and the docs — whether or not that product's
  source is public.
- Reports filed for you by `codna report` or the `codna_report_bug` MCP tool. They land here as
  ordinary issues.
- Open-ended discussion, ideas, and show-and-tell, in [Discussions](../../discussions).

**Does not belong here**

- **Security vulnerabilities.** A public issue is a public disclosure. Report privately — see
  [SECURITY.md](./SECURITY.md) for the right channel for each product.
- **Code changes to a product.** Pull requests go to the repository that owns the code (see
  [Related repositories](#related-repositories)). Pull requests here are for the templates, the
  documents, and the automation in this repository itself — see
  [CONTRIBUTING.md](./CONTRIBUTING.md).
- **Account, billing, or license details.** Anything specific to your account is faster and safer
  through the [accounts portal](https://accounts.thyn.ai/account) than in a public issue.

## Reporting a bug

Pick whichever is easiest:

- **In your browser** — [open a bug report](../../issues/new?template=bug_report.yml). Pick the
  product from the dropdown; that's what routes it.
- **From the terminal** — if you have `codna` installed:
  ```bash
  codna report "short title of the problem" --product codna
  ```
  This fills in your version and platform automatically. Add `--attach-diagnostics` to include a
  redacted `codna doctor` snapshot. No GitHub account handy? It prints a pre-filled link instead of
  failing.
- **From an AI agent** — codna's MCP server exposes a `codna_report_bug` tool with the same fields
  as the CLI. If your agent is connected to `codna mcp`, it can already file here.
- **From a script** — the templates are plain [GitHub issue forms](https://docs.github.com/en/communities/using-templates-to-encourage-useful-issues-and-pull-requests/syntax-for-issue-forms),
  so `gh issue create --repo thyn-ai/feedback --template bug_report.yml` or the REST API works too.

## What happens after you file

The product you picked in the dropdown gets applied as a `product:<name>` label automatically —
that's what routes it. A maintainer triages every report from there. For eligible bugs, Codna's
own automated fixer can pick it up and open a verified fix PR in the right repo — the same
pipeline that fixes issues inside our own projects, pointed at whatever you reported. That's a
deliberate human-in-the-loop step (a maintainer applies one label to trigger it), not something
that fires on every issue automatically.

The labels involved — `needs-triage`, `product:<name>`, `codna-fix`, `codna-secure` — are
described in [CONTRIBUTING.md](./CONTRIBUTING.md#what-happens-after-you-file).

## Security vulnerabilities

**Don't file those here.** A public issue is a public disclosure. [SECURITY.md](./SECURITY.md)
lists the right private channel for every product: the open-source repositories' own
`SECURITY.md` files, and this repository's **Security → Report a vulnerability** tab or
`security@algenta.ai` for the proprietary ones.

## Suggestions

Feature requests get their own template and are read the same way bug reports are — they just
don't carry an automated fix path.

## Related repositories

Open-source repositories from the Algenta team. The Algenta engine itself is proprietary; everything listed here is Apache-2.0. Issues and discussions are welcome in whichever repository owns the code.

- [thyn-ai/algenta-sdk](https://github.com/thyn-ai/algenta-sdk) — Python & TypeScript SDKs for the Algenta decision engine: governed tool profiles, execution receipts, approvals.
- [thyn-ai/algenta-integrations](https://github.com/thyn-ai/algenta-integrations) — Framework integrations for Algenta: LangChain, LlamaIndex, pydantic-ai, MAF, Haystack, LiteLLM, Ray Serve, vLLM, Vercel AI SDK and n8n.
- [thyn-ai/mojo-kernels](https://github.com/thyn-ai/mojo-kernels) — Clean-room Mojo kernels as drop-in accelerators for popular Python/TypeScript libraries, with bit-exact parity and pure-language fallbacks.
- [thyn-ai/security-toolchain](https://github.com/thyn-ai/security-toolchain) — The pinned, checksum-verified security toolchain (Gitleaks, Opengrep, OSV-Scanner, Trivy config, actionlint) that every thyn-ai repository runs locally and in CI.
- [thyn-ai/feedback](https://github.com/thyn-ai/feedback) (this repository) — Public issue intake for the Algenta family and the Codna GitHub App.

## License

Apache-2.0 — see [LICENSE](./LICENSE) and [NOTICE](./NOTICE). This repository contains templates,
documents, and automation only; the products it takes reports for are separate software under
their own licenses and are not contained in this repository.
