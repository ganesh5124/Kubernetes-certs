* A web server combines hardware and software to process client requests and serve web content—HTML, CSS, JavaScript, images, and more—back to your browser.

* The browser queries the DNS (Domain Name System) to resolve the domain name into an IP address.
* After obtaining the IP, it establishes a TCP connection to the server.
* The server receives the HTTP/HTTPS request, gathers the requested assets, and sends a response back.
* Your browser renders the response, displaying the web page.

## web servers communicate two main protocols
* HTTP (HyperText Transfer Protocol) – unencrypted
* HTTPS (HTTP Secure) – encrypted with TLS/SSL

```
    Transmitting sensitive information over plain HTTP can expose data to eavesdropping and man-in-the-middle attacks. Always prefer HTTPS
```

```
    Web Server	    First Released	    Concurrency Model	                    Key Benefit
    Nginx	        2004	            Event-driven, async	           Low memory footprint, high concurrency
    OpenResty	    2011	            Nginx + Lua modules	            Extensible with Lua scripting
    LiteSpeed	    2003	            Event-driven	                Drop-in Apache replacement option
    Caddy	        2015	            Event-driven, Go	            Automatic HTTPS distribution
```

* NGINX is a high-performance web server first released over 20 years ago. It’s available in two editions: the open source Community Edition and the commercial NGINX Plus. 
* NGINX powers static content delivery, load balancing, reverse proxy, and more—across Linux, macOS, and Windows.

### Asynchronous, Event-Driven Architecture
* One of NGINX’s key innovations is handling 10,000+ concurrent connections with minimal overhead. This makes it ideal for serving static assets—HTML, images, audio, and video—more efficiently than traditional, process-based servers.
* NGINX processes multiple client requests within a single worker process using non-blocking I/O.

```
    Feature	                    NGINX	                    Apache
    Architecture	            Asynchronous, event-driven	Process/thread-based
    Max. concurrent             connections	≥10,000	Varies, lower throughput
    CPU & memory usage	        Low	                        Higher
    Static content performance	Excellent	Good
```
### Event-Driven Architecture Overview
* Imagine stepping into a busy coffee shop:
    * One barista takes orders.
    * Another barista prepares drinks.
    * Neither barista waits idle—they coordinate tasks asynchronously.
* Like that coffee shop, Nginx decouples request acceptance from request processing. It listens for new events, delegates work, and immediately returns to watching for additional activity.
* Nginx uses non-blocking I/O and a single-threaded event loop per worker to juggle connections efficiently:

## In Nginx terms, each HTTP request follows these steps:

### Incoming Request
* The client issues an HTTP/S request.
### Event Loop
* Nginx accepts the connection and returns immediately to monitor other events.
### Processing Event
* The worker reads files, queries databases, or proxies to an upstream server. If I/O is required, it switches context to serve another request.
### Response Sent
* Once processing completes, Nginx replies to the client and continues the loop.

### Step-by-Step Flow
* Accept: New connection arrives.
* Register: Connection is added to the event loop.
* Dispatch: Worker processes available events.
* I/O Wait: If blocked, event loop switches to another request.
* Complete: Response is sent when processing is done.

### Nginx uses master-worker Architecture 
### Master Process
* Supervises worker lifecycle
* Reloads configuration without downtime
* Never blocks on I/O or client handling
### Worker Processes
* Each runs an independent, single-threaded event loop
* Handles connection acceptance, reading, writing, and multiplexing
* Scales across CPU cores by running multiple workers

## Use Cases
* Distributing requests for high availability
* Offloading SSL/TLS and request routing
* Caching responses to cut backend load
* Controlling outbound traffic and anonymizing clients

Features
* Load Balancing
* Reverse/Forward Proxy
* Caching




