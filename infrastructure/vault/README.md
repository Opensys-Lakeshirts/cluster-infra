# Vault GitOps Setup (Flux CD)

This directory manages the production-ready deployment of HashiCorp Vault using Flux CD and Helm.

## Structure

- **argocd/vault.yaml**: Argo CD/Flux  manifest pointing to the official Vault Helm chart.
- **Helm Chart Source**: https://helm.releases.hashicorp.com
- **Chart Version**: 0.30.1
- **Vault Version**: 1.20.1

## Configuration

The Vault setup is:
- Highly Available (HA) using Raft
- Persistent with local-path storage (8Gi per pod)
- UI enabled, injector disabled

## Notes

- Vault initialization and unseal are manual (no auto-unseal).
-  must be initialized first, followed by  from  and .
- Use  to verify HA cluster status.

