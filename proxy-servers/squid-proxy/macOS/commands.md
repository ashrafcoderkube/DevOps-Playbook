# **Squid Commands**

### **Start Squid**
```bash
brew services start squid
```

### **Stop Squid**
```bash
brew services stop squid
```

### **Restart Squid**
```bash
brew services restart squid
```

### **Check Squid Logs**
```bash
tail -f /usr/local/var/logs/squid/access.log
```

### **Reload Squid Configuration Without Restarting**
```bash
squid -k reconfigure
```

### **Test Squid Configuration for Errors**
```bash
squid -k parse
```
