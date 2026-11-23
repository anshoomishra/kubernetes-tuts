# Production Readiness Checklist

Record evidence, owner, and review date for each item; a checked box without evidence is not verification.

## Workload

- [ ] Multiple replicas across suitable failure domains
- [ ] Readiness, liveness, and startup probes reflect application behavior
- [ ] CPU/memory requests and limits are measured and reviewed
- [ ] Graceful shutdown and termination grace period are tested
- [ ] Rollout strategy and rollback procedure are documented
- [ ] PodDisruptionBudget matches the service availability objective

## Security

- [ ] Non-root execution and least privilege are used where supported
- [ ] No privileged containers or unnecessary capabilities
- [ ] Images are pinned, scanned, and provenance is verified
- [ ] RBAC and namespace boundaries are reviewed
- [ ] Secrets use an approved manager, rotation, and encryption at rest
- [ ] Network policies and admission policies are tested

## Reliability and operations

- [ ] Service-level indicators and objectives are documented
- [ ] Alerts are actionable and have an owner
- [ ] Logs, metrics, and traces are retained appropriately
- [ ] Capacity and scaling behavior have been load-tested
- [ ] Backup and restore have been tested against recovery objectives
- [ ] Upgrade, incident, and rollback runbooks are current
- [ ] On-call ownership and escalation are documented

## Governance

- [ ] Data classification, retention, and compliance requirements are known
- [ ] Cost ownership and budget alerts are configured
- [ ] Changes are reviewed and auditable
