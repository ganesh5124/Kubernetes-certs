## Load Balancer
* A load balancer is a network device—software or hardware—that distributes incoming traffic across multiple backend servers. It prevents any single server from becoming a performance bottleneck or single point of failure.

### Use Case
* Nginx not only distributes traffic but also performs health checks on backend servers. When a node fails, Nginx automatically marks it unhealthy and stops sending traffic its way, keeping your site available on remaining nodes.

```
    upstream backend {
        server 10.10.0.101:80;
        server 10.10.0.102:80;
        server 10.10.0.103:80;
    }


    server {
        listen 80;
        server_name example.com www.example.com;


        location / {
            proxy_pass http://backend;
        }
    }
```

## Load Balancing Methods
1. Round Robin : distributes traffic in a circular fashion
2. weighted Round-Robin: Assign heavier weights to more powerful servers so they receive a larger share of traffic.
3. IP Hash ( Sticky Sessions ): Ensures the same client IP always hits the same server—ideal for session persistence when data is stored in memory on each backend.
4. Least Connections: Routes each new request to the server with the fewest active connections—ideal for dynamic workloads.
5. Least Time: Selects the backend with the fastest response time—either time to first byte or last byte

* Allow load balancer Ip in that server
```
    ufw allow from 192.230.202.10 proto tcp to any port 80
```

## Reverse Proxy
* A reverse proxy sits between clients and one or more backend servers. It receives incoming requests, routes them to the appropriate server pool, and returns the server’s response to the client.
* Hiding backend server identities
* SSL/TLS offloading
* Caching static assets
* Distributing traffic across multiple application servers

































