# Extending Kubernetes: Expected Results

- The CRD reaches `Established`.
- `kubectl explain databaseclaim.spec` displays `engine` and `storageGB`.
- The sample custom resource is accepted and can be retrieved.
- A value below the declared minimum is rejected by API validation.
- No database is created until a controller/operator is implemented and running.

When implementing a controller, test idempotence, invalid input, child-resource drift, status updates, RBAC scope, and deletion/finalizer behavior.
