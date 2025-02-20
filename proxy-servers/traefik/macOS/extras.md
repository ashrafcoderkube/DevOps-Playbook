# **How to Use Traefik**

### **1. Access the Traefik Dashboard**
- Open a web browser and go to `http://localhost:8080/dashboard/`.

### **2. Set Up a Reverse Proxy for a Web Service**
Create a new configuration file:
```bash
nano /usr/local/etc/traefik/conf.d/myservice.yml
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
```bash
brew services restart traefik
```

### **3. Enable HTTPS with Let's Encrypt**
Modify `/usr/local/etc/traefik.yml`:
```yaml
certificatesResolvers:
  myresolver:
    acme:
      email: "admin@mydomain.com"
      storage: "/usr/local/etc/traefik/acme.json"
      httpChallenge:
        entryPoint: web
```
Restart Traefik:
```bash
brew services restart traefik
```
