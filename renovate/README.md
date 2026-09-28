# Renovate configuration

Shared [Renovate](https://docs.renovatebot.com/) preset for La Suite projects,
migrated from
[numerique-gouv/renovate-configuration](https://github.com/numerique-gouv/renovate-configuration).

Renovate lets you define [presets](https://docs.renovatebot.com/config-presets/)
and extend them in another configuration.

## Usage

Create a `renovate.json` file at the root of your repository with this content:

```json
{
  "extends": [
    "github>suitenumerique/ci//renovate/default"
  ]
}
```

To pin the preset to a release of this repository, append the tag:
`github>suitenumerique/ci//renovate/default#v1`.

If you need to extend or override this preset, do it in your own config file as
explained in the [preset documentation](https://docs.renovatebot.com/config-presets/).
