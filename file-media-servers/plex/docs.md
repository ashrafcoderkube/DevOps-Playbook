<img src="assets/image.png" alt="plex"  width="250" >

**Overview:**
Plex is a media server platform that allows users to organize and stream their media content (such as movies, TV shows, music, and photos) to various devices, including smartphones, smart TVs, computers, and more. Plex makes it easy to create your own personal streaming server by centralizing and managing all your media in one place.

**Key Features:**
1. **Media Organization**: Automatically organizes and catalogs your media library (movies, TV shows, music, etc.).
2. **Streaming**: Plex allows streaming media across multiple devices, whether on the same local network or remotely over the internet.
3. **Transcoding**: Plex can transcode media on-the-fly, allowing you to stream content in the right format and resolution for the device you're using.
4. **Multi-Device Support**: Plex supports streaming to a wide variety of devices, such as smartphones, gaming consoles, smart TVs, and web browsers.
5. **Remote Access**: With Plex Pass, you can access your media from anywhere by setting up remote access.
6. **Metadata Fetching**: Plex automatically downloads metadata (like cover art, descriptions, cast information) from sources like IMDb, Rotten Tomatoes, and more.
7. **User Management**: Plex allows you to create multiple user profiles with personalized libraries and recommendations.
8. **Cloud Sync**: Sync media content from your Plex library to your mobile devices for offline viewing (requires Plex Pass).
9. **Plex Pass**: Premium subscription that adds advanced features, including mobile sync, premium music, live TV, and DVR functionality.

**Use Cases:**
- **Personal Media Server**: Centralize and organize personal media collections (e.g., movies, TV shows, music) on a single device, accessible from anywhere.
- **Home Theater System**: Stream your media to a home theater setup, including smart TVs, gaming consoles, and streaming devices.
- **Remote Media Access**: Access and stream your media library from anywhere using the Plex web app or mobile app.

**Supported Platforms:**
- Plex is available on almost every platform, including Windows, macOS, Linux, iOS, Android, Roku, Amazon Fire TV, Apple TV, and many others.

**Plex Server and Client:**
- **Plex Server**: The software running on the machine where your media files are stored. This can be a dedicated server, a NAS (Network Attached Storage), or a PC.
- **Plex Client**: The software you use to access the media, whether it’s the mobile app, web browser, or smart TV app.

### **Plex Server Setup (Basic Overview)**

1. **Download Plex Media Server:**
   - Go to [Plex Downloads Page](https://www.plex.tv/media-server-downloads/) and download the appropriate version for your operating system.
   
2. **Install Plex Media Server:**
   - Install the Plex Media Server on your machine, whether it's Windows, macOS, or Linux.

3. **Initial Setup:**
   - After installation, open the Plex Media Server interface in a web browser (typically `http://localhost:32400/web`).
   - Log in with a Plex account, or create one if you don’t have one.
   
4. **Add Media Libraries:**
   - After logging in, you can start adding libraries by specifying the media type (e.g., Movies, TV Shows, Music) and pointing Plex to the directories where your media is stored.
   
5. **Enable Remote Access (Optional):**
   - To enable streaming from anywhere, configure remote access by going to Settings > Remote Access and enabling it (Plex Pass may be required for advanced features).

---

### **Plex Commands (CLI)**

While Plex does not have an official CLI for managing the server (other than Plex Media Server's web interface), you can use the following techniques and common commands to manage Plex from the command line or via scripting.

#### **1. Installing Plex Media Server (Linux)**

For Debian-based systems (Ubuntu, etc.), use the following commands:

```bash
# Install required dependencies
sudo apt-get update
sudo apt-get install apt-transport-https

# Add Plex repository
curl https://downloads.plex.tv/plex-keys/PlexSign.key | sudo apt-key add -
echo deb https://downloads.plex.tv/repo/deb public main | sudo tee /etc/apt/sources.list.d/plex.list

# Install Plex Media Server
sudo apt-get update
sudo apt-get install plexmediaserver
```

For Red Hat-based systems (CentOS, Fedora, etc.), use:

```bash
# Add Plex repository
sudo rpm --import https://downloads.plex.tv/plex-keys/PlexSign.key
echo "[plexpass]" | sudo tee -a /etc/yum.repos.d/plex.repo
echo "name=Plex Pass" | sudo tee -a /etc/yum.repos.d/plex.repo
echo "baseurl=https://downloads.plex.tv/repo/rpm/plexpass" | sudo tee -a /etc/yum.repos.d/plex.repo

# Install Plex Media Server
sudo yum install plexmediaserver
```

#### **2. Start, Stop, and Restart Plex Media Server (Linux)**

You can manage the Plex Media Server via systemd on Linux:

```bash
# Start Plex Media Server
sudo systemctl start plexmediaserver

# Stop Plex Media Server
sudo systemctl stop plexmediaserver

# Restart Plex Media Server
sudo systemctl restart plexmediaserver
```

#### **3. Plex Media Server Logs**

You can view Plex Media Server logs for troubleshooting purposes:

```bash
# View Plex logs (Linux)
cat /var/lib/plexmediaserver/Library/Application\ Support/Plex\ Media\ Server/Logs/Plex\ Media\ Server.log
```

#### **4. Updating Plex Media Server (Linux)**

To update Plex Media Server to the latest version:

```bash
# Update Plex Media Server
sudo apt-get update
sudo apt-get upgrade plexmediaserver
```

For RPM-based systems:

```bash
sudo yum update plexmediaserver
```

#### **5. Plex Server Web Interface**

By default, the Plex Web Interface is accessible at:

```bash
http://localhost:32400/web
```

You can also access it remotely once you’ve set up remote access.

---

### **Official Plex Documentation Links:**
- [Plex Website](https://www.plex.tv/)
- [Plex Media Server Setup Guide](https://support.plex.tv/articles/200264746-installation/)
- [Plex CLI Tools and API](https://github.com/plexinc-archive/plex-media-server)
- [Plex Community Forums](https://forums.plex.tv/)
- [Plex Support](https://support.plex.tv/)

