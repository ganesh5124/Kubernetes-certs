* ResourceQuota is one of the rich features of Kubernetes that helps to manage and distribute
resources according to the requirements

### Race Conditions
* If the requests and limits are given in the manifest file, it works accordingly.
* If the requests are given but the limit is not provided then, the default limit will be used.
* If the requests are not provided but the limit is provided then, the requests will be equal
to the limit.