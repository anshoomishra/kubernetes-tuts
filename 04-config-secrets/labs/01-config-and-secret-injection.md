# Lab: ConfigMap and Secret Injection

## 1. Create lab configuration and a disposable Secret

```bash
kubectl apply -f 04-config-secrets/manifests/configmap.yaml
kubectl create secret generic app-credentials --from-literal=username=student --from-literal=password='replace-this-lab-value'
```

Use a fake value only. Do not put credentials in YAML committed to Git.

## 2. Deploy the workload

```bash
kubectl apply -f 04-config-secrets/manifests/deployment.yaml
kubectl rollout status deployment/config-demo
kubectl logs deployment/config-demo
kubectl exec deployment/config-demo -- cat /etc/app/application.properties
```

Inspect the presence, not the value, of the secret environment variables:

```bash
kubectl exec deployment/config-demo -- sh -c 'test -n "$APP_USERNAME" && test -n "$APP_PASSWORD" && echo "Secret variables are set"'
```

## 3. Rotate the Secret

```bash
kubectl create secret generic app-credentials --from-literal=username=student --from-literal=password='new-lab-value' --dry-run=client -o yaml | kubectl apply -f -
kubectl rollout restart deployment/config-demo
kubectl rollout status deployment/config-demo
```

Environment variables are fixed when a container starts; restart Pods to load changed values. Mounted ConfigMap files update eventually, but applications may need to reload them.

## Cleanup

```bash
kubectl delete -f 04-config-secrets/manifests/deployment.yaml
kubectl delete -f 04-config-secrets/manifests/configmap.yaml
kubectl delete secret app-credentials
```
