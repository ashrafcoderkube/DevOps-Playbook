<img src="assets/image.png" alt="WOWZA" width="250" >


### **1. Starting and Stopping the Wowza Streaming Engine**

- **Start Wowza Streaming Engine:**
   ```bash
   sudo systemctl start WowzaStreamingEngine
   ```
   
- **Stop Wowza Streaming Engine:**
   ```bash
   sudo systemctl stop WowzaStreamingEngine
   ```

- **Restart Wowza Streaming Engine:**
   ```bash
   sudo systemctl restart WowzaStreamingEngine
   ```

- **Check Status of Wowza Streaming Engine:**
   ```bash
   sudo systemctl status WowzaStreamingEngine
   ```

### **2. Managing Applications**

- **Create a new live streaming application:**
   - First, navigate to the Wowza `content` directory:
   ```bash
   cd /usr/local/WowzaStreamingEngine/content
   ```
   - Then create a new application directory:
   ```bash
   mkdir live
   ```
   - Create or edit the `application.xml` file inside this directory for your live stream configuration.

- **Delete an Application:**
   - Simply remove the application directory:
   ```bash
   rm -rf /usr/local/WowzaStreamingEngine/content/live
   ```

### **3. Streaming with FFmpeg**

- **Push a stream to Wowza (RTMP):**
   ```bash
   ffmpeg -i input_video.mp4 -f flv rtmp://localhost/live/stream
   ```
   This command pushes a video file (`input_video.mp4`) to the Wowza server’s RTMP stream.

- **Pull a stream from Wowza (RTMP):**
   ```bash
   ffmpeg -i rtmp://localhost/live/stream -c copy -f flv rtmp://another_server/live/stream
   ```
   This command pulls the RTMP stream from Wowza and pushes it to another server.

### **4. Checking and Managing Logs**

- **View Logs:**
   You can monitor live logs by accessing the `logs/` directory in your Wowza installation. For instance:
   ```bash
   tail -f /usr/local/WowzaStreamingEngine/logs/charon-*.log
   ```

- **Clear Logs:**
   If needed, you can clear the logs by removing old log files:
   ```bash
   rm /usr/local/WowzaStreamingEngine/logs/*.log
   ```

### **5. Access Wowza Web Admin Console**

- **Start Wowza Admin Console:**  
   Open a web browser and visit:
   ```text
   http://localhost:8088/admin
   ```
   - The default login credentials are `admin/admin` (Change these for production).

### **6. Using Wowza REST API**

Wowza also offers a REST API for controlling and monitoring streams and server configurations.

- **Get the List of Applications:**
   ```bash
   curl -u admin:admin http://localhost:8087/v2/servers/_defaultServer_/vhosts/_defaultVHost_/applications
   ```

- **Create a New Stream:**
   ```bash
   curl -X POST -u admin:admin -d '{"streamName":"mystream"}' http://localhost:8087/v2/servers/_defaultServer_/vhosts/_defaultVHost_/applications/live/streams
   ```

### **7. Monitoring and Reporting**

- **Check Streaming Statistics:**
   You can monitor streaming statistics by accessing the Wowza stats in the Admin Console or through the API.
   
   Example to get stats:
   ```bash
   curl -u admin:admin http://localhost:8087/v2/servers/_defaultServer_/vhosts/_defaultVHost_/applications/live/streams/stats
   ```

---
