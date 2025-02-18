<img src="assets/image.png" alt="FTP " width="250" >

### **FTP (File Transfer Protocol) Theory**

**Overview:**
FTP (File Transfer Protocol) is a standard network protocol used to transfer files between a client and a server over a TCP/IP network. It operates on a client-server model where the client initiates the connection to the FTP server to upload or download files.

**Key Features:**
1. **Client-Server Model**: FTP relies on a client (which makes requests) and a server (which responds).
2. **Active vs. Passive Mode**: FTP supports two modes for data transfer – active mode and passive mode – to handle firewall and NAT (Network Address Translation) scenarios.
3. **Authentication**: FTP often requires a username and password for authentication, though anonymous FTP allows file access without credentials.
4. **Port Numbers**:
   - **Port 21**: Default port used by FTP for the command/control channel.
   - **Port 20**: Typically used for data transfer in active mode.

**Use Cases:**
- **File Sharing**: Transferring files between systems on a local network or over the internet.
- **Website Deployment**: Uploading website files to web servers.
- **Backup and Recovery**: Using FTP servers for backups, especially in enterprise environments.
- **System Administration**: Managing file systems on remote servers.

**Types of FTP:**
1. **Active FTP**: The client opens a random port for data transfer and the server connects to this port.
2. **Passive FTP**: The server opens a random port for data transfer, and the client connects to this port.

**Security:**
- FTP in its original form (FTP) does not provide encryption. However, secure versions exist, such as:
  - **FTPS (FTP Secure)**: Adds SSL/TLS encryption to the standard FTP.
  - **SFTP (SSH File Transfer Protocol)**: A secure alternative that uses SSH (Secure Shell) for encryption.

### **Setting Up an FTP Server (Example: vsftpd on Linux)**

1. **Install vsftpd (Very Secure FTP Daemon):**

   ```bash
   sudo apt-get update
   sudo apt-get install vsftpd
   ```

2. **Start the FTP Service**:

   ```bash
   sudo systemctl start vsftpd
   ```

3. **Enable vsftpd to Start on Boot**:

   ```bash
   sudo systemctl enable vsftpd
   ```

4. **Configure vsftpd**:

   - Edit the configuration file:
     ```bash
     sudo nano /etc/vsftpd.conf
     ```

   - Common settings include:
     - **anonymous_enable=YES/NO**: Enable/Disable anonymous FTP access.
     - **local_enable=YES**: Allow local users to log in.
     - **write_enable=YES**: Allow writing files.
     - **chroot_local_user=YES**: Restrict users to their home directory.

5. **Restart the FTP Service**:

   ```bash
   sudo systemctl restart vsftpd
   ```

6. **Check the FTP Status**:

   ```bash
   sudo systemctl status vsftpd
   ```

---

### **FTP Client Commands**

#### **Connecting to an FTP Server**

- **Open FTP Session**:
    ```bash
    ftp <hostname>
    ```

    Example:
    ```bash
    ftp ftp.example.com
    ```

- **Login with Username and Password**:
    ```bash
    Name (hostname:username): <username>
    Password: <password>
    ```

#### **File Management Commands**

- **List Files in Current Directory**:
    ```bash
    ls
    ```

- **Change Directory**:
    ```bash
    cd <directory-name>
    ```

- **Upload a File to the Server**:
    ```bash
    put <local-file>
    ```

    Example:
    ```bash
    put myfile.txt
    ```

- **Download a File from the Server**:
    ```bash
    get <remote-file>
    ```

    Example:
    ```bash
    get example.txt
    ```

- **Create a Directory on the Server**:
    ```bash
    mkdir <directory-name>
    ```

- **Delete a File from the Server**:
    ```bash
    delete <remote-file>
    ```

- **Rename a File on the Server**:
    ```bash
    rename <old-name> <new-name>
    ```

- **Exit the FTP Session**:
    ```bash
    bye
    ```

#### **Additional FTP Client Commands**

- **Put Multiple Files in a Batch**:
    ```bash
    mput *.txt
    ```

- **Get Multiple Files in a Batch**:
    ```bash
    mget *.jpg
    ```

- **Change Local Directory**:
    ```bash
    lcd <local-directory>
    ```

- **List Remote Directory**:
    ```bash
    dir
    ```

---

### **Secure FTP (SFTP)**

SFTP is a secure alternative to FTP. It uses SSH for encryption and is typically used when security is a concern.

#### **SFTP Commands**

- **Connect to an SFTP Server**:
    ```bash
    sftp <username>@<hostname>
    ```

- **Upload a File to the Server**:
    ```bash
    put <local-file>
    ```

- **Download a File from the Server**:
    ```bash
    get <remote-file>
    ```

- **Change Remote Directory**:
    ```bash
    cd <directory-name>
    ```

- **List Files in Remote Directory**:
    ```bash
    ls
    ```

- **Exit the SFTP Session**:
    ```bash
    exit
    ```

---

### **FTP Security Considerations**
1. **Use FTPS or SFTP for Encryption**: Standard FTP transmits data in plaintext. Always prefer **FTPS** or **SFTP** when security is required.
2. **Limit FTP User Access**: Ensure that only authorized users have access to the FTP server.
3. **Use Strong Passwords**: Protect against unauthorized access with strong, complex passwords.
4. **Use Firewalls**: Restrict FTP access to specific IP addresses or ranges for additional security.

### **Official FTP Resources and Documentation**

- [vsftpd Documentation](https://security.appspot.com/vsftpd.html)
- [FTP Protocol Overview](https://tools.ietf.org/html/rfc959)
- [SFTP Protocol Overview](https://tools.ietf.org/html/rfc4251)

