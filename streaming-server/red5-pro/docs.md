<img src="assets/image.png" alt="RED 5 " width="250" >

**Red5 Pro** is a scalable, customizable, and high-performance media server that supports real-time streaming and live video communication. It is used for building interactive live streaming, video chat, and other video communication applications. Red5 Pro can handle various types of streaming protocols like RTMP, RTSP, WebRTC, and HLS.

### **Key Features**
- **Real-time Streaming:** Supports low-latency streaming for interactive applications such as video chats, gaming, and live events.
- **Scalability:** Red5 Pro can scale horizontally across multiple servers and offer elastic cloud-based deployments.
- **Multiple Protocol Support:** It supports RTMP, WebRTC, HLS, RTSP, and more, making it versatile for different streaming scenarios.
- **Adaptive Bitrate Streaming:** Ensures the best possible streaming experience by adjusting quality based on bandwidth.
- **API Integration:** Provides a rich set of APIs for integrating live streaming features into your applications.
- **Web & Mobile Support:** Allows streaming to browsers (via WebRTC, HLS) and mobile devices (iOS, Android).
- **Security:** Red5 Pro provides features like secure RTMP (RTMPS) and token authentication to control access to streams.

### **Use Cases**
- **Live Event Streaming:** For events like concerts, webinars, and sports events.
- **Interactive Applications:** Such as video conferencing, live auctions, and gaming platforms.
- **Enterprise Communication:** Facilitating internal video communication or live streaming of corporate events.
- **Mobile & Web Streaming:** Delivering high-quality, real-time streaming to mobile apps and web browsers.

### **Setting Up Red5 Pro**

1. **Prerequisites:**
    - Java 8 or later.
    - Red5 Pro account for configuration and deployment.

2. **Download Red5 Pro:**
   - Go to the [Red5 Pro Download page](https://www.red5pro.com/download/) and get the appropriate package for your operating system.

3. **Install Red5 Pro:**
   - Unzip the downloaded package.
   - Navigate to the directory where you extracted Red5 Pro and run the following command to start the server:
   ```bash
   cd red5pro
   ./red5.sh
   ```

4. **Access the Admin Console:**
   - Red5 Pro provides a web-based admin console where you can manage your streams, applications, and server configurations. By default, it can be accessed at:
   ```text
   http://localhost:5080
   ```
   - The default credentials are `admin:admin`.

---

### **Red5 Pro Commands**

Here are some common **commands** to manage Red5 Pro.

#### **1. Starting and Stopping Red5 Pro**

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

#### **2. Streaming with Red5 Pro**

- **Push a Stream to Red5 Pro Server (via RTMP):**
  - You can stream to Red5 Pro using an RTMP URL, like:
    ```bash
    ffmpeg -re -i input_video.mp4 -f flv rtmp://localhost/live/stream
    ```

- **View a Stream from Red5 Pro:**
  - Using a compatible player, you can view the live stream at:
    ```text
    rtmp://localhost/live/stream
    ```

#### **3. Managing Applications**

- **Create a New Application:**
   - Navigate to the `webapps` directory of your Red5 Pro installation and create a new application directory (e.g., `liveApp`):
   ```bash
   cd /path/to/red5pro/webapps
   mkdir liveApp
   ```

- **Access the New Application in the Browser:**
   - The stream from the application can be accessed using:
   ```text
   http://localhost:5080/liveApp
   ```

#### **4. Monitor Red5 Pro Logs**

- **View Logs:**
   - The logs are located in the `logs` directory within your Red5 Pro installation.
   - To view live logs for debugging or monitoring:
   ```bash
   tail -f /path/to/red5pro/logs/red5-*.log
   ```

#### **5. Red5 Pro API Commands**

Red5 Pro offers an API for controlling various aspects of live streaming.

- **Create a Stream via the API:**
   To create or manage streams, you can make a POST request to Red5 Pro’s API:
   ```bash
   curl -X POST -d "stream_name=example_stream" http://localhost:5080/red5pro/api/createStream
   ```

- **Stop a Stream via the API:**
   Similarly, to stop a stream programmatically:
   ```bash
   curl -X POST -d "stream_name=example_stream" http://localhost:5080/red5pro/api/stopStream
   ```

#### **6. Using WebRTC**

- **Start a WebRTC Stream:**
   If you want to push a WebRTC stream, you can use Red5 Pro’s WebRTC API and tools.

- **Test WebRTC Streaming:**
   - You can test WebRTC with the sample WebRTC apps available in Red5 Pro’s demo section (access via the admin console).

---

### **Official Documentation Links:**

- **Red5 Pro Documentation:**  
  [https://www.red5pro.com/docs](https://www.red5pro.com/docs)
  
- **Red5 Pro API Documentation:**  
  [https://www.red5pro.com/docs/api](https://www.red5pro.com/docs/api)

- **Download Red5 Pro:**  
  [https://www.red5pro.com/download](https://www.red5pro.com/download)
