# **Squid Commands**

### **Start Squid**
```powershell
net start squid
```

### **Stop Squid**
```powershell
net stop squid
```

### **Restart Squid**
```powershell
net stop squid
net start squid
```

### **Check Squid Logs**
```powershell
type C:\Squid\var\logs\access.log
```

### **Reload Squid Configuration Without Restarting**
```powershell
squid -k reconfigure
```

### **Test Squid Configuration for Errors**
```powershell
squid -k parse
```
