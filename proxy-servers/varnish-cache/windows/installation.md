## Varnish Cache Proxy Server Installation & Usage on Windows

### **System Requirements**

- **Operating System**: Windows 10, 11, or Windows Server 2016/2019/2022
- **Processor**: 64-bit, 1.4 GHz or higher
- **Memory**: Minimum 2 GB RAM (4 GB recommended for production)
- **Disk Space**: Minimum 2 GB of free disk space
- **Network**: Stable internet connection


## **Installation Steps**

### **1. Download Varnish for Windows**
Varnish does not have an official Windows release. You can install it using Windows Subsystem for Linux (WSL).

#### **Enable WSL**
Open PowerShell as Administrator and run:
```powershell
wsl --install
```
Restart your computer if necessary.

#### **Install Ubuntu and Varnish**
1. Open the Microsoft Store and install **Ubuntu**.
2. Launch Ubuntu and update packages:
   ```bash
   sudo apt update && sudo apt upgrade -y
   ```
3. Install Varnish:
   ```bash
   sudo apt install -y varnish
   ```

### **2. Start and Enable Varnish Service**
```bash
sudo systemctl start varnish
sudo systemctl enable varnish
```

### **3. Verify Installation**
Check if Varnish is running:
```bash
sudo systemctl status varnish
```

