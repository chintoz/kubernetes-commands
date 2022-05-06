# Kubernetes Basics
There are several basic concepts to be considered in Kubernetes:

* **Control Plane**: There are some servers encharged of coordinate the kubernetes cluster
* **Nodes**: Machines with the kubelet agent running on them and the kube-proxy which is responsible for managing networking traffic for pods inside the node.
* **Scheduler**: TBC
* **ETCD**: Database which contains information about the kubernetes cluster state.
* **Cloud Controller Manager**: TBC
* **Controller Manager**: TBC
* **Namespace**: It's a kind of logical division inside a kubernetes cluster. It's a way to keep pod/deployment/service/ingress ordered. There are some namespaces created by default in kubernetes for internal purpose. Even there is a namespace called and configured as default. If no namespace is specified, elements will be assigned to the default one.

The client to access to a kubernetes cluster, it's needed ```kubectl``` client`.

There are several ways to install kubernetes cluster in local environment:

1. Install a kubernetes cluster from as an external cluster. For instance: minikube.
2. Use the existing embedded cluster in Docker Desktop application.

# Kubernetes Utility Commands

## Client commands
There are several interesting commands to manage our kubernetes cluster.

How to retrieve information about the kubectl client version
```shell
kubectl version --client=true
```

## Contexts

You could have several context files configured in your local environment. You can list them using the following command

```shell
kubectl config get-contexts
```
Even you can change the context using the following command

```shell
kubectl config set-context minikube
```

## Namespaces

The way to query all namespaces is using the following command (```ns``` could be replaced by ```namespace``` in all commands):

```shell
kubectl get ns
```

There are several namespaces created by default in kubernetes for internal purpose.

TBC

# Kubernetes Examples

TBC

# References

* Youtube video tutorial: https://www.youtube.com/watch?v=DCoBcpOA7W4
* Kubernetes reference documentation: https://kubernetes.io/es/docs/reference/
* 