## Elasticsearch Database Server Installation & Usage on Windows

### **System Requirements**

- **Operating System**: Windows 10, 11, or Windows Server 2016/2019/2022
- **Processor**: 64-bit, 1.4 GHz or higher
- **Memory**: Minimum 4 GB RAM (8 GB recommended for production)
- **Disk Space**: Minimum 10 GB of free disk space
- **Network**: Stable internet connection


## **Installation Steps**

### **1. Download and Install Elasticsearch**
- Go to the [official Elasticsearch download page](https://www.elastic.co/downloads/elasticsearch).
- Download the latest Windows `.zip` file.
- Extract the contents to a desired location (e.g., `C:\Elasticsearch`).

### **2. Start Elasticsearch**
- Open Command Prompt as Administrator and navigate to the extracted directory:
  ```powershell
  cd C:\Elasticsearch\bin
  ```
- Start Elasticsearch by running:
  ```powershell
  elasticsearch.bat
  ```
- Elasticsearch should now be running in the terminal.

### **3. Verify Installation**
Check if Elasticsearch is running by opening a browser and visiting:
```
http://localhost:9200/
```
Alternatively, use Command Prompt:
```powershell
curl -X GET "http://localhost:9200/"
```
If Elasticsearch is working correctly, it should return JSON output with cluster details.