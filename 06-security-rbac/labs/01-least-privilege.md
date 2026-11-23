# Lab: Least-Privilege RBAC and Restricted Pods

## 1. Create the restricted namespace

```bash
kubectl apply -f 06-security-rbac/manifests/security-lab.yaml
kubectl get namespace security-lab --show-labels
```

## 2. Add read-only Pod access and a restricted workload

```bash
kubectl apply -f 06-security-rbac/manifests/viewer-rbac.yaml
kubectl apply -f 06-security-rbac/manifests/restricted-pod.yaml
kubectl get pod restricted-demo -n security-lab
kubectl logs restricted-demo -n security-lab
```

The Pod should print a non-root UID. The `restricted` Pod Security Standard may reject Pods that do not meet its security requirements.

## 3. Check permissions

```bash
kubectl auth can-i list pods --as=system:serviceaccount:security-lab:viewer -n security-lab
kubectl auth can-i create pods --as=system:serviceaccount:security-lab:viewer -n security-lab
kubectl auth can-i get secrets --as=system:serviceaccount:security-lab:viewer -n security-lab
```

Expected: `yes`, `no`, `no`. If impersonation is forbidden, ask an administrator to run the checks or grant the narrow required impersonation permission.

## Cleanup

```bash
kubectl delete namespace security-lab
```
