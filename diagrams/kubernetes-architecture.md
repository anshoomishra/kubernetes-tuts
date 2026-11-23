# Kubernetes Architecture Diagram

```text
                 Operators and users
                         |
                    kubectl / API
                         |
               +---------v----------+
               |     API Server     |
               +--+-------+-------+-+
                  |       |       |
               +--v--+ +--v---+ +-v----------------+
               | etcd| |Sched.| |Controller Manager|
               +-----+ +------+ +-----------------+
                         |
          +--------------+-----------------+
          |                                |
   +------v------------------+    +--------v-----------------+
   | Worker node             |    | Worker node              |
   | kubelet + runtime       |    | kubelet + runtime        |
   | kube-proxy / CNI        |    | kube-proxy / CNI         |
   | Pods and volumes        |    | Pods and volumes         |
   +-------------------------+    +--------------------------+
```

The API server is the control-plane entry point. Controllers reconcile observed state toward declared desired state; the scheduler selects nodes for unscheduled Pods. Kubelets run assigned Pods through the node's container runtime. Networking and persistent storage are supplied by cluster plugins and integrations.
