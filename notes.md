## Containers Overview
* In Linux, the various flavours are nothing but different softwares on top of a common OS kernel
* So, containers of any linux distro can be run on top of a linux distro
* But containers of other OS like windows cannot be launched on top of Linux as the host OS, because Windows will use a different OS kernel to interact with the hardware 

### Containers vs VM
![](img/convm.png)
* VMs don't rely on the underlying OS or Kernel. So, they can have any OS
* Hypervisor is used for virtualization

## Kubernetes
* Kuberenetes is a container orchestration technology. It is used to manage and deploy containers and scale according to needs
### Terminology
- **Nodes** 
    * A machine that has kubernetes installed
    * A worker machine that launches containers 
    * Previously known as minions
![](img/nodes.png)
> Kubernetes is also called K8
- **Cluster** 
    * A group of nodes with a master node. Other nodes are also referred as slave/worker nodes
        * A master node watches over the worker nodes and is responsible for ochestration of the containers in those nodes
    * Even if a node fails in your cluster, your application is still accessible from the other nodes
    * Having multiple nodes help in sharing load aswell

### Components

When you install kubernetes, it comes along with:
* **API Server** 
    * The frontend. The CLI, UI .. all talk to the API to interact with k8 cluster  
* **etcd** 
    * Used to store Key-values. Contains info that is used to manage the cluster
* **Scheduler**
    * Responsible for distributing containers across multiple nodes
* **Controller**
    * Responsible for monitoring the nodes, containers and endpoints. Launches new units if the current one goes down
* **Container Runtime**
    * The underlying software that is used to launch containers (Docker) 
* **Kubelet** 
    * The agent that runs on each node in the cluster. Responsible for making sure the containers are running on the nodes as expected

![](img/components.png)

### Master vs Worker Nodes
![](img/mvw.png)
* A node running the _API server_ makes it a master node and the node running the _kubelet_ agent makes it a worker node

### kubectl
* CTL stands for control/command-line-tool
* Command Line tool deploying and managing application on a kubernetes cluster

## Pods
* A pod is a kubernetes object that holds the container. So, a pod is an instance of your application
![](img/pods.png)
* To scale up, you add more pods (instances of your app) to your node
![](img/scalepods.png)
### Multi-container pods
* You generally don't, but CAN have more than one container in a pod
* Usually these containers would be helping containers for your main application (maybe like a MySQL container for your app)
* Containers within a pod share same volume (storage) and are a part of same network space, so can communciate with each other
![](img/mcpods.png)

## YAML
![](img/yaml.png)
![](img/uo.png)

## YAML in K8
```yaml
apiVersion:
kind:
metadata:
spec:
```
* These four are the required fields for a k8 configuration file
    * `kind` is the kind of component you are creating - a pod, replicaset, or ...
    * `metadata` can have only the fields expected by k8. We cannot add our own
    * `spec` is the specification for your component
    * `apiVersion` is the api version according to the _kind_ of component

![](img/akms.png)

### Sample YAML file
```yml
apiVersion: v1
kind: Pod
metadata:
    name: myapp-pod
    labels:
        app: myapp
        type: front-end
spec:
    containers:
        -   name: nginx-container
            image: nginx
```
* Use `kubectl create -f <yamlfile>` or `kubectl apply -f <yamlfile>` command to create the pod