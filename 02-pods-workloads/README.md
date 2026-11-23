# Module 2: Pods and Workloads

Learn how Kubernetes runs containers, maintains replicas, and performs safe workload updates.

## Topics

- Pod lifecycle, labels, annotations, and container configuration
- Init containers, probes, environment variables, and resource requests/limits
- Deployments, ReplicaSets, StatefulSets, DaemonSets, Jobs, and CronJobs
- Rollouts, scaling, scheduling constraints, and rollback

## Practical lab

1. Apply `manifests/workloads.yaml`.
2. Wait for the Deployment to become ready and inspect its Pods.
3. Scale the Deployment, then update its image and inspect the rollout history.
4. Roll back to the previous revision.
5. Inspect and run the Job and CronJob examples.
6. Delete the lab resources when finished.

```bash
kubectl apply -f 02-pods-workloads/manifests/workloads.yaml
kubectl get deployments,pods,jobs,cronjobs
kubectl rollout status deployment/web
kubectl scale deployment/web --replicas=3
kubectl rollout history deployment/web
kubectl rollout undo deployment/web
kubectl delete -f 02-pods-workloads/manifests/workloads.yaml
```

## Success criteria

- The Deployment reaches its desired replica count.
- Readiness and liveness probes report healthy.
- You can explain the effect of scaling and rollback.
- The Job completes successfully.

Use a disposable cluster; CronJobs create Pods on a schedule.
