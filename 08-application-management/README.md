# Module 8: Application Lifecycle and Configuration Management

Package and customize applications with Helm and Kustomize, and practice release strategies.

## Topics

- Rolling, recreate, blue-green, and canary deployment patterns
- Helm charts, values, releases, and rollback
- Kustomize bases, overlays, patches, and image overrides
- Environment-specific configuration and GitOps principles

## Practical lab

1. Inspect the chart in `helm/hello-app`.
2. Render it before installing.
3. Install, upgrade, inspect, and roll back a Helm release.
4. Build the Kustomize overlays and compare rendered output.

```bash
helm lint 08-application-management/helm/hello-app
helm template hello 08-application-management/helm/hello-app
helm install hello 08-application-management/helm/hello-app
helm list
helm history hello
helm uninstall hello
kubectl kustomize 08-application-management/kustomize/overlays/dev
```

Helm must be installed for chart commands. The examples create resources in the current namespace; verify your context before installation.
