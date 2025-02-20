
# **Squid Commands**

### **Start Squid**
```bash
sudo systemctl start squid
```

### **Stop Squid**
```bash
sudo systemctl stop squid
```

### **Restart Squid**
```bash
sudo systemctl restart squid
```

### **Enable Squid to Start on Boot**
```bash
sudo systemctl enable squid
```

### **Disable Squid from Starting on Boot**
```bash
sudo systemctl disable squid
```

### **Check Squid Status**
```bash
sudo systemctl status squid
```

### **Check Squid Logs**
```bash
tail -f /var/log/squid/access.log
```

### **Reload Squid Configuration Without Restarting**
```bash
sudo squid -k reconfigure
```

### **Test Squid Configuration for Errors**
```bash
sudo squid -k parse
```