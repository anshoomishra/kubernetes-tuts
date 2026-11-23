# Kubernetes Tutorials

A topic-wise, practical syllabus for learning Kubernetes from fundamentals to production operations.

## 1. Learning Objectives

By the end of this syllabus, you should be able to:

- Understand Kubernetes architecture and how cluster components interact.
- Create, configure, deploy, scale, update, and troubleshoot workloads.
- Design Kubernetes networking, storage, security, and observability.
- Package applications with Helm and manage resources with Kustomize.
- Deploy and operate Kubernetes using local tools and managed cloud platforms.
- Automate validation, image delivery, and deployments using CI/CD.
- Diagnose cluster failures and apply production-ready operational practices.
- Prepare for the CKA, CKAD, and CKS certification tracks.

## 2. Prerequisites

Before starting, learn the basics of:

- Linux commands and file permissions
- YAML syntax and JSON
- Docker or another OCI-compatible container runtime
- Basic networking: IP addresses, DNS, ports, TCP/UDP, and HTTP
- Git and GitHub
- A shell such as Bash or PowerShell
- Basic systemd, logging, and process concepts

## 3. Complete Kubernetes Syllabus

### Module 1: Kubernetes Foundations

**Topics**

- Containers and container images
- Kubernetes purpose and architecture
- Control plane: API server, etcd, scheduler, and controller manager
- Worker nodes: kubelet and kube-proxy
- Container runtimes and CRI
- Kubernetes objects and API conventions
- Namespaces and contexts
- Declarative configuration with YAML

**Practical topics**

- Install Docker or Podman.
- Install `kubectl`, `kind`, `minikube`, and optionally `k3d`.
- Create a local multi-node cluster.
- Inspect cluster components and API resources.
- Switch namespaces and kubeconfig contexts.
- Use `kubectl explain`, `api-resources`, and `api-versions`.
- Create a Pod using both imperative and declarative commands.

### Module 2: Pods and Workloads

**Topics**

- Pods and Pod lifecycle
- Containers, init containers, and ephemeral containers
- Labels and annotations
- Commands, arguments, environment variables, and working directories
- Restart policies
- Probes: startup, liveness, and readiness
- Resource requests and limits
- Scheduling hints: node selectors and affinity
- Deployments, ReplicaSets, StatefulSets, DaemonSets, and Jobs
- CronJobs
- Update strategies and rollbacks

**Practical topics**

- Write and apply a multi-container Pod.
- Add init containers and shared volumes.
- Configure environment variables and ConfigMaps.
- Add liveness, readiness, and startup probes.
- Set CPU and memory requests and limits.
- Create Deployments and scale them.
- Perform rolling updates and rollbacks.
- Create Jobs and scheduled CronJobs.
- Deploy a DaemonSet.
- Schedule workloads with node selectors and affinity rules.

### Module 3: Services and Kubernetes Networking

**Topics**

- Pod and Service networking
- ClusterIP, NodePort, and LoadBalancer Services
- Endpoints and EndpointSlices
- DNS and service discovery
- Ingress and Ingress Controllers
- Gateway API
- NetworkPolicies
- CNI plugins
- Service mesh concepts
- Headless Services

**Practical topics**

- Expose a Deployment with ClusterIP.
- Use NodePort and LoadBalancer Services.
- Test in-cluster DNS resolution.
- Configure an Ingress with hostname routing.
- Add TLS certificates to an Ingress.
- Create deny-all and allow-specific NetworkPolicies.
- Test blocked and allowed traffic between Pods.
- Configure a headless Service.
- Inspect Service endpoints and kube-proxy rules.

### Module 4: Configuration and Secrets

**Topics**

- ConfigMaps
- Secrets
- Environment variables and volume injection
- Immutable configuration
- Mounted configuration updates
- External Secret Managers
- Secret encryption at rest
- Configuration best practices

**Practical topics**

- Store application settings in a ConfigMap.
- Mount a ConfigMap as files.
- Create Secrets from literals and files.
- Consume Secrets as environment variables and volumes.
- Verify Secret encoding and access controls.
- Rotate a configuration without rebuilding an image.
- Integrate a Kubernetes Secret with a cloud secret manager.

### Module 5: Storage

**Topics**

