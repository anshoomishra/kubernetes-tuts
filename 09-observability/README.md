# Module 9: Observability

Observe Kubernetes and application health through events, logs, metrics, and traces.

## Topics

- Events, container logs, and debugging tools
- Metrics Server, Prometheus, and Grafana
- Alert rules, exporters, and application metrics
- OpenTelemetry and distributed tracing
- Centralized logs, SLOs, and error budgets

## Practical lab

Deploy the sample app and practice resource inspection, logs, and port-forwarding:

```bash
kubectl apply -f 09-observability/manifests/sample-app.yaml
kubectl rollout status deployment/observe-demo
kubectl get pods,svc
kubectl logs deployment/observe-demo
kubectl top pods
kubectl port-forward service/observe-demo 8080:80
```

`kubectl top` requires Metrics Server. Prometheus, Grafana, and tracing backends are separate add-ons; install them using the method supported by your lab cluster.

## Success criteria

- You can correlate Pod status, Events, and logs.
- You can explain the difference between resource metrics and application metrics.
- You can access the sample through port-forwarding.

Cleanup: `kubectl delete -f 09-observability/manifests/sample-app.yaml`.
