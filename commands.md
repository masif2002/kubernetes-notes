## kubectl
```
kubectl explain <resource>
```
* Displays documentation for a resource (pod, replicaset, deployment...)
___
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
kubectl describe replicaset <replicaset_name>
```
* Lists details about the pod, replicaset
___
``` 
kubectl create -f <ymlfile>.yml
```
* Creates the k8 objects specified in the yaml file
___
```
kubectl get replicationcontroller
```
* Displays the list of replication controllers
___

```
kubectl get replicaset
kubectl get rs
```
* Displays the list of replicasets
___
```
kubectl get all
```
* Displays all k8 objects
___
```
kubectl delete replicaset myapp-replicaset
```
* Deletes the replicaset
* `--all=true` flag deletes all the replicasets
```
kubectl replace -f <yamlfile>
```
* Replaces the resource's definition with the new definition
___
```
kubectl edit pod <pod_name>
```
* Used to edit live configuration of the pod that is active
___
```
kubectl scale --replicas=6 -f replicaset-def.yaml
OR
kubectl scale --replicas=6 replicaset myapp-replicaset
```
* Scales replicas to 6, but does not change the actual definition in the file
* `myapp-replicaset` is the name of the replicaset you define in your definition file
___
```
kubectl rollout status deployment/myapp-deployment
```
* Displays the rollout status of your deployment
___
```
kubectl rollout history deployment/myapp-deployment
```
* History of all the rollouts for your deployment
___
```
kubectl rollout undo deployment/myapp-deployment
```
* Undoes the previous deployment
___
```
kubectl set image deployment/myapp-deployment nginx-container=nginx:1.9.1
```
* This is how you set a new image for your deployment  
* Here, the image is being updated to nginx:1.9.1 for the container named _nginx-container_
___
```
kubectl apply -f <definition_file>
```
* Apply new changes to the resource
___
```
kubectl logs <pod_name>
```
* Displays the logs of the application container runnong inside the pod
___
```
kubectl exec -it <pod_name> -- /bin/bash 
```
* Terminal inside the container
___
```
```
___
```
```
___
```
```
___
```
```
___
```
```
___
```
```
___
```
```
___
```
```
___
> `--record` flag is used to record the changes made to k8 objects      
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
minikube service <name_of_k8_service> --url
```
* Gives the URL on which the service is accessible
___