### Nodes
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
- having 
	- kube-apiserver
	- etcd
	- controller
	- scheduller
![](attachments/Pasted%20image%2020251106221637.png)

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