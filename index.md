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

There is a command to apply configuration to kubernetes cluster. We can apply any configuration defined in a YAML file in kubernetes

```shell
kubectl apply -f <path_to_file> -n <namespace_name>
```

# Kubernetes Examples

## Example one - Deploy a pod

We could use the YAML file to describe a POD to be deployed. This is the simplest way to create a POD.

In the following examples we are going to see Deployment structure which offers a richer way to declare PODs. However, in this example we can see the most simple one.

Starting from this YAML file manifest to describe a POD:

https://github.com/chintoz/kubernetes-commands/blob/main/Example1/pod.yaml

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: nginxpod
spec:
  containers:
    - name: nginxcontainer
      image: nginx:alpine
```

With this manifest file we are able to create a POD which is called `nginxpod` which contains a container called `nginxcontainer `.

To be able to deploy in our cluster we can do it using the following command:

```shell
kubectl apply -f pod.yaml -n default
```
Once it's created we can describe the pod created with the command

```shell
kubectl describe pod nginxpod -n default
```

It'll display information about the pod like this:

```shell
Name:         nginxpod
Namespace:    default
Priority:     0
Node:         minikube/172.26.71.12
Start Time:   Mon, 16 May 2022 23:17:32 +0200
Labels:       <none>
Annotations:  <none>
Status:       Running
IP:           172.17.0.3
IPs:
  IP:  172.17.0.3
Containers:
  nginxcontainer:
    Container ID:   docker://ce51fa873c7fb4036006abcbbea5c953b20dd2657acd767b3037762fbe802a26
    Image:          nginx:alpine
    Image ID:       docker-pullable://nginx@sha256:5a0df7fb7c8c03e4158ae9974bfbd6a15da2bdfdeded4fb694367ec812325d31
    Port:           <none>
    Host Port:      <none>
    State:          Running
      Started:      Mon, 16 May 2022 23:17:33 +0200
    Ready:          True
    Restart Count:  0
    Environment:    <none>
    Mounts:
      /var/run/secrets/kubernetes.io/serviceaccount from kube-api-access-2hgzh (ro)
Conditions:
  Type              Status
  Initialized       True
  Ready             True
  ContainersReady   True
  PodScheduled      True
Volumes:
  kube-api-access-2hgzh:
    Type:                    Projected (a volume that contains injected data from multiple sources)
    TokenExpirationSeconds:  3607
    ConfigMapName:           kube-root-ca.crt
    ConfigMapOptional:       <nil>
    DownwardAPI:             true
QoS Class:                   BestEffort
Node-Selectors:              <none>
Tolerations:                 node.kubernetes.io/not-ready:NoExecute op=Exists for 300s
                             node.kubernetes.io/unreachable:NoExecute op=Exists for 300s
Events:
  Type    Reason     Age   From               Message
  ----    ------     ----  ----               -------
  Normal  Scheduled  16s   default-scheduler  Successfully assigned default/nginxpod to minikube
  Normal  Pulled     15s   kubelet            Container image "nginx:alpine" already present on machine
  Normal  Created    15s   kubelet            Created container nginxcontainer
  Normal  Started    15s   kubelet            Started container nginxcontainer
```

## Example Two - TBC

TBC

# References

* Youtube video tutorial: https://www.youtube.com/watch?v=DCoBcpOA7W4
* Kubernetes reference documentation: https://kubernetes.io/es/docs/reference/
* 