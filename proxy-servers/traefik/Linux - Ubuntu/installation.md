## Traefik Proxy Server Installation & Usage on Linux & Ubuntu

### **System Requirements**

- **Operating System**: Ubuntu, Debian, CentOS, RHEL, Fedora
- **Processor**: 64-bit, 1.4 GHz or higher
- **Memory**: Minimum 2 GB RAM (4 GB recommended for production)
- **Disk Space**: Minimum 2 GB of free disk space
- **Network**: Stable internet connection


## **Installation Steps**

### **1. Update System Packages**
Before installing Traefik, update your system:

```bash
sudo apt update && sudo apt upgrade -y  # Ubuntu/Debian
sudo yum update -y  # CentOS/RHEL
```

### **2. Install Traefik**
#### **On Ubuntu/Debian-based Systems**
```bash
sudo apt install -y curl
curl -sL https://github.com/traefik/traefik/releases/latest/download/traefik_linux_amd64 -o traefik
chmod +x traefik
sudo mv traefik /usr/local/bin/
```

#### **On CentOS/RHEL-based Systems**
```bash
sudo yum install -y curl
curl -sL https://github.com/traefik/traefik/releases/latest/download/traefik_linux_amd64 -o traefik
chmod +x traefik
sudo mv traefik /usr/local/bin/
```

### **3. Verify Installation**
Check if Traefik is installed correctly:
```bash
traefik version
```