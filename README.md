# Flux CD Deploy

## TO know when instancing the cluster

- GatewayAPI may not detect cilium ip pool, need to be restarted 

## Debug fluxcd

- Kustomization stuck : `flux reconcile kustomization <kustomization> --with-source`
- Kustomization deleted : Push the yanl Kustomiation manifest with `kubectl apply -f <file>`
- HelmRelease stuck : `flux reconcile helmrelease <release_name> --force`

## Problem

- Repair PXE which is broken
  - Cilium LB IP taking precedence over real flatcar IP and messed up the kube exposed IP. Need to tweak the k3s config
- Blackbox not working
- When one node is off pods are not rescheduling correctly
  - See that : https://longhorn.github.io/longhorn-tests/manual/pre-release/node/improve-node-failure-handling/
  - See that also : https://www.medik8s.io
- Too much resources used !!
  - Explore Prometheus optim
    - Check to switch to Victoria metrics only
    - Scrape from 30 to 120s seems to mitigate a bit but to see on a longer period
    - Test retention from 30d to 7d
  - Check k3s-server proc seems to take 10% of the RAM on each node (test loading server without workload)

## Problem Solved

- Secret always in flux-system ?
  - Is ok for now but we should think if it's ok in a security pov
- Secret change must reload the helm release
  - Thx to the label reconcile.fluxcd.io/watch: Enabled (see here: https://github.com/fluxcd/flux2/issues/5446)
- Pushover notif for flux helmrelease
  - Alertmanager is the wayyy
- Certif wildcard not working with internal
  - http redirect routes have been created
  - Annotation has been added on them to avoid gatus fetching them
  - Needs to have all other routes bind **only** to https

## Print

https://print.deskpi.com/models/70