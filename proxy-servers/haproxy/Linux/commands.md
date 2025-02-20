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

### **Enable HAProxy to Start on Boot**
```bash
sudo systemctl enable haproxy
```

### **Disable HAProxy from Starting on Boot**
```bash
sudo systemctl disable haproxy
```

### **Check HAProxy Status**
```bash
sudo systemctl status haproxy
```

### **Check HAProxy Logs**
```bash
tail -f /var/log/haproxy.log
```

### **Test HAProxy Configuration for Errors**
```bash
sudo haproxy -c -f /etc/haproxy/haproxy.cfg
```