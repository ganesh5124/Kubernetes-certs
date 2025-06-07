## How can you switch to a specific namespace permanently in Kubernetes, so that you don't have to specify the namespace option each time you run a command?
* kubectl config set-context $(kubectl config current-context) --namespace=kube-system 
## Which approach is used to specify what actions should be performed in Kubernetes without specifying how they should be executed?
* Declarative approach
## Why is the "last applied configuration" feature useful in Kubernetes?
* It helps identify fields that have been removed from the local configuration file