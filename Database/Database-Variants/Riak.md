**Riak**

**What is Riak?**

Riak is a distributed NoSQL **key-value** database designed for high availability, fault tolerance, and scalability.  

**What are the design principles of Riak?**

- Riak’s data is distributed across multiple nodes in a cluster, ensuring that no single point of failure can bring the system down.
- Riak follows the principle of **eventual consistency**, meaning that after a write operation, the system guarantees that all replicas will eventually become consistent.
- Data is split into partitions (or "buckets"), which are distributed across nodes in the cluster using **consistent hashing**
- It employs techniques like Replication and Hinted Handoff to make sure data isn't lost when nodes go down.

**What are the best use-cases for Riak?**

1. Store session data for users in web applications.
2. Applications that handle real-time data, such as user activity tracking or IoT device data, can benefit from Riak’s ability to scale horizontally and handle high traffic volumes.
3. Riak was used to store large amounts of catalog data.

