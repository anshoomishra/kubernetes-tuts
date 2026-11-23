# Module 1: Command Reference and Solution

## Validate the manifests

```bash
kubectl apply --dry-run=client -f 01-foundations/manifests/namespace.yaml
kubectl apply --dry-run=client -f 01-foundations/manifests/pod.yaml
```

## Complete declarative solution

```bash
kubectl apply -f 01-foundations/manifests/namespace.yaml
kubectl config set-context --current --namespace=foundations-lab
kubectl apply -f 01-foundations/manifests/pod.yaml
kubectl wait pod/hello-pod --for=condition=Ready --timeout=120s
kubectl get pod hello-pod -o wide
kubectl describe pod hello-pod
kubectl logs hello-pod
```

## Complete imperative Pod solution

```bash
kubectl run hello-imperative --namespace=foundations-lab --image=nginx:1.27-alpine --port=80
kubectl get pod hello-imperative --namespace=foundations-lab
kubectl delete pod hello-imperative --namespace=foundations-lab
```

## Useful troubleshooting commands

```bash
kubectl get pods -n foundations-lab
kubectl describe pod hello-pod -n foundations-lab
kubectl logs hello-pod -n foundations-lab
kubectl get events -n foundations-lab --sort-by=.metadata.creationTimestamp
kubectl get pod hello-pod -n foundations-lab -o jsonpath='{.status.phase}'
```

## Reset the lab

```bash
kubectl delete namespace foundations-lab --ignore-not-found
kubectl apply -f 01-foundations/manifests/namespace.yaml
kubectl apply -f 01-foundations/manifests/pod.yaml
```
