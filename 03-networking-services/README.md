# Module 3: Services and Kubernetes Networking

Learn Pod-to-Pod connectivity, stable Service endpoints, DNS, ingress routing, and traffic policy.

## Topics

- ClusterIP, NodePort, LoadBalancer, and headless Services
- Service discovery, DNS, EndpointSlices, and kube-proxy
- Ingress controllers and Gateway API
- NetworkPolicy and CNI behavior
- TLS termination and service-mesh concepts

## Practical lab

Apply the sample Deployment and Service, test DNS and HTTP from a temporary client, then apply the ingress and NetworkPolicy examples when your cluster supports them.

```bash
kubectl apply -f 03-networking-services/manifests/networking.yaml
kubectl get svc,endpointslices,pods
kubectl run curl-client --image=curlimages/curl:8.10.1 --restart=Never -- sleep 3600
kubectl exec curl-client -- curl -sS http://web
kubectl delete pod curl-client
```

Ingress requires an installed Ingress Controller. NetworkPolicy requires a CNI plugin that enforces policies; a policy object alone may not block traffic.

## Success criteria

- The Service has endpoints for ready Pods.
- DNS resolves the Service name inside the cluster.
- HTTP requests through the Service reach nginx.
- You can describe which cluster add-ons are required for Ingress and NetworkPolicy.

Cleanup: `kubectl delete -f 03-networking-services/manifests/networking.yaml`.
