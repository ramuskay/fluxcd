# TO know when instancing the cluster

- GatewayAPI may not detect cilium ip pool, need to be restarted 

# Debug fluxcd

- Kustomization stuck : `flux reconcile kustomization <kustomization> --with-source`
- HelmRelease stuck : `flux reconcile helmrelease <release_name> --force`