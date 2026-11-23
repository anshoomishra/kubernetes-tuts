# Module 11: Cluster Installation and Operations

Operate clusters responsibly: plan versions, maintain nodes, secure access, and practice recovery in a lab.

## Topics

- kubeadm bootstrap and managed Kubernetes
- Control-plane and worker-node roles
- Version skew and cluster upgrades
- Certificates and kubeconfig access
- Node maintenance, CNI/CSI integrations, and capacity
- etcd backup/restore and high availability

## Practical topics

Use the guides in `kubeadm/` and `labs/`. kubeadm commands change host and cluster state; run them only on disposable VMs following the Kubernetes version-skew and installation instructions for your target release.

```bash
kubectl get nodes -o wide
kubectl get pods -n kube-system
kubectl drain <node-name> --ignore-daemonsets
kubectl uncordon <node-name>
```

Before any upgrade or maintenance, confirm ownership, access, capacity, backups, rollback options, and application disruption budgets. Never test etcd restore against a production data directory.
