# CI/CD and GitOps: Expected Results

- Helm lint succeeds and chart rendering produces Kubernetes resources.
- Both Kustomize overlays render without errors.
- CI validates artifacts but does not access or modify a cluster.
- When installed in a lab Argo CD cluster, the Application points to the dev overlay and reports synchronization/health status.

GitOps changes should be made through reviewed source-control commits. If reconciliation fails, inspect the Application conditions, repository credentials, target path, rendered resources, and namespace permissions.
