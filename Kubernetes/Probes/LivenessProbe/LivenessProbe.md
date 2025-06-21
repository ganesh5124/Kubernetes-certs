* The kubelet uses liveness probes to know when to restart a container. 
* For example, liveness probes could catch a deadlock, where an application is running, but unable to make progress
* A common pattern for liveness probes is to use the same low-cost HTTP endpoint as for readiness probes, but with a higher failureThreshold
* The kubelet uses readiness probes to know when a container is ready to start accepting traffic
