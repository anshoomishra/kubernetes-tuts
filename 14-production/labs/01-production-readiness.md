# Lab: Production Readiness Review

## 1. Inspect before applying

```bash
kubectl config current-context
kubectl apply --dry-run=client -f 14-production/manifests/production-app.yaml
```

Apply only to a disposable cluster:

```bash
kubectl apply -f 14-production/manifests/production-app.yaml
kubectl rollout status deployment/production-web -n production-lab
kubectl get deployment,service,pdb,pods -n production-lab
```

## 2. Review availability behavior

Check that the Deployment has three ready replicas and that the PodDisruptionBudget has allowed disruptions when the cluster has sufficient healthy Pods. Do not drain a production node as part of this exercise.

## 3. Complete the checklist

Use `runbooks/production-readiness-checklist.md` to record evidence for health, security, capacity, monitoring, recovery, and ownership.

## 4. Practice an incident tabletop

Use `runbooks/incident-response.md` to walk through a simulated elevated-error-rate incident. Do not create real service disruption.

## Cleanup

```bash
kubectl delete namespace production-lab
```
