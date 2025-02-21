# Haproxy Load Balancer Configuration on macOS

## **Configuration**

### **1. Modify HAProxy Configuration File**
The HAProxy configuration file is located at `/usr/local/etc/haproxy.cfg`.

Edit the file using:
```bash
nano /usr/local/etc/haproxy.cfg
```

### **2. Basic Load Balancing Configuration**
Add the following configuration:
```ini
defaults
    log     global
    mode    http
    timeout connect 5000ms
    timeout client 50000ms
    timeout server 50000ms

frontend http_front
    bind *:80
    default_backend http_back

backend http_back
    balance roundrobin
    server server1 192.168.1.10:80 check
    server server2 192.168.1.11:80 check
```
Restart HAProxy for changes to take effect:
```bash
brew services restart haproxy
```

### **3. Configure Load Balancing Algorithm (Optional)**
- **Least Connections**:
  ```ini
  balance leastconn
  ```
- **Source IP Hashing**:
  ```ini
  balance source
  ```
Restart HAProxy after making changes:
```bash
brew services restart haproxy
```

## **Troubleshooting**

- **HAProxy Service Not Starting**:
  ```bash
  brew services restart haproxy
  ```
- **Check HAProxy Configuration for Errors**:
  ```bash
  haproxy -c -f /usr/local/etc/haproxy.cfg
  ```
- **Clients Cannot Connect to HAProxy**:
  - Ensure HAProxy is listening:
    ```bash
    netstat -an | grep 80
    ```
  - Check firewall rules:
    ```bash
    sudo pfctl -sr | grep 80
    ```
