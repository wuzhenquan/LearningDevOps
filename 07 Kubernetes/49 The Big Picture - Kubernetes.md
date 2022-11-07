




![[Pasted image 20221107094320.png]]
### Main Kubernetes Components

### Node

#### Control Plane
Every Kubernetes cluster requires a **Control Plane node**

#### Worker Node

#### kubelet

#### kube-proxy

#### Container runtime

### Cluster
A cluster is a group of nodes, each nodes 都包含
- container runtime(Docker)
- will be running a kubelet service (is an agent that takes in the commands from the Master controller)
- a Proxy (used to proxy connections to the [[#Pods]] from another component(Services))

#### Kube API-Server

#### Scheduler

#### Controller Manager

#### etcd

#### kubectl

### Pods

### Deployments

### ReplicaSets

### StatefulSets

### DaemonSets

### Services






