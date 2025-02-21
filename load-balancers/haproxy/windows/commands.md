# **HAProxy Commands**

### **Start HAProxy**
```powershell
haproxy.exe -f C:\haproxy\haproxy.cfg
```

### **Stop HAProxy**
```powershell
taskkill /F /IM haproxy.exe
```

### **Restart HAProxy**
```powershell
taskkill /F /IM haproxy.exe
haproxy.exe -f C:\haproxy\haproxy.cfg
```

### **Check HAProxy Logs**
```powershell
type C:\haproxy\haproxy.log
```

### **Test HAProxy Configuration for Errors**
```powershell
haproxy.exe -c -f C:\haproxy\haproxy.cfg
```