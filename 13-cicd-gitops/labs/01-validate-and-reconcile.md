# Lab: CI Validation and GitOps

## 1. Validate local artifacts

From the repository root:

```bash
helm lint 08-application-management/helm/hello-app
helm template preview 08-application-management/helm/hello-app
kubectl kustomize 08-application-management/kustomize/overlays/dev
kubectl kustomize 08-application-management/kustomize/overlays/prod
```

Review the GitHub Actions workflow. It runs these repeatable render/lint checks for pushes and pull requests; it does not deploy to a cluster.

## 2. Optional Argo CD exercise

Use only a disposable cluster with Argo CD installed. Verify the current context and the Argo CD namespace before applying:

```bash
kubectl config current-context
kubectl get namespace argocd
kubectl apply -f 13-cicd-gitops/gitops/argocd-application.yaml
kubectl get applications -n argocd
```

Observe sync status in the Argo CD UI or CLI. Change the dev overlay in a branch and observe the desired-state diff before merging.

## Cleanup

```bash
kubectl delete -f 13-cicd-gitops/gitops/argocd-application.yaml
```

Deleting the Application does not necessarily delete managed resources unless Argo CD cascading deletion/finalizer behavior is configured. Inspect the Application and cluster before cleanup.
