# Traefik Proxy Server Configuration on Linux & Ubuntu

## **Configuration**

### **1. Create a Basic Traefik Configuration File**
Create the file `/etc/traefik/traefik.yml`:
```bash
sudo mkdir -p /etc/traefik
sudo nano /etc/traefik/traefik.yml
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
    directory: "/etc/traefik/conf.d"
    watch: true
```
Save and exit the file.

### **2. Create a Systemd Service File for Traefik**
```bash
sudo nano /etc/systemd/system/traefik.service
```

Add the following content:
```ini
[Unit]
Description=Traefik Reverse Proxy
After=network.target

[Service]
ExecStart=/usr/local/bin/traefik --configFile=/etc/traefik/traefik.yml
Restart=always
User=root

[Install]
WantedBy=multi-user.target
```

Save and exit.

### **3. Start and Enable Traefik**
```bash
sudo systemctl daemon-reload
sudo systemctl start traefik
sudo systemctl enable traefik
```

### **4. Verify Service Status**
```bash
sudo systemctl status traefik
```


## **Troubleshooting**

- **Traefik Service Not Starting**:
  ```bash
  sudo systemctl restart traefik
  sudo journalctl -u traefik --no-pager
  ```
- **Check Traefik Configuration for Errors**:
  ```bash
  traefik check-config --configFile=/etc/traefik/traefik.yml
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

