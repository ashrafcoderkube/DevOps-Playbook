# Traefik Proxy Server Configuration on Windows

## **Configuration**

### **1. Create a Basic Traefik Configuration File**
Create a new configuration file `C:\traefik\traefik.yml`:
```powershell
mkdir C:\traefik
notepad C:\traefik\traefik.yml
```

Add the following basic configuration:
```yaml
entryPoints:
  web:
    address: ":80"
  websecure:
    address: ":443"

api:
  dashboard: true
  insecure: true

providers:
  file:
    directory: "C:/traefik/conf.d"
    watch: true
```
Save and close the file.

### **2. Run Traefik**
Start Traefik with the configuration file:
```powershell
traefik --configFile=C:\traefik\traefik.yml
```

### **3. Verify Service Status**
Traefik should now be running. Open a web browser and go to:
```
http://localhost:8080/dashboard/
```

## **Troubleshooting**

- **Traefik Service Not Starting**:
  ```powershell
  traefik --configFile=C:\traefik\traefik.yml
  ```
- **Check Traefik Configuration for Errors**:
  ```powershell
  traefik check-config --configFile=C:\traefik\traefik.yml
  ```
- **Clients Cannot Connect to Traefik**:
  - Ensure Traefik is listening:
    ```powershell
    netstat -ano | findstr :80
    ```
  - Check Windows Firewall rules:
    ```powershell
    netsh advfirewall firewall add rule name="Allow Traefik" dir=in action=allow protocol=TCP localport=80
    ```