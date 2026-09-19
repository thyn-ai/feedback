## What does this change?

<!-- One or two sentences. Pull requests here change the intake -- the templates, the
     documents, the automation -- not the products; a product change goes to the
     repository that owns the code. -->

## Checklist

- [ ] Every YAML file I touched still parses, and the issue forms still render
- [ ] I did not rename or remove an issue-form field id or change the product list
      without a linked issue — `codna report` and the `codna_report_bug` MCP tool
      mirror `bug_report.yml` (see CONTRIBUTING.md)
- [ ] Workflow changes: every `uses:` pinned to a full commit SHA with a `# vX.Y.Z`
      comment, top-level `permissions: contents: read`, `actionlint` clean
- [ ] `.github/workflows/security.yml` and the toolchain block in
      `.pre-commit-config.yaml` are untouched — thyn-ai/security-toolchain manages
      those pins
- [ ] No hardcoded credentials or secrets
- [ ] I agree my contribution is licensed under the project's Apache-2.0
      license (inbound=outbound, GitHub Terms of Service §D.6)
