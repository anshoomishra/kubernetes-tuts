# Controller Exercise: Reconcile DatabaseClaim

The CRD and sample resource define an API object only. A controller is needed to act on changes.

## Design goals

Implement a controller using controller-runtime or the Operator SDK that:

1. Watches `DatabaseClaim` objects.
2. Validates supported engine and requested storage.
3. Creates or updates a child workload/resource in the same namespace.
4. Uses owner references so child resources are garbage-collected with the claim.
5. Updates `status.phase` and meaningful status conditions.
6. Reconciles idempotently: running the same reconcile repeatedly converges to the same desired state.
7. Handles deletion cleanly; add a finalizer only if external cleanup is required.

## Suggested progression

- Scaffold a Go operator project and generate API types from the CRD.
- Implement scheme registration and a controller watch.
- Add unit tests for desired-resource generation and reconciliation.
- Run locally against a disposable cluster.
- Build an image and deploy the controller with a dedicated ServiceAccount and narrowly scoped RBAC.
- Test create, update, invalid spec, and delete behavior.

Never give an operator broad cluster-admin rights for convenience. Grant only the API permissions it needs and keep credentials out of source control.