- Volumes and volume lifecycle
- EmptyDir, hostPath, and projected volumes
- PersistentVolumes and PersistentVolumeClaims
- StorageClasses
- Dynamic provisioning
- Access modes
- Volume expansion
- Stateful application storage
- Backup and restore concepts
- CSI drivers

**Practical topics**

- Share data between containers with EmptyDir.
- Mount a ConfigMap or Secret as a projected volume.
- Create a PersistentVolumeClaim.
- Attach storage to a Deployment or StatefulSet.
- Create and use a StorageClass.
- Expand a persistent volume.
- Use local storage for development.
- Back up and restore application data.

### Module 6: Security and Access Control

**Topics**

- Authentication and authorization
- Kubernetes users and service accounts
- RBAC: roles, ClusterRoles, bindings, and access rules
- Pod Security Standards
- Security contexts
- Linux capabilities and read-only root filesystems
- Seccomp, AppArmor, and SELinux concepts
- Admission controllers
- ServiceAccount tokens and projected tokens
- Supply-chain security
- Image signing and verification

**Practical topics**

- Create a ServiceAccount.
- Create namespace-scoped and cluster-scoped RBAC policies.
- Test permissions with `kubectl auth can-i`.
- Run a Pod with a restricted security context.
- Disable privilege escalation and remove capabilities.
- Apply the restricted Pod Security Admission level.
- Enable audit logging where supported.
- Scan images and Kubernetes manifests.
- Verify signed container images.

### Module 7: Scheduling and Cluster Resource Management

**Topics**

- Scheduling process
- Taints and tolerations
- Node affinity and anti-affinity
- Pod topology spread constraints
- Resource requests and limits
- LimitRanges and ResourceQuotas
- Priority and preemption
- Horizontal and vertical Pod autoscaling
- Cluster autoscaling
- Topology and failure domains

**Practical topics**

- Taint a node and add an appropriate toleration.
- Schedule Pods across zones or nodes.
- Configure topology spread constraints.
- Add ResourceQuota and LimitRange policies.
- Measure resource usage with Metrics Server.
- Configure a HorizontalPodAutoscaler.
- Configure a VerticalPodAutoscaler in a lab environment.
- Simulate scheduling failures and resolve them.

### Module 8: Application Lifecycle and Configuration Management

**Topics**

- Deployment strategies
- Recreate, rolling, blue-green, and canary releases
- Helm charts and values
- Helm repositories and chart dependencies
- Kustomize bases and overlays
- Environment-specific configuration
- Release rollback
- Continuous delivery patterns
- GitOps principles

**Practical topics**

- Create a Helm chart for a sample application.
- Override values for development and production.
- Install, upgrade, and roll back a Helm release.
- Build Kustomize bases and overlays.
- Perform rolling, blue-green, and canary releases.
- Deploy configuration using GitOps tools.
- Reconcile out-of-band configuration changes.

### Module 9: Observability

**Topics**

- Kubernetes events and logs
- Metrics Server
- Prometheus and exporters
- Grafana dashboards
- PrometheusRule alerts
- Distributed tracing
- OpenTelemetry
- Application and infrastructure metrics
- Logging agents and centralized logging
- SLOs and error budgets

**Practical topics**

- Debug application logs with `kubectl logs`.
- Use `kubectl debug` and ephemeral containers.
- Install Metrics Server.
- Monitor CPU and memory usage.
- Deploy Prometheus and Grafana.
- Create dashboards and alert rules.
- Correlate Pod events, logs, and metrics.
- Send application traces through OpenTelemetry.
- Configure centralized application logs.

### Module 10: Troubleshooting

**Topics**

- Pod states: Pending, Running, Succeeded, Failed, Unknown
- CrashLoopBackOff and restart analysis
- ImagePullBackOff and registry failures
- DNS and Service failures
- NetworkPolicy debugging
- Node health and kubelet problems
- Control plane and etcd failures
- API server connectivity
- Resource pressure and eviction
- CoreDNS troubleshooting
- Disaster recovery

**Practical topics**

- Diagnose a Pod stuck in Pending.
- Debug a container in CrashLoopBackOff.
- Resolve a registry authentication problem.
- Trace DNS and Service connectivity.
- Inspect Events and container logs.
- Use `kubectl get`, `describe`, `logs`, `exec`, `debug`, and `port-forward`.
- Simulate node NotReady and worker recovery.
- Restore from an etcd backup in a disposable lab cluster.
- Create a documented incident-resolution runbook.

