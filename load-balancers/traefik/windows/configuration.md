## Traefik Load Balancer Configuration on Windows

## **Configuration**

### **1. Create Traefik Configuration File**
Create a new configuration file:
```powershell
notepad C:\Traefik\traefik.yml
```

### **2. Basic Load Balancing Configuration**
Add the following content to `traefik.yml`:
```yaml
entryPoints:
  web:
    address: ":80"

providers:
  file:
    filename: "C:\\Traefik\\dynamic.yml"

api:
  dashboard: true
  insecure: true
```
Save and exit the file.

### **3. Define Backend Services**
Create the `dynamic.yml` file:
```powershell
notepad C:\Traefik\dynamic.yml
```
Add the following configuration:
```yaml
http:
  routers:
    my-router:
      rule: "Host(`example.com`)"
      service: my-service
  services:
    my-service:
      loadBalancer:
        servers:
          - url: "http://192.168.1.10:80"
          - url: "http://192.168.1.11:80"
```
Save and exit the file.

### **4. Start Traefik**
Run Traefik with the following command:
```powershell
traefik.exe --configFile=C:\Traefik\traefik.yml
```


## **Troubleshooting**

- **Traefik Not Starting**:
  ```powershell
  taskkill /F /IM traefik.exe
  traefik.exe --configFile=C:\Traefik\traefik.yml
  ```
- **Check Traefik Logs**:

  ```powershell
  type C:\Traefik\traefik.log
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