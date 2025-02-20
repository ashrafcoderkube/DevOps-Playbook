# Memcached Caching Server Configuration on Windows

## **Configuration**

### **1. Modify Memcached Configuration**
Memcached does not use a configuration file by default on Windows. Instead, you can pass parameters when starting the service.

To allocate 256MB of memory and allow external connections, run:
```powershell
C:\Memcached\memcached.exe -m 256 -l 0.0.0.0 -d restart
```

### **2. Restart Memcached Service**
```powershell
net stop memcached
net start memcached
```

## **Troubleshooting**

- **Memcached Service Not Starting**:
  ```powershell
  net stop memcached
  net start memcached
  ```
- **Connection Issues**:
  ```powershell
  netstat -ano | findstr 11211
  ```
- **Check Memory Usage**:
  ```powershell
echo stats | nc localhost 11211 | findstr bytes
  ```