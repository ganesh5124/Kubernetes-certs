### What is HPA?
* HPA automatically scales the number of Pods in a Kubernetes workload (e.g., Deployment, StatefulSet) horizontally based on resource metrics.
* Targets metrics like CPU, memory, or custom/external metrics.

### How It Works
* Runs a control loop every 15 seconds (default).
#### Fetches metrics from:
* metrics.k8s.io (via Metrics Server)
* custom.metrics.k8s.io
* external.metrics.k8s.io
```
Calculates:

desiredReplicas = ceil(currentReplicas × currentMetric / targetMetric)
```


Feature	            Vertical Pod Autoscaling (VPA)	                         Horizontal Pod Autoscaling (HPA)
Scaling Method	    Adjusts CPU and memory settings of individual pods (may restart pods for changes).          
                                                                             Increases or decreases the number of pods to distribute load.
Pod Behavior	    May cause temporary downtime during pod restarts.	      Scales pods seamlessly without interrupting existing ones.
Traffic Handling	Less effective for sudden spikes due to restart delays.	  Ideal for handling rapid traffic spikes by adding more pods instantly.
Cost Optimization	Prevents over-provisioning by matching resource allocation with actual usage.	
                                                                            Reduces operational costs by avoiding underutilized pods.
Use Cases	Stateful workloads, databases, JVM-based applications, and AI workloads requiring precise tuning.	                                                                   Stateless applications, web services, and microservices requiring rapid scaling.


