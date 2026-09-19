# Contributing to thyn-ai/feedback

Thank you for taking the time to report something. This repository is the
public front door for feedback about every thyn-ai product — **Algenta**,
**Codna**, **Telys**, **Sqai**, the **accounts portal**, and the docs. It
holds issue templates, community documents, and the automation around them,
and nothing else: there is no code to build here, and the most valuable
contribution is a report a maintainer can act on.

The products live in their own repositories. Some are public and Apache-2.0
([algenta-sdk](https://github.com/thyn-ai/algenta-sdk),
[algenta-integrations](https://github.com/thyn-ai/algenta-integrations),
[mojo-kernels](https://github.com/thyn-ai/mojo-kernels),
[security-toolchain](https://github.com/thyn-ai/security-toolchain)); the
Algenta engine, Codna, Telys, Sqai, and the accounts portal are proprietary
and their source is not public. Reports about any of them are welcome here
regardless — that is the point of this repository.

## Filing good feedback

### Pick the template that matches

| Template | Use it for | Labels it applies |
| --- | --- | --- |
| [Bug report](https://github.com/thyn-ai/feedback/issues/new?template=bug_report.yml) | Something does not work the way it is documented | `needs-triage` |
| [Feature request](https://github.com/thyn-ai/feedback/issues/new?template=feature_request.yml) | A capability that does not exist today | `enhancement`, `needs-triage` |
| [Question](https://github.com/thyn-ai/feedback/issues/new?template=question.yml) | A usage question with a concrete answer | `question`, `needs-triage` |

Blank issues are disabled on purpose: the templates are what make a report
routable (the product dropdown) and, for bugs, what an automated fixer reads.
For open-ended discussion, ideas, and show-and-tell, use
[Discussions](https://github.com/thyn-ai/feedback/discussions) instead.

### What a report a maintainer can act on looks like

- **One product per report.** Pick it in the dropdown. If a problem spans two
  products, file two reports and cross-link them.
- **The version.** `codna --version`, the SDK or package version, or the date
  you last used a hosted product.
- **The platform.** OS and architecture (`macOS 15 arm64`, `Ubuntu 24.04 in a
  GitHub Actions runner`), and the framework version for an integration.
- **What happened and what you expected instead.** Be concrete; this is the
  first thing both a maintainer and a fixing agent read.
- **The exact steps or code that reproduce it**, in order, and the error text
  as it was printed.
- **No secrets.** This repository is public. Strip tokens, keys, account
  identifiers, and customer data from logs before pasting them.
- **Search first.** Someone may have reported it already; add to that issue
  rather than opening a duplicate.

### Security vulnerabilities do not belong here

A public issue is a public disclosure. Follow [SECURITY.md](./SECURITY.md):
the public repositories each have their own `SECURITY.md`, and for the
proprietary products this repository's private **Report a vulnerability** tab
or `security@algenta.ai` is the channel.

## The other doors: CLI, MCP, and scripts

Every path files the same shape of issue, so a report from an agent and a
report from a browser land in the same place and are triaged the same way.

### `codna report`

```bash
codna report "short title of the problem" --product codna
codna report "short title" --product algenta --body "what happened" --attach-diagnostics
codna report "short title" --dry-run   # print exactly what would be sent; submit nothing
```

- `--product` is one of `algenta`, `codna`, `telys`, `sqai`, `accounts`,
  `docs` (default `codna`). Omit `--body` at a terminal and you are prompted
  for the description; scripts and agents are never prompted.
- The issue body mirrors the bug-report form's fields — *Which product?*,
  *Version* (the codna version), *Platform* (OS and Python version), *What
  happened?* — so a human reading it sees the same structure whichever door
  it came through.
- `--attach-diagnostics` adds one more section containing exactly what
  `codna doctor --json` prints: the presence and source of configuration,
  never a secret value. Nothing is attached unless you ask.
- The issue is filed **as you**, with `GITHUB_TOKEN`/`GH_TOKEN` or an
  already-logged-in `gh` CLI — never with the Codna App's credentials. With no
  token, no network, or an air-gapped machine, the command does not fail: it
  saves the report under `~/.codna/reports/` (or `$CODNA_RUNTIME_ROOT/reports/`)
  and prints a pre-filled `issues/new` link for you to submit.

### The `codna_report_bug` MCP tool

If an agent is connected to `codna mcp`, it can call `codna_report_bug` with
`title`, `body`, `product`, and `include_diagnostics`. It is the same
submission path as `codna report` and the only write tool the server exposes;
it returns `{"submitted": true|false, "url": ..., "local_path": ...}` and
falls back to the pre-filled link the same way.

### Scripts

The templates are plain [GitHub issue forms](https://docs.github.com/en/communities/using-templates-to-encourage-useful-issues-and-pull-requests/syntax-for-issue-forms),
so `gh issue create --repo thyn-ai/feedback --template bug_report.yml` and
the REST API both work.

One consequence of filing through the API: GitHub lets only repository
collaborators set labels when creating an issue, so a report filed by
`codna report` or the MCP tool arrives without the template's `needs-triage`
label. Maintainers triage unlabeled issues exactly the same way.

## What happens after you file

Triage happens through labels. You cannot apply them yourself, and you do not
need to.

| Label | Meaning |
| --- | --- |
| `needs-triage` | Applied by the template. A maintainer has not looked yet. Removed at triage. |
| `product:<name>` | Which product the report is about — `algenta`, `codna`, `telys`, `sqai`, `accounts`, or `docs`, from the dropdown. This is the label that routes the report: an approved fix is dispatched to that product's repository. |
| `bug`, `enhancement`, `question`, `documentation` | The kind of report, once confirmed. |
| `codna-fix` | **Maintainers only.** The report is approved for Codna's automated fix pipeline. Codna reads the `product:<name>` label, opens a verified fix PR in that product's own repository, and comments the outcome — the PR link, or the reason it could not — back on your report here. This is a deliberate human-in-the-loop step; it never fires on its own. |
| `codna-secure` | **Maintainers only.** The report is approved for Codna's security-reachability pass. |
| `duplicate`, `invalid`, `wontfix` | Closed with the reason in the label; a maintainer will say why in a comment. |
| `good first issue`, `help wanted` | Open for anyone to pick up, in the product's repository. |
| `stale`, `pinned`, `security` | Housekeeping. A report with no activity for 60 days is marked `stale` and closed 14 days later unless someone comments; `pinned`, `security`, `good first issue`, `codna-fix`, and `codna-secure` are exempt. |

Please do not ping maintainers to apply `codna-fix`; every report is read.

## Contributing to this repository itself

Pull requests here change the intake, not the products. Welcome changes:
clearer template wording, a missing product in the dropdown, better
documents, and workflow maintenance.

### Templates are a contract

`codna report` and `codna_report_bug` build their issue body from
`bug_report.yml`'s fields, and the offline fallback pre-fills the form by
field id (`template=bug_report.yml`, `what-happened`). Adding a field is
fine; renaming or removing one, or changing the product list, must be
coordinated with the Codna CLI — please open an issue first so it can be
done together.

### Workflows

- Every `uses:` is pinned to a full 40-character commit SHA with a
  `# vX.Y.Z` comment. Dependabot bumps them weekly, grouped.
- The top-level `permissions:` block is `contents: read`; a job that needs
  more declares it on the job. No `${{ }}` expressions inside `run:` steps.
- `.github/workflows/security.yml` and the toolchain block in
  `.pre-commit-config.yaml` are managed by
  [thyn-ai/security-toolchain](https://github.com/thyn-ai/security-toolchain)'s
  propagate step, which moves both pins together. Do not bump them by hand.
- `actionlint` must be clean and every YAML file must parse. The
  pre-commit hooks in `.pre-commit-config.yaml` run both:

  ```bash
  uv tool install pre-commit   # or: pipx install pre-commit
  pre-commit install           # installs the pre-commit and pre-push hooks
  pre-commit run --all-files
  ```

### Commits and pull requests

We follow [Conventional Commits](https://www.conventionalcommits.org/):

```
docs(templates): ask for the framework version in bug reports
ci(stale): exempt codna-secure from stale automation
```

The pull request template has the checklist. CI runs on forked-repository
pull requests with no secrets and no elevated permissions, so it is safe to
run automatically on every PR.

## Licensing

By submitting a pull request you agree that your contribution is licensed
under the project's [Apache-2.0 license](./LICENSE) (inbound=outbound,
[GitHub Terms of Service §D.6](https://docs.github.com/en/site-policy/github-terms/github-terms-of-service#6-contributions-under-repository-license)).

## Code of conduct

Everyone participating here — in issues, discussions, and pull requests — is
expected to follow the [Code of Conduct](./CODE_OF_CONDUCT.md).

## Community

- Discussions: https://github.com/thyn-ai/feedback/discussions
- Discord: https://discord.gg/w8NDsph9an
- Docs: https://docs.algenta.ai
- Email: community@algenta.ai
