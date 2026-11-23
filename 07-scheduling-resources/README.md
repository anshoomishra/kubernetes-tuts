# Module 7: Scheduling and Resource Management

Learn how Kubernetes places Pods and controls resource consumption.

## Topics

- Requests, limits, and scheduling decisions
- Taints, tolerations, node affinity, and topology spread
- LimitRanges and ResourceQuotas
- Priority, preemption, HPA, VPA, and cluster autoscaling

## Practical lab

Create a namespace with a quota and per-Pod defaults, deploy a workload, and inspect its scheduling and resource settings.

```bash
kubectl apply -f 07-scheduling-resources/manifests/resource-policies.yaml
kubectl apply -f 07-scheduling-resources/manifests/web-deployment.yaml
kubectl get resourcequota,limitrange,pods -n scheduling-lab
kubectl describe pod -n scheduling-lab
```

If Metrics Server is installed, optionally apply the HPA example. HPA requires resource requests and available metrics.

## Success criteria

- Pods schedule with explicit CPU and memory requests.
- The namespace quota reports usage and enforces limits.
- You can diagnose a Pod that cannot be scheduled from its Events.

Cleanup:

```bash
kubectl delete namespace scheduling-lab
kubectl delete -f 07-scheduling-resources/manifests/hpa.yaml --ignore-not-found
```
