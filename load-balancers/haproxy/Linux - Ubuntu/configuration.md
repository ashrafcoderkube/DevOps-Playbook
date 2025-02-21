# Haproxy Load Balancer Configuration on Linux & Ubuntu

## **Configuration**

### **1. Modify HAProxy Configuration File**
The HAProxy configuration file is located at `/etc/haproxy/haproxy.cfg`.

Edit the file using:
```bash
sudo nano /etc/haproxy/haproxy.cfg
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
sudo systemctl restart haproxy
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
sudo systemctl restart haproxy
```

## **Troubleshooting**

- **HAProxy Service Not Starting**:
  ```bash
  sudo systemctl restart haproxy
  sudo journalctl -u haproxy --no-pager
  ```
- **Check HAProxy Configuration for Errors**:
  ```bash
  haproxy -c -f /etc/haproxy/haproxy.cfg
  ```
- **Clients Cannot Connect to HAProxy**:
  - Ensure HAProxy is listening:
    ```bash
    sudo netstat -tulnp | grep haproxy
    ```
  - Check firewall rules:
    ```bash
    sudo ufw allow 80/tcp
    sudo ufw allow 443/tcp
    ```
