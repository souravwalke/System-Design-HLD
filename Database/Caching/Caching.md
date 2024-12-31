**Caching**

```Think of caching like keeping your favorite snacks on the kitchen counter instead of going to the pantry every time you want one. The kitchen counter (cache) is easily accessible, so you can grab your snack (data) quickly, instead of walking to the pantry (database) and spending time finding it.```

**What is Caching?**

Caching is a mechanism to store frequently accessed data in memory, making read operations faster by eliminating the need to query the database every time. Keeping data closer to the application in memory reduces the latency associated with fetching data from slower, persistent storage (like a database) and speeds up response times.

**What are the tradeoffs of Caching?**

  - Caching stores data in memory, which is much faster than disk-based storage. However, memory is limited and expensive so large amounts of data cannot be stored in a cache and data needs to be selectively added to the cache.
  - If the data is already in the cache, it’s super fast to retrieve. If the data is not in the cache (a cache miss), it must be fetched from the slower database, which negates the   performance benefit.
  - Caching can reduce the load on the primary database by serving data quickly from the cache. But the data in the cache can become stale if recent changes are not updated to the cache.
