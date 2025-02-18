<img src="assets/image.png" alt="plex"  width="250" >

### **1. Plex Media Server Installation (Linux)**

#### For Ubuntu/Debian-based systems:
```bash
# Update package list and install dependencies
sudo apt-get update
sudo apt-get install apt-transport-https curl

# Add Plex repository key
curl https://downloads.plex.tv/plex-keys/PlexSign.key | sudo apt-key add -

# Add Plex repository
echo deb https://downloads.plex.tv/repo/deb public main | sudo tee /etc/apt/sources.list.d/plex.list

# Update package list again
sudo apt-get update

# Install Plex Media Server
sudo apt-get install plexmediaserver
```

#### For CentOS/Red Hat-based systems:
```bash
# Import Plex repository key
sudo rpm --import https://downloads.plex.tv/plex-keys/PlexSign.key

# Add Plex repository
echo "[plexpass]" | sudo tee -a /etc/yum.repos.d/plex.repo
echo "name=Plex Pass" | sudo tee -a /etc/yum.repos.d/plex.repo
echo "baseurl=https://downloads.plex.tv/repo/rpm/plexpass" | sudo tee -a /etc/yum.repos.d/plex.repo

# Install Plex Media Server
sudo yum install plexmediaserver
```

---

### **2. Starting, Stopping, and Restarting Plex Media Server (Linux)**

#### Start Plex Media Server:
```bash
sudo systemctl start plexmediaserver
```

#### Stop Plex Media Server:
```bash
sudo systemctl stop plexmediaserver
```

#### Restart Plex Media Server:
```bash
sudo systemctl restart plexmediaserver
```

#### Enable Plex to start on boot:
```bash
sudo systemctl enable plexmediaserver
```

#### Disable Plex from starting on boot:
```bash
sudo systemctl disable plexmediaserver
```

---

### **3. Check Plex Media Server Status (Linux)**

To check the current status of Plex Media Server:

```bash
sudo systemctl status plexmediaserver
```

---

### **4. Access Plex Media Server Web Interface**

After installing and starting the Plex Media Server, you can access its web interface:

```bash
http://localhost:32400/web
```

If you're setting up remote access, you can access it from any device once the setup is complete.

---

### **5. Plex Media Server Logs**

To view the logs for troubleshooting purposes:

```bash
# Logs for Plex Media Server (Linux)
cat /var/lib/plexmediaserver/Library/Application\ Support/Plex\ Media\ Server/Logs/Plex\ Media\ Server.log
```

---

### **6. Updating Plex Media Server (Linux)**

To update Plex Media Server to the latest version:

#### For Ubuntu/Debian-based systems:
```bash
sudo apt-get update
sudo apt-get upgrade plexmediaserver
```

#### For CentOS/Red Hat-based systems:
```bash
sudo yum update plexmediaserver
```

---

### **7. Removing Plex Media Server (Linux)**

To remove Plex Media Server from your system:

#### For Ubuntu/Debian-based systems:
```bash
sudo apt-get remove plexmediaserver
```

#### For CentOS/Red Hat-based systems:
```bash
sudo yum remove plexmediaserver
```

---

### **8. Managing Media Libraries via Web Interface**

After setting up Plex, you can manage your libraries (Movies, TV Shows, Music, Photos, etc.) via the web interface at:

```bash
http://localhost:32400/web
```

In the web interface, you can:
- Add new media libraries.
- Organize and refresh metadata.
- Enable remote access.

---

### **9. Plex Media Server Health Check**

Check the health and logs of Plex Media Server to ensure it's working properly:
```bash
sudo journalctl -u plexmediaserver
```

---

### **10. Plex Database Management**

You can manage the Plex database for backups, troubleshooting, or clearing metadata using the following command:

```bash
# Backup Plex database (in case of a migration or issues)
cp -r /var/lib/plexmediaserver/Library/Application\ Support/Plex\ Media\ Server/ /path/to/backup/directory/
```
---
