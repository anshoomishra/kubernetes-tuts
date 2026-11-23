# Application Management: Expected Results

Helm:

- `helm lint` reports no chart errors.
- Default rendering contains a Deployment with two replicas and a ClusterIP Service.
- Overriding `replicaCount=3` changes the rendered/installed Deployment.
- `helm rollback` restores the previous release revision.

Kustomize:

- Dev output uses namespace `hello-dev` and one replica.
- Production output uses namespace `hello-prod` and three replicas.
- Both overlays retain the base Service and Deployment resources.

Inspect output rather than applying a chart or overlay to an unverified cluster context.
