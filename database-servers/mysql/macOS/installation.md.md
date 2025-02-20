## MySQL Database Server Installation & Usage on macOS

### **System Requirements**

- **Operating System**: macOS Ventura, Monterey, Big Sur, or Catalina.
- **Processor**: Intel or Apple Silicon (M1/M2) with Rosetta 2.
- **Memory**: Minimum 1 GB RAM (2 GB or more recommended).
- **Disk Space**: At least 2 GB of free disk space.


## **Installation Steps**

### **1. Install MySQL Using Homebrew**
Homebrew is the easiest way to install MySQL on macOS. If you haven't installed Homebrew, run:

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

#### Once Homebrew is installed, run:

Homebrew is the easiest way to install MySQL on macOS. If you haven't installed Homebrew, run:

```bash
brew update
brew install mysql
```

### **2. Start MySQL Server**
After installation, start the MySQL service:

```bash
brew services start mysql
```

To verify that MySQL is running:

```bash
mysqladmin -u root status
```

### **3. Secure MySQL Installation**
Run the MySQL security script to set up a root password and remove insecure defaults:

```bash
mysql_secure_installation
```

### Follow the prompts to:

- Set a root password.
- Remove anonymous users.
- Disallow remote root login.
- Remove test databases.