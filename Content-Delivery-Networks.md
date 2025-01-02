**Content Delivery Networks**

**What are content delivery networks?**

A Content Delivery Network (CDN) is a **geographically distributed network** of servers designed to deliver web content, especially static assets, quickly and reliably to users. 

  - A CDN caches static assets like images, JavaScript files, CSS, fonts, and sometimes even HTML pages.
  - These static assets are replicated across multiple servers (called edge servers) located in various geographical regions.
  - A user's request is routed to the nearest CDN server, minimizing the time it takes to fetch the content.
  - Instead of hitting your origin server (the application server) for every request, the CDN serves the cached static content, reducing load and costs.

Examples of Popular CDNs: AWS CloudFront, Akamai, Cloudflare

------------------------------------------------------------------------------------------------------------------------------------

**What are the benefits of using a CDN?**

- Reduces the load on your origin server and ensures your site doesn’t crash due to overwhelming traffic.
- CDN reduces latency by serving content from the server closest to the user.
- Improves page load times, especially for resource-heavy websites (Video Streaming Platforms)
- Many CDNs offer DDoS protection, Web Application Firewalls (WAF), and TLS encryption, making them essential for websites prone to attacks.
  
------------------------------------------------------------------------------------------------------------------------------------

**How CDNs Work internally?**

  - A user accesses a website (e.g., amazon.com or tiktok.com) in their browser by typing the URL or clicking a link.
  - Before fetching any content, the browser performs a DNS lookup for the domain (e.g., amazon.com).
  - The DNS query is resolved to an IP address, which points to a CDN edge server rather than the origin server
  - The edge server receives the user’s request for content.
  - If the requested content (e.g., an image or HTML file) is cached at the edge server, it is served directly to the user without going back to the origin server.
  - If the content is not cached, the edge server forwards the request to the origin server
  - Cached content is temporary and has a TTL (Time to Live), which determines how long it will be kept in the cache.
