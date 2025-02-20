# **Varnish Commands**

### **Start Varnish**
```bash
sudo systemctl start varnish
```

### **Stop Varnish**
```bash
sudo systemctl stop varnish
```

### **Restart Varnish**
```bash
sudo systemctl restart varnish
```

### **Enable Varnish to Start on Boot**
```bash
sudo systemctl enable varnish
```

### **Disable Varnish from Starting on Boot**
```bash
sudo systemctl disable varnish
```

### **Check Varnish Status**
```bash
sudo systemctl status varnish
```

### **Check Varnish Logs**
```bash
sudo journalctl -u varnish -f
```

### **Test Varnish Configuration for Errors**
```bash
varnishd -C -f /etc/varnish/default.vcl
```