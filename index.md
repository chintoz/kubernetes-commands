# Kubernetes Basics
There are several basic concepts to be considered in Kubernetes:

* **Control Plane**: There are some servers encharged of coordinate the kubernetes cluster
* **Nodes**: Machines with the kubelet agent running on them and the kube-proxy which is responsible for managing networking traffic for pods inside the node.
* **Scheduler**: TBC
* **ETCD**: Database which contains information about the kubernetes cluster state.
* **Cloud Controller Manager**: TBC
* **Controller Manager**: TBC

The client to access to a kubernetes cluster, it's needed ```kubectl``` client`.

There are several ways to install kubernetes cluster in local environment:

1. Install a kubernetes cluster from as an external cluster. For instance: minikube.
2. Use the existing embedded cluster in Docker Desktop application.

# Kubernetes Utility Commands

There are several interesting commands to manage our kubernetes cluster.

How to retrieve information about the kubectl client version
```shell
> kubectl version --client=true
```

TBC

# Kubernetes Examples

TBC