**Database Sharding/ Partitioning**

As the company grows, the data that it holds also keeps growing. As a result, the size of the tables becomes too big. How do you tackle this?

1. Your first action would be to scale vertically i.e. Upgrade your database server with more RAM, CPU, or storage to handle the increased workload. This is straightforward and doesn't require any architectural changes. But you can only scale so much.

2. Another possible action would be to archive historical data to a separate archive database or cold storage.

3. Finally, if your data continues to grow beyond what a single server can handle or you want to scale massively, then you can consider **sharding**. Sharding is generally considered a **last-resort scaling solution** because Sharding adds significant complexity to the system.

----------------------------------------------------------------------------------------------------------------------------------
**What is Database Sharding ?**

Sharding is basically, splitting data into logical partitions across multiple servers to distribute both storage and workload.

    
















Resources: https://www.youtube.com/watch?v=YCb-tDQWrXk

