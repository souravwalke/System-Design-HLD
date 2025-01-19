**Design a Rate Limiter**

**What is a rate limiter?**

In the HTTP world, a rate limiter limits the number of client requests sent over a specified period. A rate limiter acts like a security guard for our servers and does the following:

- Controls access to resources: Limits the number of requests (e.g., 100 per minute).
- Protects the system: Prevents overloading servers, abuse, or denial-of-service (DoS) attacks.
- Provides fairness: Ensures all users get a fair chance to use the system.

Rate limiters are usually present in the API Gateway in most systems because the gateway serves as the first entry point for client requests. 

Examples: Netflix does not allow more than two devices to watch at once.

---------------------------------------------------------------------------------------------------------------------------------------------------------------
**Step-1: Requirement Gathering**

1. Should it be a client-side rate limiter or a server-side? Typically it will be a server-side rate limiter.
2. Does the rate limiter throttle API requests based on IP, user ID, or other properties? - Should support multiple
3. Should the user be informed ? - Yes
4. Is it a single-machine system or distributed ? - Distributed
