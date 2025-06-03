## TLS/SSL Certificates
* When users connect to a web server, TLS certificates encrypt communication and verify the server’s identity. 
* Without secure connectivity, sensitive data—such as online banking credentials—could be transmitted in plaintext, making it vulnerable to interception and misuse. 
* Encryption transforms readable data (plaintext) into ciphertext, ensuring that intercepted data remains unreadable if decryption keys are protected.
* Data encryption typically involves keys, sets of random characters that facilitate the transformation of plaintext into ciphertext. 
* In symmetric encryption, the same key is used for both encryption and decryption. This method risks key interception if the key travels over the same network channel.
* To mitigate this risk, asymmetric encryption is employed. This method uses a key pair: a private key kept secret and a public key that anyone can use to encrypt data. 
* Data encrypted with the public key can only be decrypted using the private key, ensuring secure communication even if the public key is known.

## Securing SSH with Key Pairs
* Securing SSH access to servers is a common use case for key pairs. Instead of traditional passwords—which are prone to compromise—you generate a pair of keys. 
* The public key is placed on the server, while the private key remains with you, ensuring that only you can access the server.
```
    command to create public and private ssh key pairs ==> ssh-keygen
```
This creates two files:

* id_rsa: the private key
* id_rsa.pub: the public key

## Securing Web Servers with TLS
* Using only symmetric encryption for a web server poses a risk because the encryption key must be transmitted over the network. 
* Asymmetric encryption resolves this by securely transmitting a symmetric key between the client and server.
* For HTTPS, when a user visits a website, the server sends its public key within an SSL/TLS certificate. Even if an attacker intercepts the public key, they cannot decrypt the symmetric key because only the server holds the corresponding private key.
* Use OpenSSL to generate a pair of RSA keys for your web server
```
    openssl genrsa -out my-bank.key 1024
    openssl rsa -in my-bank.key -pubout > mybank.pem
```

### When a user connects:

* The server sends its public key embedded in a certificate.
* The browser encrypts a newly generated symmetric key with this public key.
* The server uses its private key to decrypt the symmetric key.
* Future communication is secured using the symmetric key.

## The Role of Digital Certificates
* Digital certificates serve as more than just containers for public keys. They provide essential details including:

* Certificate owner's identity (subject)
* Issuer’s identity
* Validity dates
* Subject Alternative Names (SANs) for multiple domain support

### Certificate Example
```
    Certificate:
    Data:
        Serial Number: 420327018966204255
        Signature Algorithm: sha256WithRSAEncryption
        Issuer: CN=kubernetes
        Validity
            Not After : Feb  9 13:41:28 2020 GMT
        Subject: CN=my-bank.com
        X509v3 Subject Alternative Name:
            DNS:mybank.com, DNS:i-bank.com,
            DNS:we-bank.com,
        Subject Public Key Info:
            00:b9:b0:55:24:fb:a4:ef:77:73:7c:9b
```

## Certifying Trust with Certificate Authorities
* While anyone can create a certificate (including fraudulent ones), trusted Certificate Authorities (CAs) such as Symantec, DigiCert, Komodo, or GlobalSign play a vital role in establishing trust.
* Generate a Certificate Signing Request (CSR) using your private key and domain name:

```
    openssl req -new -key my-bank.key -out my-bank.csr -subj "/C=US/ST=CA/O=MyOrg, Inc./CN=my-bank.com"
```
* Submit the CSR to a CA.
* The CA verifies your information and, once validated, signs your certificate.
* The signed certificate is returned and installed on your server, ensuring that browsers trust your website.


* This complete framework, which includes CAs, key pairs, digital certificates, and database practices for key management, is known as Public Key Infrastructure (PKI).

* Certificates that include a public key typically use the extensions .crt or .pem (for example, server.crt, server.pem, client.crt, or client.pem). 
* Private keys are usually indicated by the extension .key or may include the word “key” in the filename (e.g., server.key or server-key.pem).

## TLS in Kubernetes
* Server Certificates: Deployed on servers.
* Root Certificates: Held by the Certificate Authority (CA) to sign server certificates.
* Client Certificates: Used by clients to authenticate themselves to the server.

### TLS Components in Kubernetes Cluster
* A secure Kubernetes cluster requires encrypted TLS communications between the master and worker nodes. Whether you are an administrator using kubectl or an internal service within the cluster, every interaction relies on TLS-secured connections. There are two main requirements:

* Server components (e.g., API server, etcd, kubelet) must use TLS certificates to secure communications.
* Client components (e.g., administrative users, scheduler, controller-manager, kube-proxy) must present valid client certificates for authentication.

## Server Certificates

### Kube API Server:
* The Kube API server provides an HTTPS service for internal components and external users. It requires a server certificate and a private key (api-server.cert and api-server.key) to secure these communications.

### etcd Server:
* Acting as the primary data store for the cluster, the etcd server necessitates its certificate and key pair, named etcd-server.crt and etcd-server.key.

### Kubelet (Worker Nodes):
* Every worker node runs the kubelet service, which exposes an HTTPS API endpoint for communication with the API server. For these endpoints, a certificate and key pair (kubelet.cert and kubelet.key) is used.

## Client Certificates
### Admin User:
* Administrators connect to the Kubernetes cluster via kubectl or direct REST API calls. The admin user authenticates with a client certificate (admin.crt) and corresponding key (admin.key).

### Scheduler:
* The scheduler queries the API server for pending pods and orchestrates their deployment on the appropriate worker nodes. It uses a certificate and key pairing (scheduler.cert and scheduler.key) for authentication.

### Kube Controller Manager:
* Similar to the scheduler, the controller manager communicates with the API server using its own certificate for secure authentication.

### Kube Proxy:
* The kube proxy manages network rules on worker nodes and requires a dedicated client certificate (kube-proxy.crt and kube-proxy.key).
![alt text](image.png)







