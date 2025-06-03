## Cloud Security
* The first “C” is cloud security, which focuses on protecting the overall infrastructure—be it a public cloud, private cloud, on-premises data center, or co-located environment.
* The infrastructure hosting the Kubernetes cluster was insufficiently secured, permitting unrestricted access to cluster ports. 
* Without proper network firewalls, remote access from the attacker’s system was easily achieved.

## Cluster Security
* The attacker compromised the system by exploiting a publicly accessible Docker daemon and an unsecured Kubernetes dashboard that lacked proper authentication and authorization measures.
* To secure your cluster:
* Follow best practices to protect the Docker daemon.
* Secure the Kubernetes API by enforcing strong access controls.
* Restrict dashboard access with proper authentication.
* Implement network policies and ingress security for additional safeguard measures

## Container Security
* Enforce policies that allow only images from secure, trusted repositories.
* Disallow privileged mode for containers.
* Use container sandboxing to provide an additional layer of security.

## Code Security
* Not adding secrets in code level
* Proper configuration is need to be used
* Using hashing for security

![alt text](image.png)