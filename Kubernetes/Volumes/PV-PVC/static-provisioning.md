## PV and PVC
* A PersistentVolume (PV) is a piece of storage in the cluster that has been provisioned by an administrator or dynamically provisioned using Storage Classes
* A PersistentVolumeClaim (PVC) is a request for storage by a user. It is similar to a Pod. Pods consume node resources and PVCs consume PV resources
* Claims can request specific size and access modes (e.g., they can be mounted ReadWriteOnce, ReadOnlyMany, ReadWriteMany, or ReadWriteOncePod)

### Lifecycle of a volume and claim
* PVs are resources in the cluster. PVCs are requests for those resources and also act as claim checks to the resource
### Provisioning
* There are two ways PVs may be provisioned: statically or dynamically.
### Static
* A cluster administrator creates a number of PVs. They carry the details of the real storage, which is available for use by cluster users. They exist in the Kubernetes API and are available for consumption.
* The PVC must request a storage class and the administrator must have created and configured that class for dynamic provisioning to occur

### Binding
* A PVC to PV binding is a one-to-one mapping, using a ClaimRef which is a bi-directional binding between the PersistentVolume and the PersistentVolumeClaim.
* If a user deletes a PVC in active use by a Pod, the PVC is not removed immediately. 
* PVC removal is postponed until the PVC is no longer actively used by any Pods
* If an admin deletes a PV that is bound to a PVC, the PV is not removed immediately. PV removal is postponed until the PV is no longer bound to a PVC.

### Reclaiming
#### Retain
* The Retain reclaim policy allows for manual reclamation of the resource. When the PersistentVolumeClaim is deleted, the PersistentVolume still exists and the volume is considered "released". 
* But it is not yet available for another claim because the previous claimant's data remains on the volume
#### In this case the admin will need to do below things
* Delete the PersistentVolume. The associated storage asset in external infrastructure still exists after the PV is deleted.
* Manually clean up the data on the associated storage asset accordingly.
* Manually delete the associated storage asset.

### Delete (default for dynamic provisioning)
* When the PVC is deleted:
* The associated PV is deleted
* The underlying storage (disk) is also deleted
* Good for temporary or disposable data.

### Recycle (deprecated)
* Was used to wipe and reuse volumes automatically.

* A volume with volumeMode: Filesystem is mounted into Pods into a directory. If the volume is backed by a block device and the device is empty, Kubernetes creates a filesystem on the device before mounting it for the first time.

* volumeMode to Block to use a volume as a raw block device. Such volume is presented into a Pod as a block device, without any filesystem on it

### AccessModes
#### ReadWriteOnce
* the volume can be mounted as read-write by a single node. ReadWriteOnce access mode still can allow multiple pods to access (read from or write to) that volume when the pods are running on the same node
#### ReadOnlyMany
* the volume can be mounted as read-only by many nodes.
#### ReadWriteMany
* the volume can be mounted as read-write by many nodes.
#### ReadWriteOncePod
* the volume can be mounted as read-write by a single Pod. Use ReadWriteOncePod access mode if you want to ensure that only one pod across the whole cluster can read that PVC or write to it