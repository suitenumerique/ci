# `free-disk-space` action

Frees disk space on GitHub-hosted Linux runners, for jobs that run out of space
(large Docker builds, multi-platform images, big test suites).

It removes large preinstalled toolchains the La Suite projects don't use
(.NET, Haskell/GHC, Android SDK) and prunes all Docker images, containers and
volumes. Disk usage is printed before and after the cleanup.

```yaml
  build:
    runs-on: ubuntu-latest
    steps:
      - name: Free disk space
        uses: suitenumerique/ci/actions/free-disk-space@main

      - name: Checkout repository
        uses: actions/checkout@...
```

Run it at the start of the job: the Docker prune removes every image on the
runner, including ones pulled or built earlier in the same job.

The action has no inputs. It does nothing on non-Linux runners, and each cleanup
step is allowed to fail, so it never breaks the job.
