# Lab: Services, DNS, and NetworkPolicy

## 1. Create a stable Service

```bash
kubectl apply -f 03-networking-services/manifests/networking.yaml
kubectl get service web
kubectl get endpointslices -l kubernetes.io/service-name=web
```

## 2. Test in-cluster DNS and HTTP

```bash
kubectl run curl-client --image=curlimages/curl:8.10.1 --restart=Never -- sleep 3600
kubectl wait pod/curl-client --for=condition=Ready --timeout=90s
kubectl exec curl-client -- curl -sS http://web
kubectl exec curl-client -- nslookup web
```

## 3. Observe policy behavior

The sample policy permits ingress to `app=web` only from Pods in the same namespace. Test from another namespace to see whether your CNI enforces the policy. Without a policy-enforcing CNI, traffic may still pass.

## 4. Optional Ingress

Install and configure an Ingress Controller for your cluster, then apply `manifests/ingress.yaml`. Point `web.example.test` to the controller's address (for a local lab, a hosts-file entry may be required).

## Cleanup

```bash
kubectl delete pod curl-client --ignore-not-found
kubectl delete -f 03-networking-services/manifests/ingress.yaml --ignore-not-found
kubectl delete -f 03-networking-services/manifests/networking.yaml
```
