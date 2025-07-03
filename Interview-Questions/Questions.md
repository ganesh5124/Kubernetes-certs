#### What is etcd, and what role does it play in a Kubernetes cluster?
* Etcd is a distributed key-value store that stores the configuration data of a Kubernetes cluster.
It is primarily used to store the state of the cluster and provides a reliable source of truth for cluster consistency. In a production environment, it is recommended to have an etcd cluster with a minimum of three nodes for high availability.

* A Service Mesh is a dedicated infrastructure
layer designed to manage service-to-service
communication within a Kubernetes cluster.
Service Meshes provide authentication,
authorization, and observability features for
distributed systems.

#### How does Kubernetes handle
load balancing and network
traffic routing?

* Kubernetes uses a Service object to handle load
balancing and network traffic routing. A Service
provides a single IP address and DNS name for
a set of pods and routes traffic to those pods
based on a set of rules defined by the user

#### what is configuration Map
* A configuration map, on the other hand, is
used to store configuration data that a pod or
container can consume

#### What is Heapster?
Heapster is a cluster-wide aggregator of data provided by Kubelet running on
each node. This container management tool is supported natively on
Kubernetes cluster and runs as a pod, just like any other pod in the cluster. So,
it basically discovers all nodes in the cluster and queries usage information
from the Kubernetes nodes in the cluster, via on-machine Kubernetes agent

## How can you switch to a specific namespace permanently in Kubernetes, so that you don't have to specify the namespace option each time you run a command?
* kubectl config set-context $(kubectl config current-context) --namespace=kube-system 
## Which approach is used to specify what actions should be performed in Kubernetes without specifying how they should be executed?
* Declarative approach
## Why is the "last applied configuration" feature useful in Kubernetes?
* It helps identify fields that have been removed from the local configuration file
## What is the difference between "Gigabyte (GB)" and "Gibibyte (GiB)" in terms of their size?
* Gigabyte(GB) refers to 1000Megabytes, while Gibibyte(GiB) refers to 1024 Mebibytes 
## What does the taint effect "NoExecute" indicate in Kubernetes?
* Pods will be evicted immediately from the node, if they do not tolerate the taint
## What is one way to manually assign a node to an existing pod in Kubernetes by mimicking the behavior of the scheduler?
* Create a binding object with the target node's name and send a post request to the pod's binding API
## What does the "isGateway" field in a Container Network Interface (CNI) plugin configuration file determine?
* Whether the bridge network should act as a gateway