# Security: Solutions and Review

Verify the namespace policy, Pod security settings, and permissions:

```bash
kubectl get namespace security-lab --show-labels
kubectl get pod restricted-demo -n security-lab -o yaml
kubectl auth can-i list pods --as=system:serviceaccount:security-lab:viewer -n security-lab
kubectl auth can-i create pods --as=system:serviceaccount:security-lab:viewer -n security-lab
kubectl auth can-i get secrets --as=system:serviceaccount:security-lab:viewer -n security-lab
```

The viewer Role grants only `get`, `list`, and `watch` on Pods in one namespace. It does not grant writes, Secret access, or cluster-wide access. The restricted Pod runs non-root, drops capabilities, uses the RuntimeDefault seccomp profile, has a read-only root filesystem, and cannot escalate privileges.

Use `kubectl describe pod` and namespace Events if Pod Security Admission rejects a workload.
