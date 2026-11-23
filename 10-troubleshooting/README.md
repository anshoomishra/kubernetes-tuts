# Module 10: Troubleshooting

Practice diagnosing common workload and connectivity failures. Each file in `broken-manifests/` has one deliberate issue; apply examples individually in a disposable cluster.

## Failure scenarios

- `crash-loop.yaml`: process exits immediately.
- `bad-image.yaml`: image cannot be pulled.
- `missing-config.yaml`: referenced ConfigMap does not exist.
- `unschedulable.yaml`: resource request exceeds available capacity.

## Practical workflow

1. Observe the status with `kubectl get`.
2. Read Pod Events using `kubectl describe`.
3. Check logs, previous logs, and container state.
4. Form a hypothesis, change one thing, and verify recovery.
5. Record cause, impact, fix, and prevention in a runbook.

Useful commands:

```bash
kubectl get pods -o wide
kubectl describe pod <pod-name>
kubectl logs <pod-name>
kubectl logs <pod-name> --previous
kubectl get events --sort-by=.metadata.creationTimestamp
kubectl get nodes
kubectl get endpointslices
```

## Safety

Use an isolated cluster. Do not simulate node failures or alter control-plane/etcd state on shared clusters. The etcd recovery exercise belongs only in a disposable kubeadm lab with a verified backup.
