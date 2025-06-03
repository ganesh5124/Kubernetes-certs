## How Nginx Virtual Servers Work
* When a request arrives, Nginx inspects the Host header (e.g., example.com, mail.example.com) and matches it against configured server blocks:

* Nginx listens on a port (80 or 443 by default).
* It checks the Host header.
* It routes the request to the server block with the matching server_name.
Whether you’re serving a blog, mail client, or map application, each domain or subdomain points to its own configuration within the same Nginx instance.


## Configuring a Basic Virtual Host

```
        server {
            listen       80;
            server_name  example.com www.example.com;


            root   /var/www/example.com/html;
            index  index.html;


            location / {
                try_files $uri $uri/ =404;
            }
        }
```
## Key directives:
### listen 80;
* Binds this block to port 80 (HTTP).
### server_name
* Lists domains and subdomains handled here.
### root
* Points to the document root where your site files live.
### index
* Specifies the default file to serve.
### location /
* Tries to serve the requested URI or returns 404 if not found.

## Binding to an IP address
```
            server {
                listen       80;
                server_name  172.217.22.14;


                root   /var/www/172.217.22.14/html;
                index  index.html;


                location / {
                    try_files $uri $uri/ =404;
                }
            }
```
## Serving on Different Port
```
            server {
                listen       8080;
                server_name  wiki.example.com;


                root   /var/www/wiki.example.com/html;
                index  index.html;


                location / {
                    try_files $uri $uri/ =404;
                }
            }
```

## Managing Multiple Server Blocks
```
        server {
            listen       80;
            server_name  honda.cars.com;


            root   /var/www/honda.cars.com/html;
            index  index.html;


            location / {
                try_files $uri $uri/ =404;
            }
        }


        server {
            listen       80;
            server_name  toyota.cars.com;


            root   /var/www/toyota.cars.com/html;
            index  index.html;

            location / {
                try_files $uri $uri/ =404;
            }
        }
```


















