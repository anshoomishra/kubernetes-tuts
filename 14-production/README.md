# Module 14: Production-Ready Kubernetes

Bring reliability, security, recoverability, and operational discipline together.

## Topics

- High availability, backups, restore, and disaster recovery
- Multi-cluster design, capacity, and cost management
- Multi-tenancy, policy, and least privilege
- SLOs, disruption budgets, rollout safety, and incident response
- Platform engineering, compliance, and governance

## Practical lab

Review and render the production-style Deployment, Service, and PodDisruptionBudget. Apply them only to a disposable namespace after checking cluster context.

```bash
kubectl apply -f 14-production/manifests/production-app.yaml
kubectl rollout status deployment/production-web -n production-lab
kubectl get deployment,service,pdb -n production-lab
kubectl describe pdb production-web -n production-lab
```

Complete the readiness checklist and incident exercise in `runbooks/`. A PodDisruptionBudget protects against some voluntary disruptions; it does not provide high availability by itself.

## Production principles

- Define SLOs and alert on user-visible symptoms.
- Test recovery, not just backup creation.
- Use least privilege, policy, image provenance, and patching.
- Plan capacity and test graceful degradation.
- Review changes, define ownership, and maintain runbooks.

Cleanup: `kubectl delete namespace production-lab`.
