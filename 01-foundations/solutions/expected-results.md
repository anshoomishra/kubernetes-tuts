# Module 1: Expected Results

## Cluster

`kubectl get nodes` should show the control-plane node and worker node in `Ready` status.

Example:

```text
NAME                                   STATUS   ROLES           AGE
kubernetes-foundations-control-plane   Ready    control-plane   1m
kubernetes-foundations-worker          Ready    <none>          1m
```

## Namespace

`kubectl get namespace foundations-lab` should show:

```text
NAME              STATUS   AGE
foundations-lab   Active   10s
```

## Pod

`kubectl get pods -n foundations-lab` should show:

```text
NAME        READY   STATUS    RESTARTS   AGE
hello-pod   1/1     Running   0          30s
```

The nginx container log should contain startup messages and worker-process information.

## API exploration

`kubectl api-resources` should include resources such as:

- `pods`
- `namespaces`
- `services`
- `deployments`
- `configmaps`
- `secrets`

`kubectl explain pod` should display the Pod API description.

## Port forwarding

The page available through `http://localhost:8080` should contain nginx's default welcome-page heading.
