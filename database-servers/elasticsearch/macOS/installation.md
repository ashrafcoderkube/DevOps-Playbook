# Elasticsearch Database Server Installation & Usage on macOS

## **System Requirements**

- **Operating System**: macOS Monterey, Big Sur, or later
- **Processor**: Intel or Apple Silicon (M1/M2) with Rosetta 2
- **Memory**: Minimum 4 GB RAM (8 GB recommended for production)
- **Disk Space**: Minimum 10 GB of free disk space
- **Network**: Stable internet connection


## **Installation Steps**

### **1. Install Homebrew (If Not Installed)**
If Homebrew is not installed, install it with:
```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

### **2. Install Elasticsearch**
```bash
brew tap elastic/tap
brew install elasticsearch-full
```

### **3. Start and Enable Elasticsearch Service**
```bash
brew services start elasticsearch-full
```

### **4. Verify Installation**
Check if Elasticsearch is running:
```bash
curl -X GET "http://localhost:9200/"
```
If Elasticsearch is working correctly, it should return JSON output with cluster details.