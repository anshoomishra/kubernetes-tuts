# Scheduling: Solutions and Checks

```bash
kubectl get pods -n scheduling-lab -o wide
kubectl describe pod -n scheduling-lab
kubectl describe resourcequota compute-quota -n scheduling-lab
kubectl get hpa -n scheduling-lab
```

The Deployment declares CPU/memory requests and limits. The namespace quota aggregates resource usage; LimitRange supplies defaults to containers without explicit values. Topology spread attempts to distribute Pods by node hostname, but `ScheduleAnyway` allows placement when perfect distribution is not possible.

For `FailedScheduling`, inspect Pod Events for insufficient CPU/memory, taints, node selectors, or volume constraints. HPA requires a functioning metrics API and CPU requests to calculate utilization.
