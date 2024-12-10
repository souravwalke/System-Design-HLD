**Database Sharding/ Partitioning**

As a company grows, the data that it holds also grows. As a result, the size of the tables becomes too big. Database Sharding is the process of splitting this table into many chunks to go on various database nodes.

Sharding is generally considered a **last-resort scaling solution** because:
  - Sharding adds significant complexity to the system.
  - if the choice of shard key is wrong, it can lead to uneven data distribution (Hot Spots).
  - Recovering back from shard to non-shard architecture is very complex.




Resources: https://www.youtube.com/watch?v=YCb-tDQWrXk

