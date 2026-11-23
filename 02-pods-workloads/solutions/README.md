# Workloads: Solutions and Checks

Expected checks:

```bash
kubectl rollout status deployment/web
kubectl get deployment web
kubectl get pods -l app=web
kubectl get jobs
kubectl describe cronjob hello-cron
```

The Deployment should report two available replicas initially. A successful image update creates a new ReplicaSet; `kubectl rollout undo` restores the prior Pod template. The Job should reach `Complete`. CronJob-created Jobs may not exist until the schedule runs or a manual Job is created.

If Pods are not ready, inspect `kubectl describe pod` and namespace Events before changing the manifest.
