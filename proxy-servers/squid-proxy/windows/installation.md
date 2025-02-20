## Squid Proxy Server Installation & Usage on Windows

### **System Requirements**

- **Operating System**: Windows 10, 11, or Windows Server 2016/2019/2022
- **Processor**: 64-bit, 1.4 GHz or higher
- **Memory**: Minimum 2 GB RAM (4 GB recommended for production)
- **Disk Space**: Minimum 2 GB of free disk space
- **Network**: Stable internet connection


## **Installation Steps**

### **1. Download and Install Squid for Windows**
Squid is not officially supported on Windows, but a maintained version is available.
- Download Squid for Windows from [Squid for Windows](http://squid.acmeconsulting.it/).
- Extract the downloaded `.zip` file to `C:\Squid`.

### **2. Configure Squid**
- Navigate to the Squid configuration file:
  ```
  C:\Squid\etc\squid.conf
  ```
- Open `squid.conf` in a text editor (e.g., Notepad++ or VS Code).
- To allow specific IPs to use Squid, add the following:
  ```ini
  acl my_network src 192.168.1.0/24
  http_access allow my_network
  ```
- Save the file and close the editor.

### **3. Start Squid Proxy Server**
- Open Command Prompt as Administrator and navigate to the Squid directory:
  ```powershell
  cd C:\Squid\sbin
  ```
- Start Squid with:
  ```powershell
  squid -i
  net start squid
  ```

### **4. Verify Installation**
To check if Squid is running, open a web browser and visit:
```
http://localhost:3128/
```
Alternatively, test with:
```powershell
curl -I --proxy http://localhost:3128 http://example.com
```
