# Cert-Manager (Helm) - Managed by Argo CD

This folder contains the GitOps configuration for deploying `cert-manager` via the official Jetstack Helm chart.

## Helm Chart Source

- **Repository**: https://charts.jetstack.io
- **Chart**: `cert-manager`
- **Version**: `v1.18.1`

## Argo CD Application

Argo CD watches the `cert-manager.yaml` in the `cluster-infra/argocd/` directory and ensures the `cert-manager` chart is installed in the `cert-manager` namespace with CRDs.

Auto-sync is enabled for automatic reconciliation when the Git repo is updated.

## ClusterIssuer

ClusterIssuer is created via Kustomize in `base/issuer-cluster.yaml`.

```yaml
spec:
  acme:
    email: suyash@4gd.ai
    server: https://acme-v02.api.letsencrypt.org/directory
    privateKeySecretRef:
      name: letsencrypt-prod-private-key
    solvers:
      - http01:
          ingress:
            class: haproxy

