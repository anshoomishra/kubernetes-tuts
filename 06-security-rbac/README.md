# Module 6: Security and RBAC

Practice least-privilege access and secure Pod defaults in a disposable cluster.

## Topics

- ServiceAccounts and token projection
- Roles, ClusterRoles, and bindings
- Authentication, authorization, and admission
- Pod Security Standards and security contexts
- Linux capabilities, seccomp, image scanning, and supply-chain controls

## Practical lab

The namespace manifest enables the restricted Pod Security Standard. Apply the remaining examples, then test access using the `viewer` ServiceAccount.

```bash
kubectl apply -f 06-security-rbac/manifests/security-lab.yaml
kubectl apply -f 06-security-rbac/manifests/viewer-rbac.yaml
kubectl apply -f 06-security-rbac/manifests/restricted-pod.yaml
kubectl auth can-i list pods --as=system:serviceaccount:security-lab:viewer -n security-lab
kubectl auth can-i create pods --as=system:serviceaccount:security-lab:viewer -n security-lab
```

Expected: listing Pods is allowed; creating Pods is denied. These impersonation checks require your current identity to be permitted to impersonate.

## Success criteria

- A Pod starts under the restricted namespace policy.
- Its container runs as non-root with privilege escalation disabled.
- RBAC grants only the intended read access.

## Cleanup

```bash
kubectl delete namespace security-lab
```

Never apply test security policies to a shared or production namespace without review.
