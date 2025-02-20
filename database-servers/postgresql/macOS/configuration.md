# PostgreSQL Database Server Configuration on macOS

## **Configuration**

### **1. Connect to PostgreSQL**
To access PostgreSQL, use the following command:

```bash
psql postgres
```

### **2. Set a Password for the PostgreSQL User**
Inside the PostgreSQL shell, set a password for the default `postgres` user:

```sql
ALTER USER postgres PASSWORD 'newpassword';
```

Exit the shell:

```sql
\q
```

### **3. Configure PostgreSQL for Remote Access (Optional)**
To allow remote access, modify the configuration file:

```bash
nano /usr/local/var/postgres/postgresql.conf
```

Find and modify this line:

```ini
listen_addresses = '*'
```

Then, edit `pg_hba.conf` to allow remote access:

```bash
nano /usr/local/var/postgres/pg_hba.conf
```

Add this line:

```ini
host    all             all             0.0.0.0/0               md5
```

Restart PostgreSQL for changes to take effect:

```bash
brew services restart postgresql
```


## **How to Use PostgreSQL on macOS**

### **1. Create a New Database**
```sql
CREATE DATABASE my_database;
```

### **2. Create a New User and Grant Privileges**
```sql
CREATE USER my_user WITH ENCRYPTED PASSWORD 'mypassword';
GRANT ALL PRIVILEGES ON DATABASE my_database TO my_user;
```

### **3. List Databases**
```sql
\l
```

### **4. Connect to a Database**
```sql
\c my_database
```

### **5. Create a Table**
```sql
CREATE TABLE users (
    id SERIAL PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    email VARCHAR(100) UNIQUE NOT NULL
);
```

### **6. Insert Data into the Table**
```sql
INSERT INTO users (name, email) VALUES ('John Doe', 'john.doe@example.com');
```

### **7. Retrieve Data**
```sql
SELECT * FROM users;
```

### **8. Backup and Restore PostgreSQL Database**

#### **Backup Database**
```bash
pg_dump -U postgres -d my_database -F c -f backup.dump
```

#### **Restore Database**
```bash
pg_restore -U postgres -d my_database backup.dump
```


## **Troubleshooting**

- **PostgreSQL Service Not Running**:
  ```bash
  brew services restart postgresql
  brew services list
  ```
- **Forgot PostgreSQL Password**:
  Reset the password by accessing PostgreSQL as the system user:
  ```bash
  psql postgres
  ALTER USER postgres PASSWORD 'newpassword';
  \q
  ```
- **Remote Connection Issues**:
  Ensure `listen_addresses = '*'` is set in `postgresql.conf` and `pg_hba.conf` allows remote access.