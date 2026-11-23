# Lab: Quotas, Scheduling, and Autoscaling

## 1. Apply namespace policies and Deployment

```bash
kubectl apply -f 07-scheduling-resources/manifests/resource-policies.yaml
kubectl apply -f 07-scheduling-resources/manifests/web-deployment.yaml
kubectl rollout status deployment/web -n scheduling-lab
kubectl get resourcequota,limitrange,pods -n scheduling-lab
```

## 2. Inspect placement and resource usage

```bash
kubectl get pods -n scheduling-lab -o wide
kubectl describe resourcequota compute-quota -n scheduling-lab
kubectl describe pod -n scheduling-lab
```

Compare Pod placement with available node capacity. Try setting a high request on a disposable Pod and inspect why it remains Pending.

## 3. Optional autoscaling

Metrics Server must be installed:

```bash
kubectl top nodes
kubectl top pods -n scheduling-lab
kubectl apply -f 07-scheduling-resources/manifests/hpa.yaml
kubectl get hpa -n scheduling-lab --watch
```

If metrics show `<unknown>`, inspect Metrics Server and wait for metrics to become available. An HPA object alone does not install Metrics Server.

## Cleanup

```bash
kubectl delete namespace scheduling-lab
```
