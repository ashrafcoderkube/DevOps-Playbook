# **Redis Commands**

### **Start Redis**
```bash
brew services start redis
```

### **Stop Redis**
```bash
brew services stop redis
```

### **Restart Redis**
```bash
brew services restart redis
```

### **Check Redis Status**
```bash
brew services list
```

### **Check Redis Logs**
```bash
tail -f /usr/local/var/log/redis.log
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