# **How to Use Traefik Load Balancer**

### **1. Test Load Balancer**
Access the load balancer from a web browser or use `curl`:
```bash
curl -I http://example.com
```

### **2. Monitor Load Balancing in Real-Time**
To see which backend server is handling requests, check Traefik logs:
```bash
journalctl -u traefik -f
```

### **3. Add SSL with Let's Encrypt**
Modify `traefik.yml` to enable Let's Encrypt:
```yaml
certificatesResolvers:
  myresolver:
    acme:
      email: "admin@example.com"
      storage: "/etc/traefik/acme.json"
      httpChallenge:
        entryPoint: web
```
Restart Traefik:
```bash
sudo systemctl restart traefik
```
