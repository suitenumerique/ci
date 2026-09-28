# `trivy-cache` action

Builds a Docker image and scans it with Trivy for HIGH and CRITICAL
vulnerabilities, failing on detection. The Trivy database is cached for the day
to speed up subsequent scans.

Migrated from
[numerique-gouv/action-trivy-cache](https://github.com/numerique-gouv/action-trivy-cache)
(root action).

```yaml
      - name: Run trivy scan
        uses: suitenumerique/ci/actions/trivy-cache@main
        with:
          docker-build-args: "--target backend-production -f Dockerfile"
          docker-image-name: "docker.io/lasuite/meet-backend:${{ github.sha }}"
          docker-context: "."              # optional, defaults to "."
          trivyignores: ./.github/.trivyignore  # optional
```
