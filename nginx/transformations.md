## URL Redirect and Rewrite
* Redirect (return) issues an HTTP status code (e.g., 301) back to the client and changes what appears in their browser’s address bar.
* Rewrite silently alters the URI before Nginx processes it, keeping the user’s URL intact.

1. Entire Domain Redirect
nginx redirects helps forward requests form an old domain URL to a new one

```
        server {
            listen       80;
            server_name  honda.cars.com;


            return 301 https://cars.honda.com$request_uri;


            root  /var/www/example.com/html;
            index index.html;


            location / {
                try_files $uri $uri/ =404;
            }
        }
```
2. HTTP traffic to HTTPS Redirect


![alt text](image.png)

3.3. Regex Cheat Sheet
Symbol	Description	Example
^	Start of string	^/old matches /old
$	End of string	/page$ matches /page
.	Any single character	a.b matches acb
*	Zero or more of the preceding token	.* captures anything
[]	Character class	[a-z]
()	Capture group	(.*)


## Rewrite Directive
```
    server {
            listen 80;
            server_name example.com;
            root /var/www/html;


            index index.html index.htm index.nginx-debian.html;


            location / {
                # Redirect all /images/... requests to /pics/...
                rewrite ^/images/(.*)$ /pics/$1 permanent;


                # Then attempt to serve the request
                try_files $uri $uri/ =404;
            }
        }
```
* Using Nginx’s rewrite directive with regular expressions allows seamless URL remapping and preserves SEO by issuing 301 redirects. Always:

* Validate your Nginx configuration (nginx -t)
* Reload Nginx to apply changes
* Test rewrites in a staging environment








