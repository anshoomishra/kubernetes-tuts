# Observability: Expected Checks

```bash
kubectl get deployment observe-demo
kubectl get pods -l app=observe-demo
kubectl get endpointslices -l kubernetes.io/service-name=observe-demo
kubectl logs deployment/observe-demo --all-pods=true
kubectl get events --sort-by=.metadata.creationTimestamp
```

The Deployment should have two available replicas and the Service should have ready endpoints. Logs show nginx startup messages. Metrics are available only when the cluster has a functioning metrics API. Events are short-lived cluster observations; use a metrics/logging backend for retention and alerting.
