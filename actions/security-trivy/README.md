# `security-trivy` action

Migrated from
[numerique-gouv/action-trivy-cache](https://github.com/numerique-gouv/action-trivy-cache).

You can add this action to your workflow to scan your codebase for vulnerabilities using Trivy.

This action does not report the vulnerabilities to GitHub Security tab, but it can be used to fail the workflow
if any vulnerability is found. It's not recommended to make this check required in branch protection rules,
as it may block merges due to non-critical vulnerabilities.

```yaml
  security-trivy:
    permissions:
      contents: read
    runs-on: ubuntu-latest
    steps:
      - name: Run Trivy analysis for vulnerabilities
        uses: suitenumerique/ci/actions/security-trivy@main
```
