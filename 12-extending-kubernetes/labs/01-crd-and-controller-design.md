# Lab: Define a Custom Resource

## 1. Install the CRD

```bash
kubectl apply -f 12-extending-kubernetes/crd/database-claim-crd.yaml
kubectl wait --for=condition=Established --timeout=60s crd/databaseclaims.learning.example.com
kubectl explain databaseclaim.spec
```

## 2. Create and inspect an instance

```bash
kubectl apply -f 12-extending-kubernetes/crd/sample-database-claim.yaml
kubectl get databaseclaims
kubectl get databaseclaim demo -o yaml
```

## 3. Test schema validation

Create a temporary copy of the sample with `storageGB: 0` and try to apply it. The API server should reject the value because the schema requires at least one GiB. Do not edit the valid sample to make this test.

## 4. Design its controller

Use the exercise in `controller/README.md` to identify desired child resources, RBAC permissions, status conditions, and deletion behavior. A CRD without a controller stores API data but does not provision a database.

## Cleanup

```bash
kubectl delete -f 12-extending-kubernetes/crd/sample-database-claim.yaml
kubectl delete -f 12-extending-kubernetes/crd/database-claim-crd.yaml
```
