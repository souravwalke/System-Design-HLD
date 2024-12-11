**Database Sharding/ Partitioning**

As the company grows, the data that it holds also keeps growing. As a result, the size of the tables becomes too big. How do you tackle this?

1. Your first action would be to scale vertically i.e. Upgrade your database server with more RAM, CPU, or storage to handle the increased workload. This is straightforward and doesn't require any architectural changes. But you can only scale so much.

2. Another possible action would be to archive historical data to a separate archive database or cold storage.

3. Finally, if your data continues to grow beyond what a single server can handle or you want to scale massively, then you can consider **sharding**. Sharding is generally considered a **last-resort scaling solution** because Sharding adds significant complexity to the system.

----------------------------------------------------------------------------------------------------------------------------------
**What is Database Sharding ?**

Sharding is splitting data into logical partitions across multiple servers to distribute storage and workload.

How is it done?

1. *Key-Based Sharding*: You choose one or more columns in the table as your *shard key*. There is a *hash function* through which this shard key is passed through. The hash function returns the actual node to which this data belongs. This is an effortless way of sharding and effectively distributing the data. But everything depends on the choice of a hash function. A Wrong hash function will lead to unequal distribution. Adding or removing shards is also hard, as the hash function changes, and most data must be redistributed across shards.

2. *Range-Based Sharding*: Data is partitioned based on ranges of values for a particular column, such as timestamp, price, or user_id. It is better than Key-based because You can easily add a new shard by creating a new range without much redistribution. Range selection should be such that it is non-temporal otherwise most data falls into one range and would lead to hotspots. This type of sharding is best when you have to deal with range-queries a lot in your application.

3. *Directory-Based Sharding*: A lookup table is used to map data to specific shards. Instead of directly using a shard key to decide where data goes, the directory stores the mapping of the data to the appropriate shard. You can add shards easily without directly affecting the data. A major disadvantage is that it creates a single point of failure (if the node containing the central directory goes down). Also increases latency as each query has to first go to the lookup table and then to the actual shard.
















Resources: https://www.youtube.com/watch?v=YCb-tDQWrXk

