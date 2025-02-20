# PostgreSQL Database Server Configuration Ubuntu

## **Configuration**

### **1. Change PostgreSQL Password**
To change the password for the `postgres` user, log in and run:

```sql
ALTER USER postgres PASSWORD 'newpassword';
```

### **2. Allow Remote Connections (Optional)**
Edit the PostgreSQL configuration file (`postgresql.conf`):

```ini
listen_addresses = '*'
```

Edit the authentication file (`pg_hba.conf`):

```ini
host    all             all             0.0.0.0/0               md5
```

Restart PostgreSQL for changes to take effect:

```powershell
net stop postgresql-x64-14
net start postgresql-x64-14
```


## **How to Use PostgreSQL**

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
```powershell
pg_dump -U postgres -d my_database -F c -f backup.dump
```

#### **Restore Database**
```powershell
pg_restore -U postgres -d my_database backup.dump
```

## **Troubleshooting**

- **PostgreSQL Service Not Starting**:
  ```powershell
  net start postgresql-x64-14
  sc query postgresql-x64-14
  ```
- **Forgot PostgreSQL Password**:
  ```sql
  ALTER USER postgres PASSWORD 'newpassword';
  ```
- **Remote Connection Issues**:
  Ensure `listen_addresses = '*'` is set in `postgresql.conf` and `pg_hba.conf` allows remote access.

