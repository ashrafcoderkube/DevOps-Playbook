# **How to Use HAProxy**

### **1. Set Up HAProxy as an HTTP Load Balancer**
- Ensure backend servers are running on `192.168.1.10:80` and `192.168.1.11:80`.
- Configure HAProxy as shown in the **Configuration** section.
- Restart HAProxy:
  ```bash
  sudo systemctl restart haproxy
  ```
- Test load balancing:
  ```bash
  curl -I http://localhost
  ```

### **2. Enable HTTPS Support**
To enable SSL termination, install an SSL certificate and modify `haproxy.cfg`:
```ini
frontend https_front
    bind *:443 ssl crt /etc/haproxy/certs/mycert.pem
    default_backend https_back

backend https_back
    balance roundrobin
    server server1 192.168.1.10:443 check ssl verify none
    server server2 192.168.1.11:443 check ssl verify none
```
Restart HAProxy:
```bash
sudo systemctl restart haproxy
```

### **3. Enable HAProxy Statistics Web Interface**
Add this to `haproxy.cfg`:
```ini
listen stats
    bind *:8080
    stats enable
    stats uri /stats
    stats refresh 10s
    stats auth admin:password
```
Restart HAProxy and access stats at `http://server-ip:8080/stats`.
