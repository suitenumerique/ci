# `security-trivy-critical` action

Migrated from
[numerique-gouv/action-trivy-cache](https://github.com/numerique-gouv/action-trivy-cache).

You can add this action to your workflow to scan your codebase for critical vulnerabilities using Trivy.

```yaml
  security-trivy-critical:
    permissions:
      contents: read
      security-events: write
    runs-on: ubuntu-latest
    steps:
      - name: Run Trivy analysis for critical vulnerabilities
        uses: suitenumerique/ci/actions/security-trivy-critical@main
```

This check will scan your repository for vulnerabilities and report any critical issues
found in the Security tab of your GitHub repository.

This action will never fail the workflow, it will only report the vulnerabilities found.

You can then add the "GitHub Advanced Security / Trivy" to the required checks for your branches
in the branch protection rules to ensure that no critical vulnerabilities are introduced
in your codebase.
