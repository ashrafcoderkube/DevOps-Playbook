## PostgreSQL Database Server Installation & Usage on macOS

### **System Requirements**

- **Operating System**: macOS Ventura, Monterey, Big Sur, or Catalina
- **Processor**: Intel or Apple Silicon (M1/M2) with Rosetta 2
- **Memory**: Minimum 2 GB RAM (4 GB recommended for production)
- **Disk Space**: Minimum 2 GB of free disk space


## **Installation Steps**

### **1. Install PostgreSQL Using Homebrew**
Homebrew is the easiest way to install PostgreSQL on macOS. If you haven't installed Homebrew, run:

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

Once Homebrew is installed, install PostgreSQL:

```bash
brew update
brew install postgresql
```

### **2. Start PostgreSQL Service**
After installation, start the PostgreSQL service:

```bash
brew services start postgresql
```

To verify that PostgreSQL is running:

```bash
pg_ctl -D /usr/local/var/postgres status
```

### **3. Initialize the Database (If Needed)**
If PostgreSQL does not start automatically, you may need to initialize the database:

```bash
initdb /usr/local/var/postgres -E utf8
```

Restart the PostgreSQL service:

```bash
brew services restart postgresql
```
