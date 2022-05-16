# Kubernetes Basics
There are several basic concepts to be considered in Kubernetes:

* **Control Plane**: There are some servers encharged of coordinate the kubernetes cluster
* **Nodes**: Machines with the kubelet agent running on them and the kube-proxy which is responsible for managing networking traffic for pods inside the node.
* **Scheduler**: TBC
* **ETCD**: Database which contains information about the kubernetes cluster state.
* **Cloud Controller Manager**: TBC
* **Controller Manager**: TBC
* **Namespace**: It's a kind of logical division inside a kubernetes cluster. It's a way to keep pod/deployment/service/ingress ordered. There are some namespaces created by default in kubernetes for internal purpose. Even there is a namespace called and configured as default. If no namespace is specified, elements will be assigned to the default one.
* **Pod**: A pod is a set of containers. Generally, a pod usually runs one container, but it could run several.
* **Deployment**: A template to generate pods.

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

## PODs

The way to query the pods belonging to a namespace

```shell
kubectl get pod -n <namespace_name>
```

If we want to display additional information about pods we could use the same command with the option `wide` to display additional columns:

```shell
kubectl get pod -n <namespace_name> -o wide
```

It's going to display internal IP, cluster node which is running the pod, etc..

If we want to delete a pod from the cluster, the command to be used

```shell
kubectl delete pod <pod_name> -n <namespace_name>
```
If we have configured a minimum set of pods deployed, it could be recreated a new pod to replace the deleted one.

# Kubernetes Examples

## Example one - Deploy a pod

We could use the YAML file to describe a POD to be deployed. This is the simplest way to create a POD.

In the following examples we are going to see Deployment structure which offers a richer way to declare PODs. However, in this example we can see the most simple one.

Starting from this YAML file manifest to describe a POD:

TBC - Link to the repo with the manifest

# References

* Youtube video tutorial: https://www.youtube.com/watch?v=DCoBcpOA7W4
* Kubernetes reference documentation: https://kubernetes.io/es/docs/reference/
* 