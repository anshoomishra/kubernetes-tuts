# Module 13: CI/CD and GitOps

Automate validation and delivery while keeping source control as the reviewed record of desired state.

## Topics

- Container build and image registries
- Manifest, Helm, and policy validation in CI
- Deployment promotion and progressive delivery
- Secure CI credentials and workload identity
- GitOps reconciliation with Argo CD or Flux
- Image signing and provenance

## Practical lab

1. Inspect the active workflow at `.github/workflows/validate-kubernetes.yml`.
2. Run Helm lint and render the Kustomize overlays locally.
3. Review the Argo CD Application example before applying it.
4. In a disposable cluster with Argo CD installed, configure the GitOps application and observe reconciliation.
5. Change desired state in Git and inspect the resulting rollout.

The GitOps example references this repository's `main` branch and development overlay. It requires Argo CD and repository access from the cluster.

## Security

Never store registry passwords, kubeconfigs, or production secrets in workflow files. Prefer short-lived credentials and workload identity. Protect deployment branches and require reviewed changes.
