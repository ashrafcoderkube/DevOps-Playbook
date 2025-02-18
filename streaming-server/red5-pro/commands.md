<img src="assets/image.png" alt="RED 5 " width="250" >


### **1. Starting and Stopping Red5 Pro**

- **Start Red5 Pro Server:**
  ```bash
  cd /path/to/red5pro
  ./red5.sh
  ```

- **Stop Red5 Pro Server:**
  ```bash
  cd /path/to/red5pro
  ./red5.sh stop
  ```

### **2. Streaming Commands**

- **Push a Stream to Red5 Pro Server (via RTMP):**
  Use **FFmpeg** to push video streams to Red5 Pro:
  ```bash
  ffmpeg -re -i input_video.mp4 -f flv rtmp://localhost/live/stream
  ```

- **Pull a Stream from Red5 Pro:**
  To view a live stream:
  ```text
  rtmp://localhost/live/stream
  ```

### **3. Managing Applications**

- **Create a New Application:**
  Navigate to the `webapps` directory and create a new application:
  ```bash
  cd /path/to/red5pro/webapps
  mkdir liveApp
  ```

- **Access the New Application in the Browser:**
  Your stream will be available at:
  ```text
  http://localhost:5080/liveApp
  ```

### **4. Monitoring Red5 Pro Logs**

- **View Logs:**
  To monitor Red5 Pro logs in real-time:
  ```bash
  tail -f /path/to/red5pro/logs/red5-*.log
  ```

### **5. Red5 Pro API Commands**

- **Create a Stream via the API:**
  Use the API to create a stream:
  ```bash
  curl -X POST -d "stream_name=example_stream" http://localhost:5080/red5pro/api/createStream
  ```

- **Stop a Stream via the API:**
  Use the API to stop a stream:
  ```bash
  curl -X POST -d "stream_name=example_stream" http://localhost:5080/red5pro/api/stopStream
  ```
