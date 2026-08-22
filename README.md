# thyn-ai feedback

One place to report a bug, request a feature, or ask a question about any thyn-ai product:
**Algenta**, **Codna**, **Telys**, **Sqai**, or the accounts portal.

This repo holds only issues — there's no code here. Product source lives in each product's own
repo (some private); this is the public front door regardless of where the code lives.

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

A maintainer triages every report. For eligible bugs, Codna's own automated fixer can pick it up
and open a verified fix PR in the right repo — the same pipeline that fixes issues inside our own
projects, pointed at whatever you reported. That's a deliberate human-in-the-loop step, not
something that fires on every issue automatically.

## Security vulnerabilities

**Don't file those here.** Use the security contact link when opening a new issue, or go straight
to the affected product's `SECURITY.md` ([codna](https://github.com/thyn-ai/codna/security/policy)).

## Suggestions

Feature requests get their own template and are read the same way bug reports are — they just
don't carry an automated fix path.
