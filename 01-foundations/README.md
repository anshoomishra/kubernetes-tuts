# Module 1: Kubernetes Foundations

This module introduces containers, Kubernetes architecture, local clusters, namespaces, contexts, and the Kubernetes API.

## Learning objectives

By the end of this module, you will be able to:

- Explain the Kubernetes control plane and worker node components.
- Distinguish a container runtime, kubelet, Pod, and Kubernetes object.
- Create and access a local Kubernetes cluster.
- Switch namespaces and kubeconfig contexts safely.
- Inspect resources using `kubectl`.
- Create a Pod using imperative and declarative commands.
- Explain the `apiVersion`, `kind`, `metadata`, and `spec` fields in a manifest.

## Prerequisites

Install:

- Docker Desktop or another container runtime
- `kubectl`
- `kind`

Verify the tools:

```bash
docker version
kubectl version --client
kind version
```

## Architecture overview

```text
                    kubectl
                       |
                       v
+------------------------------------------------+
| Kubernetes API Server                          |
|                                                |
| API Server -> etcd                             |
| API Server -> Scheduler -> Node assignment     |
| API Server -> Controller Manager               |
+------------------------------------------------+
                       |
                       v
+-----------------------+-----------------------+
| Worker node           | Worker node           |
| kubelet               | kubelet               |
| kube-proxy            | kube-proxy            |
| container runtime     | container runtime     |
| Pods                  | Pods                  |
+-----------------------+-----------------------+
```

### Core components

- **API server:** Validates and serves the Kubernetes API.
- **etcd:** Stores cluster state.
- **Scheduler:** Assigns unscheduled Pods to nodes.
- **Controller manager:** Runs controllers that reconcile desired and actual state.
- **kubelet:** Runs and monitors containers on a worker node.
- **kube-proxy:** Implements Service networking rules.
- **Container runtime:** Runs OCI-compatible containers through CRI.

## Folder guide

```text
01-foundations/
├── README.md
├── manifests/
│   ├── kind-cluster.yaml
│   ├── namespace.yaml
│   └── pod.yaml
├── labs/
│   ├── 01-create-local-cluster.md
│   └── 02-explore-kubernetes.md
└── solutions/
    ├── commands.md
    └── expected-results.md
```

## Practical sequence

1. [Create a local cluster](labs/01-create-local-cluster.md)
2. [Explore resources and create a Pod](labs/02-explore-kubernetes.md)

## Core commands

```bash
kubectl cluster-info
kubectl get nodes
kubectl get namespaces
kubectl get pods -A
kubectl api-resources
kubectl api-versions
kubectl explain pod
kubectl explain pod.spec.containers
kubectl config get-contexts
kubectl config current-context
```

## Cleanup

Delete the namespace and local cluster:

```bash
kubectl delete namespace foundations-lab
kind delete cluster --name kubernetes-foundations
```
