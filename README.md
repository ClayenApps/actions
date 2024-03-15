# actions
Reusable GitHub Actions workflows.

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