### Module 11: Cluster Installation and Operations

**Topics**

- kubeadm and manual cluster setup
- Managed Kubernetes services
- Cluster upgrades
- Certificate and kubeconfig management
- Cluster networking and CNI operations
- Node and control plane maintenance
- Backup and restore
- etcd maintenance
- High availability
- Capacity planning
- Cloud controller and storage integrations

**Practical topics**

- Bootstrap a cluster with kubeadm in virtual machines.
- Join worker and control plane nodes.
- Upgrade one minor Kubernetes version in a lab.
- Renew or inspect certificates.
- Back up and restore etcd.
- Drain and uncordon nodes.
- Replace a failed worker node.
- Configure high availability for the control plane.

### Module 12: Extending Kubernetes

**Topics**

- Custom Resource Definitions
- Custom controllers
- Operators and reconciliation loops
- Kubernetes API aggregation
- Admission webhooks
- Finalizers
- Kubernetes client libraries
- Controller-runtime and Operator SDK concepts

**Practical topics**

- Create a CRD and custom resources.
- Write a basic controller or operator.
- Implement create, update, and delete reconciliation.
- Add status conditions and finalizers.
- Create a validating or mutating admission webhook.
- Build and deploy a controller image.

### Module 13: CI/CD and GitOps

**Topics**

- CI versus CD
- Container build and registry workflows
- Manifest and Helm validation
- Kubernetes deploy stages
- Progressive delivery
- Secrets in CI/CD
- Policy-as-code
- GitOps controllers
- Supply-chain provenance

**Practical topics**

- Build and publish a container image.
- Add YAML and Kubernetes manifest validation to CI.
- Run policy checks before deployment.
- Deploy with Argo CD or Flux.
- Promote releases between environments.
- Sign images and create a provenance attestation.
- Recover when a GitOps deployment fails.

### Module 14: Production-Ready Kubernetes

**Topics**

- High availability and disaster recovery
- Multi-cluster and multi-region design
- Cloud load balancers
- Cost optimization
- Multi-tenancy
- Capacity planning
- Cluster and Pod security
- Platform engineering
- Reliability engineering
- Compliance and governance

**Practical topics**

- Deploy the same application across namespaces or clusters.
- Configure Pod disruption budgets.
- Test application behavior during node loss.
- Enforce workload policy with an admission controller.
- Build a cost and capacity report.
- Create a backup, restore, upgrade, and incident runbook.
- Implement a production-readiness checklist.

## 4. Suggested 12-Week Learning Plan

| Week | Topic | Practical output |
|---|---|---|
| 1 | Foundations and local cluster | Working local cluster and a first Pod |
| 2 | Pods and workload controllers | Multi-container Deployment with probes |
| 3 | Services and networking | DNS, Service, and Ingress demo |
| 4 | Configuration and storage | Stateful app with ConfigMap, Secret, and PVC |
| 5 | Security and RBAC | Restricted workload with least-privilege access |
| 6 | Scheduling and resources | Quotas, limits, taints, and autoscaling |
| 7 | Helm and Kustomize | Environment-specific application releases |
| 8 | Observability | Metrics dashboard and alert rules |
| 9 | Troubleshooting | Debugged broken cluster scenarios |
| 10 | Cluster installation and upgrades | kubeadm cluster upgrade and backup |
| 11 | Operators and admission | Custom Resource and controller |
| 12 | GitOps and production design | End-to-end release and operations runbook |

Spend at least 60% of study time on hands-on practice. Rebuild each lab from YAML after first completing it with imperative commands.

## 5. Repository Structure

The repository is organized so each numbered module maps to one syllabus topic. Every module has its own `README.md`, practical lab instructions, and solution notes, plus runnable manifests or module-specific resources.

