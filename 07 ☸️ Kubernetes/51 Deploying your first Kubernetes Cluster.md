### What is Minikube?

> quickly sets up a local Kubernetes cluster on macOS, Linux, and Windows

[Installation](https://minikube.sigs.k8s.io/docs/start/) 

### Getting a Kubernetes cluster up and running

run `minikube start` to deploy your first Kubernetes cluster
![[Pasted image 20221107135833.png]]
`minikube addons list` to check addons
![[Pasted image 20221107140023.png]]

I am also defining in our project some additional configuration, apiserver is set to 6433 instead of a random API port, and I define the container runtime also to containerd however docker is default and CRI-O is also available. I am also setting a specific Kubernetes version.

![[Pasted image 20221107140829.png]]


### What is kubectl?

[installation](https://kubernetes.io/docs/tasks/tools/install-kubectl-macos/#install-with-homebrew-on-macos)
[Overview of kubectl](https://kubernetes.io/docs/reference/kubectl/overview/) 

kubectl is a cli that is used or allows you to interact with Kubernetes clusters
We use kubectl to deploy applications and inspect and manage cluster resources. 

### kubectl cheat sheet

[Unofficial Kubernetes](https://unofficial-kubernetes.readthedocs.io/en/latest/)

![[Pasted image 20221107141455.png]]![[Pasted image 20221107141504.png]]

