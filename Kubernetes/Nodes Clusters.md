### Nodes
- Physical / VM machines
- where containers are run

### Clusters
- A group of nodes form a cluster
- distribute loads as well

### Master
- Orchestrating all the containers on the worker nodes
- having 
	- kube-apiserver
	- etcd
	- controller
	- scheduller

### Worker nodes
- has 
	- kubelet
	- container runtime
- carry out the action requested 

### Components
- API Server
	- Act as the front end for interaction with Kubernetes Cluster
- kubelet
- controller
- Container runtime
	- 
	- ex: docker
- Scheduler
- etcd
	- key value store