# **Memcached Commands**

### **Start Memcached**
```bash
sudo systemctl start memcached
```

### **Stop Memcached**
```bash
sudo systemctl stop memcached
```

### **Restart Memcached**
```bash
sudo systemctl restart memcached
```

### **Enable Memcached to Start on Boot**
```bash
sudo systemctl enable memcached
```

### **Disable Memcached from Starting on Boot**
```bash
sudo systemctl disable memcached
```

### **Check Memcached Status**
```bash
sudo systemctl status memcached
```

### **Check Memcached Logs**
```bash
tail -f /var/log/memcached.log
```

### **Check Memcached Statistics**
```bash
echo stats | nc localhost 11211
```
