# Lab: Workloads and Rollouts

Apply the workload examples from the module README. Observe resource ownership:

```bash
kubectl get pods --show-labels
kubectl describe deployment web
kubectl get replicasets
```

Scale, update, inspect, and roll back:

```bash
kubectl scale deployment/web --replicas=3
kubectl set image deployment/web nginx=nginx:1.28-alpine
kubectl rollout status deployment/web
kubectl rollout history deployment/web
kubectl rollout undo deployment/web
```

The CronJob schedule is every 15 minutes. Trigger a one-off Job from it rather than waiting:

```bash
kubectl create job hello-cron-manual --from=cronjob/hello-cron
kubectl get jobs,pods
kubectl logs job/hello-cron-manual
```

Cleanup:

```bash
kubectl delete -f 02-pods-workloads/manifests/workloads.yaml
kubectl delete job hello-cron-manual --ignore-not-found
```
