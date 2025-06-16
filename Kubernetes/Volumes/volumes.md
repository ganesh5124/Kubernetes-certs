* Kubernetes volumes provide a way for containers in a pod to access and share data via the filesystem
## emptyDir Volume (in simple terms)
* It’s a temporary storage volume that is created when a Pod starts.
* It’s empty at first, hence the name emptyDir.
* It lives as long as the Pod lives — once the Pod is deleted, the data inside emptyDir is gone too