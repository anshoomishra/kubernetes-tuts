# Lab 2: Explore Kubernetes and Create a Pod

## Objective

Use declarative manifests and imperative commands to create and inspect resources.

## 1. Create a namespace

```bash
kubectl apply -f 01-foundations/manifests/namespace.yaml
kubectl get namespace foundations-lab
```

Optional imperative alternative:

```bash
kubectl create namespace foundations-lab-imperative
kubectl delete namespace foundations-lab-imperative
```

## 2. Change the default namespace

```bash
kubectl config set-context --current --namespace=foundations-lab
kubectl config view --minify --output 'jsonpath={..namespace}'
```

The output should be `foundations-lab`.

## 3. Explore the API

```bash
kubectl api-resources
kubectl api-versions
kubectl explain pod
kubectl explain pod.spec
kubectl explain pod.spec.containers
```

## 4. Create the first Pod declaratively

```bash
kubectl apply -f 01-foundations/manifests/pod.yaml
kubectl get pods
kubectl get pod hello-pod -o yaml
```

Wait until the status is `Running`:

```bash
kubectl wait pod/hello-pod --for=condition=Ready --timeout=120s
```

## 5. Create a second Pod imperatively

```bash
kubectl run busybox-check --image=busybox:1.36 --restart=Never --command -- sh -c "echo Kubernetes foundations; sleep 3600"
kubectl get pods
kubectl logs busybox-check
```

Delete it afterward:

```bash
kubectl delete pod busybox-check
```

## 6. Inspect the nginx Pod

```bash
kubectl describe pod hello-pod
kubectl logs hello-pod
kubectl exec hello-pod -- nginx -t
```

Port-forward to access nginx:

```bash
kubectl port-forward pod/hello-pod 8080:80
```

Open `http://localhost:8080` in another terminal or replace the command with:

```bash
curl http://localhost:8080
```

Stop port forwarding with `Ctrl+C`.

## 7. Test Pod deletion

Delete the Pod and recreate it:

```bash
kubectl delete pod hello-pod
kubectl apply -f 01-foundations/manifests/pod.yaml
kubectl get pod hello-pod
```

A standalone Pod is not automatically replaced after deletion.

## Success criteria

- The `foundations-lab` namespace exists.
- The current context uses `foundations-lab`.
- `hello-pod` is `Running` and `Ready`.
- The nginx configuration passes `nginx -t`.
- Port forwarding returns the nginx page.

## Cleanup

```bash
kubectl delete -f 01-foundations/manifests/namespace.yaml
```

Deleting the namespace removes resources in that namespace.
