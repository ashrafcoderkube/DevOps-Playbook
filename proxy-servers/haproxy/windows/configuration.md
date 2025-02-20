# HAProxy Server Configuration on Windows

## **Configuration**

### **1. Modify HAProxy Configuration File**
The HAProxy configuration file is located at `/etc/haproxy/haproxy.cfg` in WSL or Cygwin.

Edit the file using:
```bash
nano /etc/haproxy/haproxy.cfg
```

### **2. Basic Load Balancing Configuration**
Add the following configuration to balance traffic between two backend servers:
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


## **Troubleshooting**

- **HAProxy Service Not Starting**:
  ```bash
  sudo systemctl restart haproxy
  ```
- **Check HAProxy Configuration for Errors**:
  ```bash
  haproxy -c -f /etc/haproxy/haproxy.cfg
  ```
- **Clients Cannot Connect to HAProxy**:
  - Ensure HAProxy is listening:
    ```bash
    netstat -an | grep 80
    ```
  - Check firewall rules:
    ```powershell
    netsh advfirewall firewall add rule name="Allow HAProxy" dir=in action=allow protocol=TCP localport=80
    ```