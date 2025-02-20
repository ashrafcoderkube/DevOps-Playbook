# **Varnish Commands**

### **Start Varnish**
```bash
brew services start varnish
```

### **Stop Varnish**
```bash
brew services stop varnish
```

### **Restart Varnish**
```bash
brew services restart varnish
```

### **Check Varnish Logs**
```bash
tail -f /usr/local/var/log/varnish/varnish.log
```

### **Test Varnish Configuration for Errors**
```bash
varnishd -C -f /usr/local/etc/varnish/default.vcl
```
