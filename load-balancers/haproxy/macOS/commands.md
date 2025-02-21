# **HAProxy Commands**

### **Start HAProxy**
```bash
brew services start haproxy
```

### **Stop HAProxy**
```bash
brew services stop haproxy
```

### **Restart HAProxy**
```bash
brew services restart haproxy
```

### **Check HAProxy Status**
```bash
brew services list
```

### **Check HAProxy Logs**
```bash
tail -f /usr/local/var/log/haproxy.log
```

### **Test HAProxy Configuration for Errors**
```bash
haproxy -c -f /usr/local/etc/haproxy.cfg
```
