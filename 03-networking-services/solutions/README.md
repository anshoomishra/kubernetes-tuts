# Networking: Solutions and Checks

Confirm the Service selects ready Pods:

```bash
kubectl get pods -l app=web
kubectl get svc web
kubectl get endpointslices -l kubernetes.io/service-name=web
kubectl exec curl-client -- nslookup web
kubectl exec curl-client -- curl -sS -o /dev/null -w '%{http_code}\n' http://web
```

Expected HTTP status is `200`. If there are no EndpointSlices, compare Service selectors with Pod labels and inspect Pod readiness. If DNS fails, check CoreDNS Pods and the client Pod's namespace. A NetworkPolicy has no effect unless the network plugin enforces it.
