# Varnish Cache Server Configuration on macOS

## **Configuration**

### **1. Modify Varnish Configuration File**
The Varnish configuration file is located at `/usr/local/etc/varnish/default.vcl`.

Edit the file using:
```bash
nano /usr/local/etc/varnish/default.vcl
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
Modify the Varnish service configuration:
```bash
nano /usr/local/etc/varnish/varnish.params
```
Find the line with `VARNISH_LISTEN_PORT` and change it to:
```ini
VARNISH_LISTEN_PORT=80
```
Restart Varnish:
```bash
brew services restart varnish
```

## **Troubleshooting**

- **Varnish Service Not Starting**:
  ```bash
  brew services restart varnish
  ```
- **Check Varnish Configuration for Errors**:
  ```bash
  varnishd -C -f /usr/local/etc/varnish/default.vcl
  ```
- **Clients Cannot Connect to Varnish**:
  - Ensure Varnish is listening:
    ```bash
    netstat -an | grep 80
    ```
  - Check firewall rules:
    ```bash
    sudo pfctl -sr | grep 80
    ```