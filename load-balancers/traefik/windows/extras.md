# **How to Use Traefik Load Balancer**

### **1. Test Load Balancer**
Access the load balancer from a web browser or use `curl`:
```powershell
curl -I http://example.com
```

### **2. Monitor Load Balancing in Real-Time**
To see which backend server is handling requests, check Traefik logs:
```powershell
type C:\Traefik\traefik.log
```

### **3. Add SSL with Let's Encrypt**
Modify `traefik.yml` to enable Let's Encrypt:
```yaml
certificatesResolvers:
  myresolver:
    acme:
      email: "admin@example.com"
      storage: "C:\\Traefik\\acme.json"
      httpChallenge:
        entryPoint: web
```
Restart Traefik:
```powershell
taskkill /F /IM traefik.exe
traefik.exe --configFile=C:\Traefik\traefik.yml
```
