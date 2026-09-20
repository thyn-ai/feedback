# Governance

This document describes how decisions are made for `thyn-ai/feedback`, the
public issue intake for the open-source tooling around Algenta and for the
Codna GitHub App. It is intentionally lightweight and will evolve as the
contributor community grows.

## Roles

- **Reporters and contributors** — anyone who files a report, takes part in
  a discussion, or opens a pull request.
- **Maintainers** — people with triage and merge authority on this
  repository. The project currently has a single maintainer: the `thyn-ai`
  organization owner (see [CODEOWNERS](./.github/CODEOWNERS)), who also
  holds final decision authority on all matters not explicitly delegated.

## Triage authority

Maintainers own the labels. In particular, `codna-fix` and `codna-secure`
hand a report to Codna's automated pipelines and are applied only by a
maintainer, after reading the report — never automatically, and never by a
reporter. The label set itself (`product:<name>`, the triage states) changes
by pull request or by a maintainer, announced in an issue.

## Decision-making

Changes to this repository — templates, documents, workflows — are made by
**lazy consensus**:

1. Propose the change as a GitHub issue or pull request.
2. Maintainers and contributors discuss in the open.
3. If no maintainer objects within 72 hours (three business days), the
   proposal is considered accepted and may proceed.

Maintainers may fast-track obvious, low-risk changes (typo fixes, CI repairs,
dependency security bumps) without waiting out the window. Any maintainer may
pause lazy consensus by raising an objection, in which case the change waits
until the objection is resolved in discussion. Where consensus cannot be
reached, the organization owner makes the final call.

Changes to the issue forms' field ids or product list also need a matching
change in the Codna CLI, which mirrors them (see
[CONTRIBUTING.md](./CONTRIBUTING.md#templates-are-a-contract)); those land
together or not at all.

## Becoming a maintainer

External contributors can become maintainers. The path:

1. **Sustained contribution** — a track record of careful triage, useful
   reports, reviews, and merged pull requests over several months.
2. **Nomination** — an existing maintainer nominates the contributor, citing
   specific contributions, in a GitHub discussion visible to all maintainers.
3. **Lazy consensus** — if no maintainer objects within 14 days, the
   nomination carries. The organization owner confirms and grants access.

Maintainers are expected to triage reports, review pull requests, uphold the
[Code of Conduct](./CODE_OF_CONDUCT.md), follow the
[security policy](./SECURITY.md), and keep CI green on `main`. Maintainers
who become inactive for more than a year may be moved to emeritus status by
the organization owner; emeritus maintainers can regain access on request.

## Releases

There are none. This repository ships no code and publishes no packages; a
change takes effect when it is merged to `main`.

## Changing this document

Amendments to this file follow the same lazy-consensus process as any other
change, with one difference: the review window is 14 days, and the
organization owner must approve the merged pull request.
