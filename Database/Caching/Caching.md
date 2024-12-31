**Caching**

```Think of caching like keeping your favorite snacks on the kitchen counter instead of going to the pantry every time you want one. The kitchen counter (cache) is easily accessible, so you can grab your snack (data) quickly, instead of walking to the pantry (database) and spending time finding it.```

-------------------------------------------------

**What is Caching?**

Caching is a mechanism to store frequently accessed data in memory, making read operations faster by eliminating the need to query the database every time. Keeping data closer to the application in memory reduces the latency associated with fetching data from slower, persistent storage (like a database) and speeds up response times.

-------------------------------------------------

**What are the tradeoffs of Caching?**

- Caching stores data in memory much faster than disk-based storage.
  **Tradeoff:**  However, memory is limited and expensive so large amounts of data cannot be stored in a cache and data needs to be selectively added.

- If the data is already in the cache, it’s super fast to retrieve.
  **Tradeoff:**  If the data is not in the cache (a cache miss), it must be fetched from the slower database, which negates the   performance benefit.

- Caching can reduce the load on the primary database by serving data quickly from the cache.
  **Tradeoff:** Cached data may become stale if the underlying data in the database changes but the cache isn’t updated immediately.

- Caching can greatly improve performance for read-heavy applications.
  **Tradeoff:** Implementing cache invalidation and ensuring cache consistency can complicate your system.

-------------------------------------------------
