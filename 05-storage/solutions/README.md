# Storage: Solutions and Checks

Check PVC and Pod state:

```bash
kubectl get pvc demo-data
kubectl describe pvc demo-data
kubectl get pod storage-demo -o wide
kubectl exec storage-demo -- cat /data/hello.txt
```

The claim should reach `Bound`, and the file should remain after recreating the Pod while keeping the claim. A Pending claim usually indicates there is no matching/default StorageClass, insufficient capacity, or a provisioner issue; inspect PVC Events.

Deleting a PVC can result in permanent data loss. Inspect the PV's reclaim policy and retain any data needed before cleanup.
