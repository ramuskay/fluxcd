# TO know when instancing the cluster

- GatewayAPI may not detect cilium ip pool, need to be restarted 

# Debug fluxcd

- Kustomization stuck : `flux reconcile kustomization <kustomization> --with-source`
- Kustomization deleted : Push the yanl Kustomiation manifest with `kubectl apply -f <file>`
- HelmRelease stuck : `flux reconcile helmrelease <release_name> --force`