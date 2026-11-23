# Lab: Events, Logs, and Metrics

## 1. Deploy and inspect the app

```bash
kubectl apply -f 09-observability/manifests/sample-app.yaml
kubectl rollout status deployment/observe-demo
kubectl get pods -l app=observe-demo -o wide
kubectl describe deployment observe-demo
kubectl get events --sort-by=.metadata.creationTimestamp
```

## 2. Read logs and access the app

```bash
kubectl logs deployment/observe-demo --all-pods=true
kubectl port-forward service/observe-demo 8080:80
```

In another terminal, open `http://localhost:8080` or run `curl http://localhost:8080`. Stop forwarding with Ctrl+C.

## 3. Inspect resource metrics

```bash
kubectl top nodes
kubectl top pods
```

If these commands report that metrics are unavailable, check whether Metrics Server is installed and healthy. Do not treat `kubectl top` as a replacement for historical monitoring.

## Extension

Install Prometheus and Grafana in a disposable cluster. Add a dashboard for node and Pod CPU/memory, then create an alert for an unavailable replica. For traces, instrument a sample application with OpenTelemetry and send spans to a lab collector.

## Cleanup

```bash
kubectl delete -f 09-observability/manifests/sample-app.yaml
```
