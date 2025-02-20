# **How to Use Traefik**

### **1. Set Up a Reverse Proxy for a Web Service**
Create a new configuration file:
```powershell
notepad C:\traefik\conf.d\myservice.yml
```

Add the following:
```yaml
http:
  routers:
    myservice:
      rule: "Host(`mydomain.com`)"
      service: myservice
      entryPoints:
        - web
  services:
    myservice:
      loadBalancer:
        servers:
          - url: "http://192.168.1.100:80"
```
Restart Traefik for changes to take effect:
```powershell
traefik --configFile=C:\traefik\traefik.yml
```

### **2. Enable HTTPS with Let's Encrypt**
Modify `C:\traefik\traefik.yml`:
```yaml
certificatesResolvers:
  myresolver:
    acme:
      email: "admin@mydomain.com"
      storage: "C:/traefik/acme.json"
      httpChallenge:
        entryPoint: web
```
Restart Traefik:
```powershell
traefik --configFile=C:\traefik\traefik.yml
```
