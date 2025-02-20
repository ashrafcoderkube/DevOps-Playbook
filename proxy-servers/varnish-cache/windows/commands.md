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

### **Check Varnish Logs**
```bash
sudo journalctl -u varnish -f
```

### **Test Varnish Configuration for Errors**
```bash
varnishd -C -f /etc/varnish/default.vcl
```