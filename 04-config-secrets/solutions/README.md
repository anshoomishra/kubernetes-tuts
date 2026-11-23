# Configuration: Solutions and Safety Checks

Expected checks:

```bash
kubectl get configmap app-settings -o yaml
kubectl describe deployment config-demo
kubectl logs deployment/config-demo
kubectl exec deployment/config-demo -- cat /etc/app/application.properties
```

The Pod should become Ready after `app-credentials` exists. If it does not, inspect `kubectl describe pod` for `CreateContainerConfigError` and verify the referenced Secret and keys.

Security reminders:

- Base64 encoding in a Secret manifest is not encryption.
- Do not commit credentials, kubeconfigs, or production Secret manifests.
- Restrict Secret access with RBAC and enable encryption at rest in the cluster.
- Prefer a managed secret store and short-lived credentials for production.
