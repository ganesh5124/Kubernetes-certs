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