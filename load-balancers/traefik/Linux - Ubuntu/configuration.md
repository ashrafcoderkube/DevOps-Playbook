## Traefik Load Balancer Configuration on Linux & Ubuntu

## **Configuration**

### **1. Create Traefik Configuration File**
Create a new directory and configuration file:
```bash
sudo mkdir -p /etc/traefik
sudo nano /etc/traefik/traefik.yml
```

### **2. Basic Load Balancing Configuration**
Add the following content to `traefik.yml`:
```yaml
entryPoints:
  web:
    address: ":80"

providers:
  file:
    filename: "/etc/traefik/dynamic.yml"

api:
  dashboard: true
  insecure: true
```
Save and exit the file.

### **3. Define Backend Services**
Create the `dynamic.yml` file:
```bash
sudo nano /etc/traefik/dynamic.yml
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
sudo traefik --configFile=/etc/traefik/traefik.yml
```

## **Troubleshooting**

- **Traefik Not Starting**:
  ```bash
  sudo systemctl restart traefik
  journalctl -u traefik --no-pager
  ```
- **Check Traefik Logs**:

  ```bash
  journalctl -u traefik -f
  ```
- **Clients Cannot Connect to Traefik**:
  - Ensure Traefik is listening:

    ```bash
    sudo netstat -tulnp | grep traefik
    ```
  - Check firewall rules:
    ```bash
    sudo ufw allow 80/tcp
    sudo ufw allow 443/tcp
    ```