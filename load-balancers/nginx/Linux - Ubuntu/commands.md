# **Nginx Commands**

### **Start Nginx**
```bash
sudo systemctl start nginx
```

### **Stop Nginx**
```bash
sudo systemctl stop nginx
```

### **Restart Nginx**
```bash
sudo systemctl restart nginx
```

### **Enable Nginx to Start on Boot**
```bash
sudo systemctl enable nginx
```

### **Disable Nginx from Starting on Boot**
```bash
sudo systemctl disable nginx
```

### **Check Nginx Status**
```bash
sudo systemctl status nginx
```

### **Test Nginx Configuration for Errors**
```bash
sudo nginx -t
```

### **Reload Nginx Without Restarting**
```bash
sudo systemctl reload nginx
```

### **Check Nginx Logs**
```bash
tail -f /var/log/nginx/access.log
```
