# **Traefik Commands**

### **Start Traefik**
```bash
sudo systemctl start traefik
```

### **Stop Traefik**
```bash
sudo systemctl stop traefik
```

### **Restart Traefik**
```bash
sudo systemctl restart traefik
```

### **Enable Traefik to Start on Boot**
```bash
sudo systemctl enable traefik
```

### **Disable Traefik from Starting on Boot**
```bash
sudo systemctl disable traefik
```

### **Check Traefik Logs**
```bash
journalctl -u traefik -f
```

### **Test Traefik Configuration for Errors**
```bash
traefik check-config --configFile=/etc/traefik/traefik.yml
```
