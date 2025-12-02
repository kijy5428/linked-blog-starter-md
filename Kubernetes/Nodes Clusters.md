### Nodes
- Where kubernetes got installed
- Physical / VM machines
- where containers are run
- ![](attachments/Pasted%20image%2020251106221456.png)

### Clusters
- A group of nodes form a cluster
- Can tolerate failure if one Node fails
- distribute loads as well
![](attachments/Pasted%20image%2020251106221548.png)
### Master
- Orchestrating all the containers on the worker nodes
	- ex: distributing the workloads to other nodes from failed nodes
- having 
	- kube-apiserver
	- etcd
	- controller
	- scheduller
![](attachments/Pasted%20image%2020251106221637.png)
![](attachments/Pasted%20image%2020251106223253.png) 
### Worker nodes
- where container get hosted
- has 
	- kubelet
	- container runtime
- carry out the action requested 

### Components
- API Server
	- Act as the front end for interaction with Kubernetes Cluster
- kubelet
- controller
	- Replication controller
- Container runtime
	- podman
	- ex: docker
- Scheduler
- etcd
	- key value store
- ![](attachments/Pasted%20image%2020251106222512.png)