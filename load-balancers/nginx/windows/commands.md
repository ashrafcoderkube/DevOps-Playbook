# **Nginx Commands**

### **Start Nginx**
```powershell
start nginx
```

### **Stop Nginx**
```powershell
taskkill /F /IM nginx.exe
```

### **Restart Nginx**
```powershell
taskkill /F /IM nginx.exe
start nginx
```

### **Check Nginx Configuration for Errors**
```powershell
ginx -t
```

### **Reload Nginx Without Restarting**
```powershell
ginx -s reload
```

### **Check Nginx Logs**
```powershell
type C:\nginx\logs\access.log
```
