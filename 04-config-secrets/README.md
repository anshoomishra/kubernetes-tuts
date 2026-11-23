# Module 4: Configuration and Secrets

Separate application configuration from container images and learn safe Secret handling.

## Topics

- ConfigMaps and Secrets
- Environment variables and mounted files
- Immutable configuration and update behavior
- Secret rotation, encryption at rest, and external secret stores

## Practical lab

Create the ConfigMap and Deployment, then generate a lab-only Secret locally. Inspect the Pod environment and mounted files. Never commit real credentials.

```bash
kubectl apply -f 04-config-secrets/manifests/configmap.yaml
kubectl create secret generic app-credentials --from-literal=username=student --from-literal=password='replace-this-lab-value'
kubectl apply -f 04-config-secrets/manifests/deployment.yaml
kubectl get configmap,secret
kubectl exec deployment/config-demo -- printenv APP_MODE
```

## Success criteria

- The container receives non-sensitive settings from the ConfigMap.
- Secret values are injected only at runtime.
- You can explain why Base64-encoded Secret data is not encryption.
- You can rotate a Secret and restart workloads that consume it as environment variables.

Cleanup:

```bash
kubectl delete -f 04-config-secrets/manifests/deployment.yaml
kubectl delete -f 04-config-secrets/manifests/configmap.yaml
kubectl delete secret app-credentials --ignore-not-found
```
