# **Memcached Commands**

### **Start Memcached**
```bash
brew services start memcached
```

### **Stop Memcached**
```bash
brew services stop memcached
```

### **Restart Memcached**
```bash
brew services restart memcached
```

### **Check Memcached Logs**
```bash
tail -f /usr/local/var/log/memcached.log
```

### **Check Memcached Status**
```bash
brew services list
```

### **Check Memcached Statistics**
```bash
echo stats | nc localhost 11211
```
