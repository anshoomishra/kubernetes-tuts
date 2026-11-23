# Cluster Operations: Maintenance Checklist

Before drain:

- Confirm the target node and current context.
- Check replicas, spare capacity, PodDisruptionBudgets, and local data.
- Notify service owners and ensure monitoring is available.

During maintenance:

- Drain only the intended node.
- Observe evicted Pods and application health.
- Keep an approved rollback path.

After maintenance:

- Uncordon the node.
- Verify node readiness, system Pods, and workload replicas.
- Check Events and application health signals.
- Record outcome and any follow-up actions.

Use official release-specific documentation for kubeadm upgrades and etcd backup/restore; do not improvise restore flags or version transitions.
