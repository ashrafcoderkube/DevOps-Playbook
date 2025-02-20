# Redis Caching Server Installation & Usage on macOS

## **System Requirements**

- **Operating System**: macOS Monterey, Big Sur, or later
- **Processor**: Intel or Apple Silicon (M1/M2) with Rosetta 2
- **Memory**: Minimum 2 GB RAM (4 GB recommended for production)
- **Disk Space**: Minimum 2 GB of free disk space
- **Network**: Stable internet connection


## **Installation Steps**

### **1. Install Homebrew (If Not Installed)**
If Homebrew is not installed, install it with:
```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

### **2. Install Redis**
```bash
brew install redis
```

### **3. Start and Enable Redis Service**
```bash
brew services start redis
```

### **4. Verify Installation**
Check if Redis is running:
```bash
redis-cli ping
```
If Redis is working correctly, it should return:
```
PONG
```