
## **Nginx Commands**

### **Start Nginx**
```bash
brew services start nginx
```

### **Stop Nginx**
```bash
brew services stop nginx
```

### **Restart Nginx**
```bash
brew services restart nginx
```

### **Check Nginx Status**
```bash
brew services list
```

### **Test Nginx Configuration for Errors**
```bash
nginx -t
```

### **Reload Nginx Without Restarting**
```bash
nginx -s reload
```

### **Check Nginx Logs**
```bash
tail -f /usr/local/var/log/nginx/access.log
```
