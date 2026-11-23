# Module 12: Extending Kubernetes

Extend the API with CustomResourceDefinitions (CRDs), then learn how controllers reconcile custom resources.

## Topics

- CRD schema and validation
- Custom resources and API versions
- Reconciliation loops, status, and finalizers
- Admission webhooks and API aggregation
- Kubernetes client libraries, controller-runtime, and operators

## Practical lab

Apply the CRD first, wait for it to be established, then create the example resource:

```bash
kubectl apply -f 12-extending-kubernetes/crd/database-claim-crd.yaml
kubectl wait --for=condition=Established --timeout=60s crd/databaseclaims.learning.example.com
kubectl apply -f 12-extending-kubernetes/crd/sample-database-claim.yaml
kubectl get databaseclaims
kubectl describe databaseclaim demo
```

The CRD defines and validates data only; it does not provision a database. Build the reconciliation exercise using the design guide in `controller/README.md`.

Cleanup:

```bash
kubectl delete -f 12-extending-kubernetes/crd/sample-database-claim.yaml
kubectl delete -f 12-extending-kubernetes/crd/database-claim-crd.yaml
```

Deleting a CRD deletes its custom resources. Confirm the resources are disposable before removal.
