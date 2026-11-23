# Lab: Diagnose Common Failures

Run one scenario at a time. Capture the initial status, diagnosis, corrective action, and verified result before moving to the next scenario.

## CrashLoopBackOff

```bash
kubectl apply -f 10-troubleshooting/broken-manifests/crash-loop.yaml
kubectl get pod crash-loop-demo --watch
kubectl describe pod crash-loop-demo
kubectl logs crash-loop-demo --previous
```

## ImagePullBackOff

```bash
kubectl apply -f 10-troubleshooting/broken-manifests/bad-image.yaml
kubectl describe pod bad-image-demo
```

## Missing configuration

```bash
kubectl apply -f 10-troubleshooting/broken-manifests/missing-config.yaml
kubectl describe pod missing-config-demo
```

## Unschedulable Pod

```bash
kubectl apply -f 10-troubleshooting/broken-manifests/unschedulable.yaml
kubectl describe pod unschedulable-demo
```

Compare your diagnosis with `solutions/README.md`. Delete each test Pod before continuing:

```bash
kubectl delete pod crash-loop-demo bad-image-demo missing-config-demo unschedulable-demo --ignore-not-found
```
