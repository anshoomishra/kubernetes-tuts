# kubeadm Learning Guide

This folder is a checklist for a disposable multi-VM kubeadm lab. Exact package commands vary by operating system and Kubernetes release; follow the official installation guide for the version selected by your lab.

## Lab preparation

- Create at least one control-plane VM and one worker VM.
- Provide supported Linux versions, stable hostnames, unique MAC addresses and product UUIDs.
- Configure time synchronization and required network connectivity.
- Disable swap or configure the kubelet consistently with the chosen release.
- Install a compatible container runtime and configure its cgroup driver.
- Install matching `kubeadm`, `kubelet`, and `kubectl` versions.
- Allow the required control-plane and node ports only on the lab network.

## Bootstrap sequence

1. Validate prerequisites and runtime health on every VM.
2. Initialize the first control-plane node with `kubeadm init` using a planned Pod CIDR.
3. Configure kubeconfig for the administrator account.
4. Install a CNI plugin compatible with the selected Kubernetes version and Pod CIDR.
5. Confirm control-plane system Pods and node readiness.
6. Join worker nodes using the generated join command; do not publish or commit join tokens.
7. Verify node and CoreDNS readiness.

## Operations exercises

- Drain and uncordon a worker while observing application availability.
- Back up etcd using the procedure for your topology and verify the backup.
- In a separate disposable cluster, restore the backup and validate API state.
- Upgrade one minor version at a time following the official upgrade plan.
- Review certificate expiration and kubeconfig access.

## Safety

Do not run bootstrap, reset, upgrade, or etcd restore commands on a shared cluster. Backups and join tokens contain sensitive cluster data; keep them out of Git.
