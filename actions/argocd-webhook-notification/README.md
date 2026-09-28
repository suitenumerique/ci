# `argocd-webhook-notification` action

Notifies Argo CD that the deployment repository changed, by sending it a signed
GitHub `push` webhook, so it syncs right away instead of waiting for its next poll.

Migrated from
[numerique-gouv/action-argocd-webhook-notification](https://github.com/numerique-gouv/action-argocd-webhook-notification).

```yaml
  notify-argocd:
    runs-on: ubuntu-latest
    needs: build-and-push
    if: github.event_name != 'pull_request'
    steps:
      - name: Notify Argo CD
        uses: suitenumerique/ci/actions/argocd-webhook-notification@main
        with:
          deployment_repo_path: "${{ secrets.DEPLOYMENT_REPO_URL }}"
          argocd_webhook_secret: "${{ secrets.ARGOCD_PREPROD_WEBHOOK_SECRET }}"
          argocd_url: "${{ vars.ARGOCD_PREPROD_WEBHOOK_URL }}"
```

## Inputs

| Name                    | Description                                                              |
|-------------------------|--------------------------------------------------------------------------|
| `deployment_repo_path`  | Path of the deployment repository watched by Argo CD, e.g. `org/repo`    |
| `argocd_webhook_secret` | Webhook secret, the value of `webhook.github.secret` in the Argo CD chart |
| `argocd_url`            | Base URL of Argo CD; the webhook is sent to `<argocd_url>/api/webhook`   |
