## kubectl
```
kubectl run nginx
```
* Used to deploy an instance of the application (pod) 
* `--image=` flag is used to specify a docker image
___
```
kubectl cluster-info
```
* Displays information about the cluster
___

```
kubectl get nodes
```
* Lists all nodes part of a cluster 
```
kubectl get pods
```
* Lists all the pods
* `-o wide` option can be used to specify thr list of pods in a more detailed manner
___
```
kubectl describe pod <pod_name>
```
* Lists details about the pod
___
``` 
kubectl create -f <ymlfile>.yml
```
* Creates the k8 component from the yaml file
___

## minikube
```
minikube status
```
* Status of the minikube cluster
___

```
minikube start --driver=<driver>
```
* The driver can be docker, VirtualBox or ...
___

```
minikube stop
```
___

```
```
___