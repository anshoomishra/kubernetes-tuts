# Lab: Helm and Kustomize

## Helm

```bash
helm lint 08-application-management/helm/hello-app
helm template hello 08-application-management/helm/hello-app
helm install hello 08-application-management/helm/hello-app
kubectl get deployment,service
helm upgrade hello 08-application-management/helm/hello-app --set replicaCount=3
helm history hello
helm rollback hello 1
helm uninstall hello
```

Use `helm template` to inspect rendered YAML before installation.

## Kustomize

```bash
kubectl kustomize 08-application-management/kustomize/overlays/dev
kubectl kustomize 08-application-management/kustomize/overlays/prod
```

Optional apply (creates the target namespaces):

```bash
kubectl create namespace hello-dev
kubectl apply -k 08-application-management/kustomize/overlays/dev
kubectl delete -k 08-application-management/kustomize/overlays/dev
kubectl delete namespace hello-dev
```

## Success criteria

- Rendered Helm output has the requested replica count and valid selectors.
- A Helm release can be upgraded and rolled back.
- Dev and production overlays render different replica counts and namespaces.
