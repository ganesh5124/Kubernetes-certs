* The kubelet uses liveness probes to know when to restart a container. 
* For example, liveness probes could catch a deadlock, where an application is running, but unable to make progress
* A common pattern for liveness probes is to use the same low-cost HTTP endpoint as for readiness probes, but with a higher failureThreshold
* The kubelet uses readiness probes to know when a container is ready to start accepting traffic
* LivenessProbe is a rich feature in Kubernetes that is used to check the health of your
application.
* Kubernetes by default doesn’t check the health check of the applications.
* If you want to use the livenessProve feature and want to check the health of your
application, you have to mention it in the manifest file