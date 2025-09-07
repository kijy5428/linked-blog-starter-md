### CRI
- Container runtime interface
- Defined by kubernetes 
- Container runtime which follows this standard could be used within Kubernetes

### OCI
- Open Container initiaitve
- imagespec
	-define how image is built
- runtimespec
	- define how runtime shoudl be developed

### Docker
- used to be the only supported container runtime in Kubernetes
- later Kubernetes use dockershim to support the docker container runtime
- 
### dockershim
- provided by kubernetes to adpat to support docker

### containerD
- A runtime that could be installed independently from docker
- CRI compatible
- the daemon for runc
- Could be used separately from docker

### runc
- Container runtime provided within docker

### Debugging tools
- nerdctl / ctr
	- Support containerD
- crictl (across different CRI compatible runtime)
	- support all CRI

![](attachments/Pasted%20image%2020250907001622.png)