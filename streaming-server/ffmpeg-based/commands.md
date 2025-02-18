<img src="assets/image.png" alt="ffmpeg" width="250" >

### **FFmpeg-Based Streaming Server Commands**

FFmpeg is a versatile tool for streaming, transcoding, and processing multimedia content. Below are some commonly used commands for FFmpeg-based streaming setups, particularly for live streaming and video-on-demand (VoD) services.

#### **Basic Streaming Commands**

1. **Stream Video to RTMP Server:**
   - To stream a video to a streaming server (e.g., YouTube, Twitch, or a custom RTMP server):
     ```bash
     ffmpeg -i input_video.mp4 -f flv rtmp://<server_address>/live/stream
     ```
     - `input_video.mp4`: Path to the input video file.
     - `rtmp://<server_address>/live/stream`: The RTMP server URL and stream key.

2. **Stream Live Camera Feed to RTMP Server:**
   - To stream a live camera feed (using a webcam) to an RTMP server:
     ```bash
     ffmpeg -f v4l2 -i /dev/video0 -f flv rtmp://<server_address>/live/stream
     ```
     - `/dev/video0`: Path to the webcam device (Linux example).
     - Adjust the device path for other operating systems (e.g., `/dev/video1` for another camera on Linux).

3. **Stream Video to HLS (HTTP Live Streaming):**
   - FFmpeg can segment a video file into chunks for HLS streaming:
     ```bash
     ffmpeg -i input_video.mp4 -c:v libx264 -preset fast -profile:v baseline -maxrate 500k -bufsize 1000k -hls_time 10 -hls_list_size 0 -f hls output.m3u8
     ```
     - `-hls_time 10`: Segment the video into chunks of 10 seconds.
     - `-f hls output.m3u8`: Output the video as an HLS stream with the `m3u8` playlist file.

4. **Convert Video to Multiple Bitrates for Adaptive Streaming (HLS):**
   - To create multiple bitrate streams for adaptive streaming (different quality levels) with HLS:
     ```bash
     ffmpeg -i input_video.mp4 \
       -c:v libx264 -b:v 500k -hls_time 10 -hls_list_size 0 -f hls -hls_segment_filename 'output_500k_%03d.ts' output_500k.m3u8 \
       -c:v libx264 -b:v 1000k -hls_time 10 -hls_list_size 0 -f hls -hls_segment_filename 'output_1000k_%03d.ts' output_1000k.m3u8 \
       -c:v libx264 -b:v 1500k -hls_time 10 -hls_list_size 0 -f hls -hls_segment_filename 'output_1500k_%03d.ts' output_1500k.m3u8
     ```
     - Generates three different bitrate streams (500k, 1000k, and 1500k) for adaptive streaming.

5. **Stream Video Using RTSP Protocol:**
   - To stream a video using the Real-Time Streaming Protocol (RTSP):
     ```bash
     ffmpeg -i input_video.mp4 -f rtsp rtsp://<server_address>/stream
     ```

6. **Live Streaming from Camera (Webcam) to RTMP Server:**
   - For a live streaming setup, capture video from a webcam and stream to an RTMP server:
     ```bash
     ffmpeg -f v4l2 -i /dev/video0 -f flv rtmp://<server_address>/live/stream
     ```
     - `/dev/video0` refers to the webcam device (adjust as necessary).

#### **Transcoding and Format Conversion Commands**

1. **Convert Video to H.264 (For RTMP Streaming):**
   - FFmpeg can convert videos to the H.264 codec for RTMP streaming:
     ```bash
     ffmpeg -i input_video.mp4 -c:v libx264 -c:a aac -preset fast -f flv rtmp://<server_address>/live/stream
     ```

2. **Convert Video to MP4 (H.264/AAC) for VOD Streaming:**
   - Convert a video file to the widely compatible MP4 format using the H.264 video codec and AAC audio codec:
     ```bash
     ffmpeg -i input_video.avi -c:v libx264 -c:a aac -strict experimental output_video.mp4
     ```

3. **Extract Audio from Video File:**
   - Extract the audio stream from a video file and save it as an MP3 file:
     ```bash
     ffmpeg -i input_video.mp4 -vn -acodec libmp3lame output_audio.mp3
     ```
     - `-vn`: Disable video processing (extract audio only).
     - `-acodec libmp3lame`: Use the MP3 codec for audio.

4. **Transcode Video for Different Devices:**
   - Transcode a video for playback on mobile devices:
     ```bash
     ffmpeg -i input_video.mp4 -c:v libx264 -preset slow -c:a aac -strict experimental -b:v 1000k -b:a 128k output_video_device.mp4
     ```
     - Adjust video and audio bitrates as needed.

#### **Additional Useful Commands for Streaming**

1. **Live Stream Recording:**
   - Record a live stream (e.g., RTMP or RTSP) to a file:
     ```bash
     ffmpeg -i rtmp://<server_address>/live/stream -c:v copy -c:a copy -t 3600 output_video.mp4
     ```
     - `-t 3600`: Limit the recording to one hour (3600 seconds).

2. **Stream from a URL to an RTMP Server:**
   - Stream content from a URL (such as an IP camera feed) to an RTMP server:
     ```bash
     ffmpeg -i http://<camera_ip>/stream -f flv rtmp://<server_address>/live/stream
     ```

3. **Start HLS Streaming from a Video File:**
   - Set up an HLS stream from a local video file to stream over HTTP:
     ```bash
     ffmpeg -i input_video.mp4 -c:v libx264 -preset veryfast -hls_time 10 -hls_list_size 0 -f hls output.m3u8
     ```
     - This command generates a series of `.ts` files for the HLS stream.

#### **FFmpeg Streaming Server Setup**

1. **Nginx with RTMP Module (FFmpeg Streaming Server) Setup:**
   - To set up Nginx with RTMP for live streaming using FFmpeg:
     - First, install the RTMP module for Nginx.
     - Add the following to your `nginx.conf` file:
       ```nginx
       server {
         listen 1935;
         chunk_size 4096;
         application live {
           live on;
           record off;
         }
       }
       ```
     - Then, use FFmpeg to push a stream to your Nginx RTMP server:
       ```bash
       ffmpeg -i input_video.mp4 -f flv rtmp://<nginx_server_address>/live/stream
       ```

### **Links for Additional Information**
- [FFmpeg Official Documentation](https://ffmpeg.org/documentation.html)
- [FFmpeg Wiki - Streaming Guide](https://trac.ffmpeg.org/wiki/Streaming)
- [Nginx RTMP Module Documentation](https://github.com/arut/nginx-rtmp-module)
- [Wowza Streaming Engine Docs](https://www.wowza.com/docs/wowza-streaming-engine)
