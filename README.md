# ci

Shared GitHub Actions workflows, actions and Renovate preset for La Suite projects.

## Usage

```yaml
jobs:
  changelog:
    uses: suitenumerique/ci/.github/workflows/_changelog.yml@main

  build:
    steps:
      - uses: suitenumerique/ci/actions/mail-templates@main
```

Each workflow documents its inputs; each action has its own README.

## Content

- [`.github/workflows/`](.github/workflows): reusable workflows, prefixed with `_`
- [`actions/`](actions): composite actions
- [`renovate/`](renovate): Renovate preset, `github>suitenumerique/ci//renovate/default`
