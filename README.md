# actions
Reusable GitHub Actions workflows.

## Docker GHCR

Build and push Docker Image to the
[GitHub Container Registry]([https://](https://github.blog/2020-09-01-introducing-github-container-registry/)).

```yml
// ...
jobs:
  myService:
    name: Build and push
    uses: ClayenApps/actions/.github/workflows/docker-ghcr.yml@main
    with:
      service: 'myService' # Optional
```

## Portainer Redeploy

Calls Portainer instance to redeploy stack via git.

```yml
// ...
jobs:
  portainer:
    name: Deploy to Portainer
    uses: ClayenApps/actions/.github/workflows/portainer-redeploy.yml@main
    with:
      apiUrl: 'https://example.com/portainer/api'
      serviceId: ${{ vars.PORTAINER_SERVICE_ID }}
      endpointId: ${{ vars.PORTAINER_ENDPOINT_ID }}
    secrets:
      token: ${{ secrets.PORTAINER_TOKEN }}
```

## Portainer Update

Calls Portainer instance to update stack via compose file.

```yml
// ...
jobs:
  portainer:
    name: Deploy to Portainer
    uses: ClayenApps/actions/.github/workflows/portainer-update.yml@main
    with:
      apiUrl: 'https://example.com/portainer/api'
      serviceId: ${{ vars.PORTAINER_SERVICE_ID }}
      endpointId: ${{ vars.PORTAINER_ENDPOINT_ID }}
      composePath: my-compose-file.yml # Optional
    secrets:
      token: ${{ secrets.PORTAINER_TOKEN }}
```

## Telegram Notify

Send Telegram message to notify about completed workflow.

Message includes links to the repository and workflow run pages.

> [!NOTE]
>
> Characters `_`, `*`, `[`, `]`, `(`, `)`, `~`, ``` ` ```, `>`, `#`, `+`, `-`, `=`, `|`, `{`, `}`,
> `.`, `!` must be escaped with the preceding backslash (`\\` in yaml).
>
> [Bot API documentation](https://core.telegram.org/bots/api#markdownv2-style)

```yml
// ...
jobs:
  notify:
    name: Send Telegram report
    if: ${{ always() }}
    uses: ClayenApps/actions/.github/workflows/telegram-notify.yml@main
    with:
      message: |
        *${{ github.repository }}*
        Project deployed successfully\\.
      additional_buttons: '[{ "text": "Click me!", "url": "https://www.youtube.com/watch?v=dQw4w9WgXcQ" }]' # Optional
    secrets:
      chat_id: ${{ secrets.TELEGRAM_CHAT }}
      token: ${{ secrets.TELEGRAM_TOKEN }}
```
