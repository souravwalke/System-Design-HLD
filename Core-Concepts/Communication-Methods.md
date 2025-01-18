**Communication Patterns**

**What is Polling?**

Polling is a method where the client repeatedly sends requests to the server at regular intervals to check for updates or changes in data.

How Polling Works:
- The client sends a request to the server (e.g., "Do you have any updates?").
- The server responds with the current state or data.
- The client repeats the request after a fixed interval, regardless of whether there are updates or not.

Pros of Polling:
- Simple to Implement: Easy to set up on both client and server sides.
- Reliable: The client doesn't depend on server-side push mechanisms.

Cons of Polling:
- Inefficient: If there are no updates, the client still sends unnecessary requests.
- High Latency: The client only gets updates at the next polling interval, not immediately.
- Increased Load: Frequent requests can overload the server, especially with many clients.

---------------------------------------------------------------------------------------------------------------------------

**What is Long Polling?**

Long polling is a technique used in client-server communication to enable near real-time updates. 

How Long Polling Works:
- The client sends a request to the server asking for updates.
- The server doesn’t respond immediately. Instead, it holds the request open until:
  - There’s new data to send.
  - A timeout occurs (if no data is available for a long time).
- When the server has an update, it responds to the client and closes the connection.
- After receiving the response, the client immediately sends another request to repeat the process.

Long polling is efficient for scenarios where you don't need instantaneous real-time updates, but it can become resource-intensive for high-concurrency applications. For high-volume, real-time applications, alternatives like WebSockets may be better.

---------------------------------------------------------------------------------------------------------------------------

**What are Web Sockets?**

WebSockets are a protocol that enables real-time, full-duplex communication between a client (typically a browser) and a server over a single, persistent connection.

How WebSockets Work:
  1. The client (browser or app) initiates a WebSocket connection by sending an HTTP request to the server.
  2. If the server supports WebSockets, it responds with a special WebSocket handshake to establish the connection.
  3. Once the WebSocket connection is established, it stays open.
  4. The client and server can send messages to each other at any time, without the need for further HTTP requests or responses.
  5. Either side can close the WebSocket connection when it’s no longer needed.

Use Cases: Real-time messaging applications, Live data streaming 

---------------------------------------------------------------------------------------------------------------------------
