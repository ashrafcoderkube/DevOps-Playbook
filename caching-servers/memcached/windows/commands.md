# **Memcached Commands**

### **Start Memcached**
```powershell
net start memcached
```

### **Stop Memcached**
```powershell
net stop memcached
```

### **Restart Memcached**
```powershell
net stop memcached
net start memcached
```

### **Check Memcached Status**
```powershell
sc query memcached
```

### **Check Memcached Statistics**
```powershell
echo stats | nc localhost 11211
```
