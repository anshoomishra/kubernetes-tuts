# Module 5: Kubernetes Storage

Learn ephemeral volumes, persistent claims, dynamic provisioning, and stateful workloads.

## Topics

- Volume types and Pod volume lifecycle
- PersistentVolumes, PersistentVolumeClaims, and StorageClasses
- Access modes, CSI, expansion, and StatefulSets
- Data backup and restore

## Practical lab

Apply the claim and Pod. The claim relies on a default StorageClass; inspect available classes first. The Pod writes a file to persistent storage. Delete and recreate the Pod to confirm the data survives.

```bash
kubectl get storageclass
kubectl apply -f 05-storage/manifests/persistent-volume-claim.yaml
kubectl apply -f 05-storage/manifests/storage-pod.yaml
kubectl rollout status pod/storage-demo
kubectl exec storage-demo -- cat /data/hello.txt
kubectl delete pod storage-demo
kubectl apply -f 05-storage/manifests/storage-pod.yaml
kubectl exec storage-demo -- cat /data/hello.txt
```

If there is no default StorageClass, use a cluster-specific class in the PVC. Do not use `hostPath` as shared or durable production storage.

## Cleanup

```bash
kubectl delete -f 05-storage/manifests/storage-pod.yaml
kubectl delete -f 05-storage/manifests/persistent-volume-claim.yaml
```

PVC deletion may delete dynamically provisioned backing storage depending on the StorageClass reclaim policy. Verify it before cleanup.
