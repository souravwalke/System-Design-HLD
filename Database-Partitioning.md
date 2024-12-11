**Database Sharding/ Partitioning**

As a company grows, the data that it holds also grows. As a result, the size of the tables becomes too big. Database Sharding is the process of splitting this table into many chunks to go on various database nodes. You can perform sharding in multiple ways

  - Key-Based Sharding: A specific column (e.g., user_id, order_id, etc.) is chosen as the shard key. A hash function is applied to the shard key. The output of the hash function determines which shard (partition) the data belongs to


Sharding is generally considered a **last-resort scaling solution** because Sharding adds significant complexity to the system. If the choice of shard key is wrong, it can lead to uneven data distribution (Hot Spots). Recovering back from shard to non-shard architecture is very complex.
    
Resources: https://www.youtube.com/watch?v=YCb-tDQWrXk

