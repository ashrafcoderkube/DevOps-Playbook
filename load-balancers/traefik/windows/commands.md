# **Traefik Commands**

### **Start Traefik**
```powershell
traefik.exe --configFile=C:\Traefik\traefik.yml
```

### **Check Traefik Version**
```powershell
traefik version
```

### **Restart Traefik**
Stop the running process and restart it:
```powershell
taskkill /F /IM traefik.exe
traefik.exe --configFile=C:\Traefik\traefik.yml
```

### **View Traefik Logs**
```powershell
type C:\Traefik\traefik.log
```

### **Enable Traefik Dashboard**
The dashboard can be accessed at:
```
http://localhost:8080/dashboard/
```
