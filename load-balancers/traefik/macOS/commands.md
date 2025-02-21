# **Traefik Commands**

### **Start Traefik**
```bash
traefik --configFile=~/.config/traefik/traefik.yml
```

### **Check Traefik Version**
```bash
traefik version
```

### **Restart Traefik**
Stop the running process and restart it:
```bash
pkill traefik
traefik --configFile=~/.config/traefik/traefik.yml
```

### **View Traefik Logs**
```bash
tail -f ~/.config/traefik/traefik.log
```

### **Enable Traefik Dashboard**
The dashboard can be accessed at:
```
http://localhost:8080/dashboard/
```
