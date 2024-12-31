**Caching**

```Think of caching like keeping your favorite snacks on the kitchen counter instead of going to the pantry every time you want one. The kitchen counter (cache) is easily accessible, so you can grab your snack (data) quickly, instead of walking to the pantry (database) and spending time finding it.```

--------------------------------------------------------------------------------------------------

**What is Caching?**

Caching is a mechanism to store frequently accessed data in memory, making read operations faster by eliminating the need to query the database every time. Keeping data closer to the application in memory reduces the latency associated with fetching data from slower, persistent storage (like a database) and speeds up response times.

Cached information can include the results of database queries, computationally intensive calculations, API requests/responses, and web artifacts such as HTML, JavaScript, and image files.

A successful cache results in a **high hit rate** which means the data was present when fetched.

--------------------------------------------------------------------------------------------------

**What are the tradeoffs of Caching?**

- Caching stores data in memory much faster than disk-based storage.
  **Tradeoff:**  However, memory is limited and expensive so large amounts of data cannot be stored in a cache and data needs to be selectively added.

- If the data is already in the cache, it’s super fast to retrieve.
  **Tradeoff:**  If the data is not in the cache (a cache miss), it must be fetched from the slower database, which negates the   performance benefit.

- Caching can reduce the load on the primary database by serving data quickly from the cache.
  **Tradeoff:** Cached data may become stale if the underlying data in the database changes but the cache isn’t updated immediately.

- Caching can greatly improve performance for read-heavy applications.
  **Tradeoff:** Implementing cache invalidation and ensuring cache consistency can complicate your system.

--------------------------------------------------------------------------------------------------

**What are some of the cache eviction policies?**

Cache eviction policies determine how to remove data from the cache when it reaches its memory limit. These policies are essential because cache memory is limited, and when it’s full, older or less useful data needs to be removed to make room for newer data. 

- FIFO (First In, First Out): Cache evicts the oldest data. Simple to implement but not efficient.
- LRU (Least Recently Used): Cache evicts the least recently accessed data. Best and most widely used of the lot.
- LFU (Least Frequently Used): The cache evicts the data that has been accessed the least number of times.
- Random Eviction: The cache randomly selects a key to evict when space is needed.
- TTL (Time to Live): Data in the cache is evicted after a predefined period.

--------------------------------------------------------------------------------------------------

**What are the ways to keep the cache updated with the most recent database write updates?**

- Write-Through Cache: Every time you write to the database, the data is also written to the cache at the same time. Cache data is always consistent but increases write latency.
- Write-Back Cache: Data is first written to the cache, and the cache later asynchronously writes it to the database. Risk of data loss if the cache fails before it writes to the database.
- Cache Invalidation: When the data in the database changes, you explicitly invalidate or remove the affected cache entries.

--------------------------------------------------------------------------------------------------

**What are the different cache design patterns ?**

*Global Cache*

 - Global cache acts as an **independent component**, decoupled from the application or system logic. The two are loosely coupled and can be scaled independently.
 - If the application crashes, restarts, or scales (e.g., adding more servers), the cache remains unaffected and operational, serving data to other instances.
 - The cache can be upgraded, restarted, or scaled without affecting the application.
 - If one application server or instance fails, other instances can still access the centralized cache without interruption.
 - With a dedicated caching layer, multiple application servers or services can share the same cache.

*Local Cache*

 - Local cache resides on the same node as the application or systems utilizing it.
 - When local caches are used, they only benefit the local application consuming the data.
 - If applications had local, isolated caches, they might become inconsistent when one instance updates data while others are unaware.
