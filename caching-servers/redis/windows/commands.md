# **Redis Commands**

### **Start Redis**
```powershell
redis-server
```

### **Stop Redis**
```powershell
taskkill /F /IM redis-server.exe
```

### **Restart Redis (Memurai)**
```powershell
net stop memurai
net start memurai
```

### **Check Redis Logs (WSL)**
```bash
tail -f /var/log/redis/redis-server.log
```

### **Connect to Redis CLI**
```powershell
redis-cli
```

### **Test Redis Connection**
```powershell
redis-cli ping
```

### **Check Redis Memory Usage**
```powershell
redis-cli info memory
```

---
