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

Calls Portainer instance to redeploy stack.

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
```
