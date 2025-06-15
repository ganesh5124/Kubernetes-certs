## HTTPS
## Headers
## Authentication


* Used to check logs of apache
```
    sudo tail -f /var/log/apache2/access.log
```

## HTTPS in Nginx
* When you access a website via HTTPS, all communication between your browser and the server is encrypted. On an unencrypted connection (HTTP), anyone on the same network—such as a coffee shop Wi-Fi—could intercept your passwords, credit-card numbers, or personal details
* With HTTP, data is sent in plain text. An attacker can easily read it.
* With HTTPS, intercepted data is encrypted and unreadable.

* Seo Benefits: Search engines like Google prioritize secure sites in search rankings. Enabling HTTPS not only protects user data but also improves your site’s visibility and trustworthiness.

### SSL and TLS Protocols
* SSL (Secure Sockets Layer) and TLS (Transport Layer Security) are cryptographic protocols that secure data in transit. Although we still colloquially call them “SSL certificates,” modern sites use TLS under the hood.
* Your browser connects to the server over HTTPS
* The server responds by sending its TLS certificate, which includes its public key and identity details.
* A trusted CA—like Let’s Encrypt, DigiCert, or Comodo—verifies the domain owner and signs the certificate.
* Your browser checks that the certificate matches the domain (e.g., https://onlinestore.com), ensuring you’re communicating with the real site.
* TLS employs asymmetric encryption (public-key cryptography), similar to SSH. A public key encrypts data, and only the corresponding private key can decrypt it.


