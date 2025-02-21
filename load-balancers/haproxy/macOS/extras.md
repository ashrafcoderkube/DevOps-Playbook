# **How to Use HAProxy**

### **1. Test Load Balancer**
Access the load balancer from a web browser or use `curl`:
```bash
curl -I http://localhost
```

### **2. Monitor Load Balancing in Real-Time**
To see which backend server is handling requests, check HAProxy logs:
```bash
tail -f /usr/local/var/log/haproxy.log
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
Restart HAProxy and access stats at `http://localhost:8080/stats`.
