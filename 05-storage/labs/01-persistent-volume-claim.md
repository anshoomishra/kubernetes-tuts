# Lab: PersistentVolumeClaim

## 1. Check cluster storage

```bash
kubectl get storageclass
kubectl get persistentvolumes
```

If no default StorageClass exists, ask your cluster administrator which class to use; do not guess a cloud-specific StorageClass name.

## 2. Create and inspect the claim

```bash
kubectl apply -f 05-storage/manifests/persistent-volume-claim.yaml
kubectl get pvc demo-data
```

Some StorageClasses use `WaitForFirstConsumer`, so the claim remains Pending until a Pod requests it. Create the Pod, then wait for both resources:

```bash
kubectl apply -f 05-storage/manifests/storage-pod.yaml
kubectl wait pod/storage-demo --for=condition=Ready --timeout=120s
kubectl get pvc demo-data
kubectl exec storage-demo -- cat /data/hello.txt
```

The claim should reach `Bound` once the volume is provisioned.

## 3. Verify data survives Pod recreation

```bash
kubectl delete pod storage-demo
kubectl apply -f 05-storage/manifests/storage-pod.yaml
kubectl wait pod/storage-demo --for=condition=Ready --timeout=120s
kubectl exec storage-demo -- cat /data/hello.txt
```

## Cleanup

Check the StorageClass reclaim policy before deleting the claim. Then delete the Pod and claim with the commands in the module README.
