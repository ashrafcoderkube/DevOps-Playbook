# **How to Use Nginx Load Balancer**

### **1. Test Load Balancer**
Access the load balancer from a web browser or use `curl`:
```powershell
curl -I http://localhost
```

### **2. Monitor Load Balancing in Real-Time**
To see which backend server is handling requests, check Nginx logs:
```powershell
type C:\nginx\logs\access.log
```

### **3. Add Health Checks for Backend Servers**
Modify `nginx.conf` to check if backend servers are healthy:
```nginx
upstream backend_servers {
    server 192.168.1.10:80 max_fails=3 fail_timeout=30s;
    server 192.168.1.11:80 max_fails=3 fail_timeout=30s;
}
```
Restart Nginx:
```powershell
taskkill /F /IM nginx.exe
start nginx
```
