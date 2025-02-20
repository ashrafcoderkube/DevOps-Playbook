# **HAProxy Commands**

### **Start HAProxy**
```bash
sudo systemctl start haproxy
```

### **Stop HAProxy**
```bash
sudo systemctl stop haproxy
```

### **Restart HAProxy**
```bash
sudo systemctl restart haproxy
```

### **Check HAProxy Status**
```bash
sudo systemctl status haproxy
```

### **Test HAProxy Configuration for Errors**
```bash
haproxy -c -f /etc/haproxy/haproxy.cfg
```
