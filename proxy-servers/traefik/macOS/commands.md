# **Traefik Commands**

### **Start Traefik**
```bash
brew services start traefik
```

### **Stop Traefik**
```bash
brew services stop traefik
```

### **Restart Traefik**
```bash
brew services restart traefik
```

### **Check Traefik Logs**
```bash
tail -f /usr/local/var/log/traefik.log
```

### **Test Traefik Configuration for Errors**
```bash
traefik check-config --configFile=/usr/local/etc/traefik.yml
```
