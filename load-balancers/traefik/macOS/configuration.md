## Traefik Load Balancer Configuration on macOS

## **Configuration**

### **1. Create Traefik Configuration File**
Create a new configuration file:
```bash
mkdir -p ~/.config/traefik
nano ~/.config/traefik/traefik.yml
```

### **2. Basic Load Balancing Configuration**
Add the following content to `traefik.yml`:
```yaml
entryPoints:
  web:
    address: ":80"

providers:
  file:
    filename: "~/.config/traefik/dynamic.yml"

api:
  dashboard: true
  insecure: true
```
Save and exit the file.

### **3. Define Backend Services**
Create the `dynamic.yml` file:
```bash
nano ~/.config/traefik/dynamic.yml
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
```bash
traefik --configFile=~/.config/traefik/traefik.yml
```

## **Troubleshooting**

- **Traefik Not Starting**:
  ```bash
  pkill traefik
  traefik --configFile=~/.config/traefik/traefik.yml
  ```
- **Check Traefik Logs**:

  ```bash
  tail -f ~/.config/traefik/traefik.log
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