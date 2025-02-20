# Traefik Proxy Server Configuration on macOS

## **Configuration**

### **1. Create a Basic Traefik Configuration File**
Create the file `/usr/local/etc/traefik.yml`:
```bash
nano /usr/local/etc/traefik.yml
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
    directory: "/usr/local/etc/traefik/conf.d"
    watch: true
```
Save and exit the file.

### **2. Start and Enable Traefik**
```bash
brew services start traefik
```

### **3. Verify Service Status**
```bash
brew services list
```


## **Troubleshooting**

- **Traefik Service Not Starting**:
  ```bash
  brew services restart traefik
  ```
- **Check Traefik Configuration for Errors**:
  ```bash
  traefik check-config --configFile=/usr/local/etc/traefik.yml
  ```
- **Clients Cannot Connect to Traefik**:
  - Ensure Traefik is listening:
    ```bash
    netstat -an | grep 80
    ```
  - Check firewall rules:
    ```bash
    sudo pfctl -sr | grep 80
    ```
