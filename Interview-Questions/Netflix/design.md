**Design a Video Streaming Platform (Netflix/ Youtube)**

--------------------------------------------------------------------------------------------------------------------------------------------------------------------
**Functional Requirements**
- Users should be able to upload videos.
- Users should be able to watch videos.
- Users should be able to search for videos

Below the Line
- Users can like and comment on a video.
- Users can subscribe to a channel and get notified.
- Users should see a home feed with videos.

**Non-Functional Requirements**
- System should prioritize availability over consistency.
- The system should have low-latency video streaming.
- System should support adaptive bitrate streaming.

--------------------------------------------------------------------------------------------------------------------------------------------------------------------
**Video Streaming Basics**

1. **Transcoding** is the process of converting a media file from one format, codec, or resolution to another.
2. Netflix/YouTube streams to many different devices, each supporting different video formats.
3. Users also have different internet speeds, from slow mobile networks to high-speed connections.
4. To ensure smooth playback, Netflix creates multiple versions of each video at different quality levels (bitrates from 100 kbps to 16 Mbps).
5. The Netflix/YouTube app then picks the best version based on the user’s real-time internet speed.
6. 
