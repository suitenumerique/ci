# `mail-templates` action

Provides the Django mail templates generated from MJML to the current job.

The templates are restored from the cache when the MJML sources haven't changed.
Otherwise they are built (Node.js 22, with yarn or npm depending on the lockfile)
and cached for the next jobs and runs. The cache key is a hash of every file in
the MJML project, so any change to a template, a build script or a dependency
triggers a rebuild.

```yaml
  test-back:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout repository
        uses: actions/checkout@...

      - name: Build or restore the mail templates
        uses: suitenumerique/ci/actions/mail-templates@main
```

The action must run after the checkout, as it reads the MJML sources.

## Inputs

| Name               | Default                           | Description                                 |
|--------------------|-----------------------------------|---------------------------------------------|
| `mail_directory`   | `src/mail`                        | Directory of the MJML project               |
| `output_directory` | `src/backend/core/templates/mail` | Where the build writes the Django templates |
