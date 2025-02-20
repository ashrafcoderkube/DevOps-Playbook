## HAProxy Installation & Usage on Windows

### **System Requirements**

- **Operating System**: Windows 10, 11, or Windows Server 2016/2019/2022
- **Processor**: 64-bit, 1.4 GHz or higher
- **Memory**: Minimum 2 GB RAM (4 GB recommended for production)
- **Disk Space**: Minimum 2 GB of free disk space
- **Network**: Stable internet connection


## **Installation Steps**

### **1. Download HAProxy for Windows**
HAProxy is primarily designed for Linux, but it can be used on Windows via Cygwin or the Windows Subsystem for Linux (WSL).

#### **Using Windows Subsystem for Linux (WSL)**
1. Install WSL if not already installed:
   ```powershell
   wsl --install
   ```
2. Install Ubuntu or Debian from the Microsoft Store.
3. Launch WSL and update packages:
   ```bash
   sudo apt update && sudo apt upgrade -y
   ```
4. Install HAProxy:
   ```bash
   sudo apt install -y haproxy
   ```

#### **Using Cygwin**
1. Download and install Cygwin from [Cygwin Official Site](https://www.cygwin.com/).
2. During installation, select `haproxy` package.
3. Complete installation and open the Cygwin terminal.
