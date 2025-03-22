**Lamport Timestamp** - Lamport timestamp is a simple mechanism used in distributed systems to assign a sequence of timestamps to events, ensuring a consistent logical order of events.  even if the nodes in the system do not have synchronized clocks.

--------------------------------------------------------------------------------------------------------------------------------------------
**Apache Flink** is a framework and distributed processing engine for stateful computations over unbounded and bounded data streams.

-  Unbounded streams: Data streams that don't have a defined end, like continuous sensor data or clickstreams.
-  Bounded streams: Finite datasets, similar to traditional batch processing.

Use Case: Real-time data streaming applications, analytics, and event-driven systems.

--------------------------------------------------------------------------------------------------------------------------------------------
**Merkle tree (also called a hash tree)** is a tree-like data structure in which every leaf node contains the hash of a data block, and every non-leaf (parent) node contains the hash of its child nodes. The root of the Merkle tree represents the complete dataset. It's a clever way of detecting differences between large sets of records. 

--------------------------------------------------------------------------------------------------------------------------------------------
**Reverse Proxy**

A reverse proxy is a server that sits between users and backend servers and forwards client requests to the appropriate backend.

Why Use a Reverse Proxy?
  - Load Balancing – Distributes traffic across multiple backend servers to prevent overload.
  - Security – Hides backend servers from direct public access, protecting them from attacks.
  - Caching – Stores frequently requested data to reduce server load and speed up responses.
  - SSL Termination – Handles encryption/decryption of HTTPS requests, improving performance.
  - Compression & Optimization – Reduces data size before sending responses, making sites faster.

Eg. A website like Netflix has millions of users. Instead of sending all requests directly to backend servers, it uses NGINX as a reverse proxy to Distribute traffic among multiple video servers and cache frequently watched videos to reduce repeated processing.

--------------------------------------------------------------------------------------------------------------------------------------------
