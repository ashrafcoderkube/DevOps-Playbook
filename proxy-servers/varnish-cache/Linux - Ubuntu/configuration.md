# Varnish Cache Server Configuration on Linux & Ubuntu

## **Configuration**

### **1. Modify Varnish Configuration File**
The Varnish configuration file is located at `/etc/varnish/default.vcl`.

Edit the file using:
```bash
sudo nano /etc/varnish/default.vcl
```

### **2. Basic Backend Configuration**
Modify the backend server settings:
```vcl
backend default {
    .host = "127.0.0.1";
    .port = "8080";
}
```
Save and exit the file.

### **3. Change Varnish Listening Port to 80**
Modify the Varnish systemd configuration file:
```bash
sudo nano /etc/systemd/system/varnish.service
```
Find the line starting with `ExecStart` and change the port to 80:
```ini
ExecStart=/usr/sbin/varnishd -a :80 -T localhost:6082 -f /etc/varnish/default.vcl -s malloc,256m
```
Reload the systemd daemon and restart Varnish:
```bash
sudo systemctl daemon-reload
sudo systemctl restart varnish
```

## **Troubleshooting**

- **Varnish Service Not Starting**:
  ```bash
  sudo systemctl restart varnish
  sudo journalctl -u varnish --no-pager
  ```
- **Check Varnish Configuration for Errors**:
  ```bash
  varnishd -C -f /etc/varnish/default.vcl
  ```
- **Clients Cannot Connect to Varnish**:
  - Ensure Varnish is listening:
    ```bash
    sudo netstat -tulnp | grep varnish
    ```
  - Check firewall rules:
    ```bash
    sudo ufw allow 80/tcp
    ```