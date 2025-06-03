## Package Manager of Operating Systems

Operating System	    Package Manager	        Install Nginx Command
Ubuntu	                    APT	                sudo apt update && sudo apt install nginx
CentOS/RHEL	                YUM or DNF	        sudo yum install epel-release && sudo yum install nginx
macOS	                    Homebrew	        brew update && brew install nginx
Windows (WSL)	            APT	                sudo apt update && sudo apt install nginx

## Core Component of Nginx
* Nginx configuration by exploring the nginx.conf file—typically located at (/etc/nginx/nginx.conf) on Linux systems

### At a glance, an nginx.conf file is divided into four main sections:

* Global settings:Define user permissions, worker processes, PID file location, compression, caching, and more.
* events block: Controls Nginx’s event model and the maximum number of simultaneous connections per worker.
* http block: Contains HTTP directives for logging, timeouts, compression, MIME types, and includes for server blocks.
* server block: Configures how Nginx responds to requests for specific domain names or IP addresses (virtual hosts).

### Server blocks, or virtual hosts, let you host multiple domains on one Nginx instance. Incoming requests are routed to the matching block based on server_name or IP address.

## Nginx Directory Structure
Path	                            Description
/etc/nginx/nginx.conf	            Main configuration file
/etc/nginx/sites-available/	        Store individual server block files
/etc/nginx/sites-enabled/	        Symbolic links to enabled sites from sites-available
/etc/nginx/conf.d/	                Additional configuration snippets (e.g., SSL, load balancing)
/var/www/...	                    Default web content roots (Debian/Ubuntu)
/usr/share/nginx/html	            Default web root (RHEL/CentOS)
/etc/nginx/mime.types	            MIME type definitions
/run/nginx.pid	                    PID file location
/var/log/nginx/	                    Access and error logs

## Essential Nginx Commands
Command	                Description
nginx -h	            Display help and available options
nginx -v	            Show Nginx version
nginx -V	            Show version and compile-time options
nginx -t	            Check configuration syntax and validity
nginx -T	            Dump complete configuration for review
nginx -s reload	        Reload configuration without downtime
nginx -s stop	        Graceful shutdown
nginx -s quit	        Immediate shutdown
nginx -s reopen	        Reopen log files
sudo systemctl reload nginx	        Reload using systemd (graceful)
sudo systemctl restart nginx	    Restart Nginx (brief downtime possible)
sudo systemctl status nginx	        Check Nginx service status

## Firewall
* A firewall is a security barrier—hardware or software—between your system and the Internet. It inspects and filters incoming and outgoing traffic, blocking unauthorized access while permitting legitimate communication.

## Port
* A port is a logical communication endpoint—think of it as a “door” or “window” in your network. Each service listens on a specific port number.

* Using firewald we can achieve allow/deny specific ports to our application
```
    sudo yum update && sudo yum install firewalld Install (if needed):
    sudo systemctl start firewalld
    sudo systemctl enable firewalld         Start and enable at boot:
    sudo firewall-cmd --permanent --add-port=80/tcp         Open port permanently (e.g., HTTP)
    sudo firewall-cmd --reload
    sudo firewall-cmd --permanent --remove-port=80/tcp      remove port permanently (e.g., HTTP)
    sudo firewall-cmd --reload
    sudo firewall-cmd --list-all                            Check active zones and ports
    sudo netstat -nltup                                     lists active connections and listening ports
```


