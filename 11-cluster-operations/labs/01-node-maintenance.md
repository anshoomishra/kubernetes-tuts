# Lab: Worker Node Maintenance

Run only in a disposable cluster with at least two workers and a replicated test workload. A single-node cluster may evict workloads without another node to run them.

## 1. Select and inspect a worker

```bash
kubectl get nodes
kubectl get pods -A -o wide
kubectl describe node <worker-node>
```

Confirm there is enough spare capacity and review PodDisruptionBudgets before draining.

## 2. Drain the worker

```bash
kubectl drain <worker-node> --ignore-daemonsets
kubectl get nodes
```

Do not add `--delete-emptydir-data` unless you understand and accept loss of that node-local ephemeral data.

## 3. Simulate maintenance

Perform a harmless lab maintenance step on the VM. Do not modify the control plane or container runtime in a shared environment.

## 4. Return the worker

```bash
kubectl uncordon <worker-node>
kubectl get nodes
kubectl get pods -A -o wide
```

Verify node readiness and workload availability before declaring maintenance complete.
