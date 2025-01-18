**Load Balancers**

```Imagine a pizza delivery service with multiple delivery agents. They'll be overloaded if all orders are routed to a single agent. Instead, orders are distributed evenly among all agents to ensure timely deliveries. That's load balancing for your servers!```

----------------------------------------------------------------------------------------------------------------------------

**What is load balancing?**

Load balancing is the process of distributing incoming network requests (or traffic) across multiple servers to ensure that no single server is overwhelmed. This improves performance, reliability, and availability.

  - A client sends a request to a website/application. Instead of going directly to a server, the request first reaches the load balancer.
  - The load balancer routes the request to a healthy server based on a specific algorithm or rule (e.g., round-robin, least connections).
  - The backend server processes the request and sends the response to the load balancer, which then forwards it to the client.
  - The load balancer continuously checks which backend servers are healthy and capable of handling requests. Done using Ping/ TCP checks.
  - If a server fails the health check, it is marked unavailable and requests are redirected to other servers.

-------------------------------------------------------------------------------------------------------------------------------

**How does the load balancer choose which server to send the request to?**

The load balancer uses a variety of algorithms and rules to decide which backend server should handle a particular request.

  - **Round Robin:** Requests are sent to each server in a sequential, circular order. Best used when all backend servers are roughly equal in performance.
  - **Least Connections**: The load balancer checks which server has the fewest active connections (or requests) and sends the next request to that server.
  - **IP Hash**: The load balancer hashes the client’s IP address and uses that value to choose a backend server. Ensures the same client is always directed to the same server.
  - **Geolocation**: Routes traffic based on the geographic location of the client. Ideal for global applications or content delivery networks (CDNs).
  - **Weighted Round Robin**: Similar to Round Robin, each server is assigned a weight based on its capacity. Servers with higher weights will get more requests.

-------------------------------------------------------------------------------------------------------------------------------

**How to Avoid Load Balancer as a Single point of failure?**

To avoid a load balancer becoming a single point of failure, you can deploy Multiple Load Balancers (Active-Active or Active-Passive).

    - Active-Active Setup: Multiple load balancers are running simultaneously, each distributing traffic. If one fails, the others can continue serving requests.
    
    - Active-Passive Setup: One load balancer is active, and the other is passive, only becoming active if the primary one fails.

-------------------------------------------------------------------------------------------------------------------------------

