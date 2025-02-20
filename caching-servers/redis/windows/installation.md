## Redis Caching Server Installation & Usage on Windows

### **System Requirements**

- **Operating System**: Windows 10, 11, or Windows Server 2016/2019/2022
- **Processor**: 64-bit, 1.4 GHz or higher
- **Memory**: Minimum 2 GB RAM (4 GB recommended for production)
- **Disk Space**: Minimum 2 GB of free disk space
- **Network**: Stable internet connection


## **Installation Steps**

### **1. Download and Install Redis for Windows**
Redis does not have an official Windows release, but a maintained version is available via Memurai or WSL.

#### **Option 1: Install Redis via Memurai**
1. Download [Memurai](https://www.memurai.com/download) (a Redis-compatible alternative for Windows).
2. Install and start Memurai.
3. Verify installation:
   ```powershell
   redis-cli ping
   ```

#### **Option 2: Install Redis via Windows Subsystem for Linux (WSL)**
1. Enable WSL by running PowerShell as Administrator:
   ```powershell
   wsl --install
   ```
2. Install Ubuntu from the Microsoft Store and launch it.
3. Inside Ubuntu, install Redis:
   ```bash
   sudo apt update && sudo apt install -y redis-server
   ```
4. Start Redis:
   ```bash
   sudo systemctl start redis
   ```
5. Verify Redis is running:
   ```bash
   redis-cli ping
   ```