```text
kubernetes-tuts/
├── .github/
│   └── workflows/
│       └── validate-kubernetes.yml
├── 01-foundations/
│   ├── README.md
│   ├── manifests/
│   ├── labs/
│   └── solutions/
├── 02-pods-workloads/
│   ├── manifests/
│   └── labs/
├── 03-networking-services/
│   ├── manifests/
│   └── labs/
├── 04-config-secrets/
│   ├── manifests/
│   └── labs/
├── 05-storage/
│   ├── manifests/
│   └── labs/
├── 06-security-rbac/
│   ├── manifests/
│   └── labs/
├── 07-scheduling-resources/
│   ├── manifests/
│   └── labs/
├── 08-application-management/
│   ├── helm/
│   ├── kustomize/
│   └── labs/
├── 09-observability/
│   ├── manifests/
│   └── labs/
├── 10-troubleshooting/
│   ├── broken-manifests/
│   └── solutions/
├── 11-cluster-operations/
│   ├── kubeadm/
│   └── labs/
├── 12-extending-kubernetes/
│   ├── crd/
│   └── controller/
├── 13-cicd-gitops/
│   ├── pipelines/
│   └── gitops/
├── 14-production/
│   ├── manifests/
│   └── runbooks/
├── scripts/
├── diagrams/
└── README.md
```

The CI workflow checks the sample Helm chart and renders both Kustomize overlays on pushes and pull requests. See [Module 13](13-cicd-gitops/README.md) for the CI/CD and GitOps lab.

Recommended contents for each module:

- `README.md`: objective, prerequisites, commands, and cleanup steps.
- `manifests/`: Kubernetes YAML used by the lesson.
- `labs/`: step-by-step exercise instructions.
- `solutions/`: corrected manifests and expected results.
- `scripts/`: setup, validation, and cleanup automation.

Do not apply manifests without reading a lab's prerequisites. Labs should be run in disposable clusters unless the lab explicitly documents production-like requirements.

## 6. Repository Access Guide

### Clone with HTTPS

```bash
git clone https://github.com/anshoomishra/kubernetes-tuts.git
cd kubernetes-tuts
```

### Clone with SSH

```bash
git clone git@github.com:anshoomishra/kubernetes-tuts.git
cd kubernetes-tuts
```

### Browse the repository

- GitHub repository: `https://github.com/anshoomishra/kubernetes-tuts`
- HTTPS clone URL: `https://github.com/anshoomishra/kubernetes-tuts.git`
- SSH clone URL: `git@github.com:anshoomishra/kubernetes-tuts.git`

### Update a local copy

```bash
git switch main
git pull --ff-only origin main
```

### Create a topic branch

```bash
git switch -c topic/module-name
```

Example:

```bash
git switch -c topic/03-networking
```

### Run a module locally

```bash
cd 03-networking-services
kubectl apply -f manifests/
```

After the exercise:

```bash
kubectl delete -f manifests/
```

### Contribute

1. Fork the repository.
2. Create a topic branch.
3. Add or update the module's documentation and YAML.
4. Validate every manifest.
5. Test the exercise in a disposable Kubernetes cluster.
6. Commit and open a pull request.

## 7. Standard Lab Workflow

For every module:

1. Read the module `README.md`.
2. Verify the Kubernetes context.
3. Create the required namespace.
4. Review the manifests before applying them.
5. Apply resources in dependency order.
6. Verify Pods, Services, configuration, and logs.
7. Test the documented success criteria.
8. Complete the failure or troubleshooting exercise.
9. Run cleanup commands.
10. Record observations and commands in your notes.

Useful safety check:

```bash
kubectl config current-context
kubectl get nodes
kubectl get namespaces
```

## 8. Validation Commands

Validate a manifest before applying it:

```bash
kubectl apply --dry-run=client -f manifest.yaml
kubectl apply --dry-run=server -f manifest.yaml
```

Validate a complete directory:

```bash
kubectl apply --dry-run=client -f manifests/
```

Check resource status:

```bash
kubectl get all -A
kubectl get events -A --sort-by=.metadata.creationTimestamp
```

## 9. Cleanup

Remove resources created from a module directory:

```bash
kubectl delete -f manifests/
```

Delete a test namespace:

```bash
kubectl delete namespace <namespace-name>
```

Stop and remove a local `kind` cluster:

```bash
kind delete cluster
```

## 10. Certification-Oriented Topics

Use the syllabus as a preparation guide:

- **CKAD:** Pods, Deployments, Services, configuration, Jobs, probes, resources, and observability.
- **CKA:** cluster setup, upgrades, networking, storage, security, troubleshooting, and operations.
- **CKS:** least privilege, secure supply chain, runtime security, auditing, and cluster hardening.

Certification preparation should include time-boxed labs and troubleshooting without internet references.