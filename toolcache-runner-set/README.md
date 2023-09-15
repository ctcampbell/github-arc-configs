Edit `values.yaml` accordingly (i.e. the volume mount hostPath if you are testing in a single node Kubernetes install) and then install in Helm like:

```
INSTALLATION_NAME="toolcache-runner-set"                                                                                         
NAMESPACE="arc-runners"
GITHUB_CONFIG_URL="https://github.com/<your org|enterprise|repo>"
GITHUB_PAT="<your pat>"
helm upgrade "${INSTALLATION_NAME}" \
    --namespace "${NAMESPACE}" \
    --create-namespace \
    --set githubConfigUrl="${GITHUB_CONFIG_URL}" \
    --set githubConfigSecret.github_token="${GITHUB_PAT}" \
    -f values.yaml \
    oci://ghcr.io/actions/actions-runner-controller-charts/gha-runner-scale-set
```
