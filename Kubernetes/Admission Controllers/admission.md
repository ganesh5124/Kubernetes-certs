## Overview of Admission Controllers
* Admission Controllers are plugins that intercept requests to the Kubernetes API server before persisting an object. They are categorized into two main types:

### Validating Admission Controllers:
* These controllers examine incoming requests and reject them if they do not conform to specified policies. For example, a namespace existence validator checks if the requested namespace exists; if it doesn't, the request is rejected.

### Mutating Admission Controllers:
* These controllers modify incoming requests prior to their persistence. A common example is the default storage class admission controller. When you create a PersistentVolumeClaim (PVC) without specifying a storage class, this controller automatically adds the default storage class to the request.

