# **Traefik Commands**

### **Start Traefik**
```bash
sudo traefik --configFile=/etc/traefik/traefik.yml
```

### **Check Traefik Version**
```bash
traefik version
```

### **Restart Traefik**
Stop the running process and restart it:
```bash
pkill traefik
sudo traefik --configFile=/etc/traefik/traefik.yml
```

### **View Traefik Logs**
```bash
journalctl -u traefik -f
```

### **Enable Traefik Dashboard**
The dashboard can be accessed at:
```
http://localhost:8080/dashboard/
```