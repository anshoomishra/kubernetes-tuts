# Lab 1: Create a Local Kubernetes Cluster

## Objective

Create a disposable two-node cluster and verify access to the Kubernetes API.

## 1. Confirm Docker

```bash
docker version
docker ps
```

Docker must be running before creating the cluster.

## 2. Create the cluster

Run this command from the repository root:

```bash
kind create cluster --config 01-foundations/manifests/kind-cluster.yaml
```

The configuration creates one control-plane node and one worker node.

## 3. Select the context

```bash
kubectl config use-context kind-kubernetes-foundations
kubectl config current-context
```

## 4. Verify the cluster

```bash
kubectl cluster-info
kubectl get nodes
kubectl get nodes -o wide
kubectl get componentstatuses
```

Kubernetes may not provide `kubectl get componentstatuses` on every recent release. If it is unavailable, use:

```bash
kubectl get pods -n kube-system
```

## 5. Inspect the system namespace

```bash
kubectl get namespaces
kubectl get pods -n kube-system
kubectl get pods -n kube-system -o wide
```

## Success criteria

- The context is `kind-kubernetes-foundations`.
- `kubectl cluster-info` succeeds.
- Both nodes appear in `kubectl get nodes`.
- Core Kubernetes system Pods are visible.

## Cleanup

```bash
kind delete cluster --name kubernetes-foundations
```
