**Design a Rate Limiter**

**What is a rate limiter?**

In the HTTP world, a rate limiter limits the number of client requests sent over a specified period. A rate limiter acts like a security guard for our servers and does the following:

- Controls access to resources: Limits the number of requests (e.g., 100 per minute).
- Protects the system: Prevents overloading servers, abuse, or denial-of-service (DoS) attacks.
- Provides fairness: Ensures all users get a fair chance to use the system.

Most systems usually present rate limiters in the API Gateway because the gateway serves as the first entry point for client requests. 

Examples: Netflix does not allow more than two devices to watch simultaneously.

---------------------------------------------------------------------------------------------------------------------------------------------------------------
**Step-1: Requirement Gathering**

1. Should it be a client-side rate limiter or a server-side? Typically it will be a server-side rate limiter.
2. Does the rate limiter throttle API requests based on IP, user ID, or other properties? - Should support multiple
3. Should the user be informed in case the requests are throttled? - Yes
4. Is it a single-machine system or distributed? - Distributed

---------------------------------------------------------------------------------------------------------------------------------------------------------------
**Step 2: Propose a High-level Design**

- While proposing the design of a rate limiter, we will consider a basic client-server architecture.
  
- There are multiple places where the rate-limiter can be placed
  - Client-side: Not recommended as we would not have any control over the implementation and can be easily bypassed by the user with some software.
  - Application server: Although a better solution, this allows the requests to hit the application server and can increase the load of the server.
  - Middleware: This is the best solution since the server and rate-limiter are decoupled and can be scaled independently.

- Rate limiting can be implemented using different algorithms, and each of them has distinct pros and cons.

- **Token bucket algorithm:**
  -  A token bucket is a container that has a pre-defined capacity.
  -  Tokens are put in the bucket at preset rates periodically.
  -  Once the bucket is full, no more tokens are added.
  -  Each request consumes one token.
  -  If there are enough tokens, we take one token out for each request, and the request goes through.
  -  If there are not enough tokens, the request is dropped.
 
  - Pros: The algorithm is easy to implement and memory efficient.
  - Cons: Tuning the bucket size and token refill rate is challenging. Requires a lot of analysis to get it right.

- **Fixed window counter algorithm:**
  - The algorithm divides the timeline into fix-sized time windows and assigns a counter for each window.
  - Each request increments the counter by one.
  - Once the counter reaches the pre-defined threshold, new requests are dropped until a new time window starts.

  - Pros: Easy to implement and memory efficient.
  - Cons: A major problem with this algorithm is a burst of traffic at the edges of time windows.

- **Sliding Window Log:**
  - The sliding window log algorithm fixes the issue of the fixed window counter. (Burst traffic at the edges)
  - The algorithm keeps track of request timestamps.
  - When a new request comes in, remove all the outdated timestamps.
  - Add the timestamp of the new request to the log
  - If the log size is the same or lower than the allowed count, a request is accepted. Otherwise, it is rejected.

  - Pros: Rate limiting implemented by this algorithm is very accurate.
  - Cons: Not memory efficient

---------------------------------------------------------------------------------------------------------------------------------------------------------------
**Deep Dives**

1. The system should support multiple rate-limiting rules for different APIs.

Rules are generally written in configuration files and saved on disk. However, making a database call for each request can be expensive and disk fetch calls are slower. Instead of reading rules directly from the database or disk for every request, we load them into a cache, which is a faster, in-memory data store.

2. The system should handle requests that are rate-limited.

In case a request is rate-limited, APIs return an HTTP response code 429 (too many requests) to the client. Other possibilities could be to add throttled requests to a message queue for a retry.

3. The system should work in a distributed environment.

In a distributed rate-limiting setup, although there could be multiple rate limiters all of them should share a global redis counter to avoid synchronization issues.
