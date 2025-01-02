**Database Replication**

An important concept that answers the question _"How to prevent database failures ?"_. In simple words, it involves creating and maintaining multiple copies (replicas) of your data across different servers or nodes.

------------------------------------------------------------------------------------------------------------------------------------------------------

**What is Single Leader Replication / Master-Slave Architecture?**

- A single node (Leader/Master) to handle all the write operation workloads.
- Multiple nodes to handle the read operation workloads. Read requests are distributed across the follower nodes.
- In case of a follower node failure, a new follower can be added to the pool. It is updated with the latest data using a consistent snapshot of the leader.
- In case of Leader node failure, one of the follower nodes should be promoted as a Leader node.
- Advantages: Simple and Scalable
- Problems: Leader node failure complexities (Risk of data loss, Split Brain scenarios), Write Bottleneck
- **Use Cases: E-commerce Product Catalogs, Social Media Feed pages**

------------------------------------------------------------------------------------------------------------------------------------------------------

**What is Multi Leader Replication?**

- multiple nodes (leaders) can handle write operations simultaneously.
- Leaders replicate their changes to each other.
- Leader use either Circular, Star, or All for All topology to replicate their changes. Circular and Star are not reliable.
- Advantages: Suitable for systems with geo-distributed writes.
- Problems: Dealing with write conflicts from multiple leaders. (Last Write wins, Version Vectors)
- **Use Cases: Google Docs, Couch DB**

------------------------------------------------------------------------------------------------------------------------------------------------------

**What is Chain Replication?**

Chain Replication is an approach to replicating data across multiple nodes that involves arranging the nodes in a chain. Chain Replication excels at strong consistency and sequential ordering. 

- The chain consists of a head node, multiple replica nodes, and a tail node.
- All writes by the client are written to the head node, and this data is replicated to the chain of replica nodes and finally reaches the tail node.
- The tail node acknowledges the write and sends a response which is then propagated through the replica nodes and finally the head. Only then the write is considered successful.
- All reads are done on the tail node which stores the most up-to-date data. 
