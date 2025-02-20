# **Redis Commands**

### **Start Redis**
```bash
sudo systemctl start redis
```

### **Stop Redis**
```bash
sudo systemctl stop redis
```

### **Restart Redis**
```bash
sudo systemctl restart redis
```

### **Enable Redis to Start on Boot**
```bash
sudo systemctl enable redis
```

### **Disable Redis from Starting on Boot**
```bash
sudo systemctl disable redis
```

### **Check Redis Status**
```bash
sudo systemctl status redis
```

### **Check Redis Logs**
```bash
tail -f /var/log/redis/redis-server.log
```

### **Connect to Redis CLI**
```bash
redis-cli
```

### **Test Redis Connection**
```bash
redis-cli ping
```

### **Check Redis Memory Usage**
```bash
redis-cli info memory
```
