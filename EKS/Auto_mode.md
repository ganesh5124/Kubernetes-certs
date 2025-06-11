## EKS Auto Mode
* EKS Auto Mode extends AWS management of Kubernetes clusters beyond the cluster itself, to allow AWS to also set up and manage the infrastructure that enables the smooth operation of your workloads

### Features
* Streamline Kubernetes Cluster Management
* Efficiency
* Application Availability
* Security
* Automated Upgrades
* Managed Components
* Customizable NodePools and NodeClasses

```
    Create eks auto mode cluster
    eksctl create cluster --name=<cluster-name> --enable-auto-mode
```

* The purpose of the system node pool is to segregate critical add-ons onto different nodes. 
* Nodes provisioned by the system node pool have a CriticalAddonsOnly Kubernetes taint. 
* Kubernetes will only schedule pods onto these nodes if they have a corresponding toleration













