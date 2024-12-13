**Database Replication**

An important concept that answers the question _"How to prevent database failures ?"_. In simple words, it involves creating and maintaining multiple copies (replicas) of your data across different servers or nodes.

1. Single Leader Replication / Master-Slave Architecture

- A single node (Leader/Master) to handle all the write operation workloads.
- Multiple nodes to handle the read operation workloads. Read requests are distributed across the follower nodes.
- In case of a follower node failure, a new follower can be added to the pool. It is updated with the latest data using a consistent snapshot of the leader.
- In case of Leader node failure, one of the follower nodes should be promoted as a Leader node.
- Advantages: Simple and Scalable
- Problems: Leader node failure complexities (Risk of data loss, Split Brain scenarios), Write Bottleneck
- **Use Cases: E-commerce Product Catalogs, Social Media Feed pages**

2. Multi Leader Replication

- multiple nodes (leaders) can handle write operations simultaneously.
- Leaders replicate their changes to each other.
- Leader use either Circular, Star, or All for All topology to replicate their changes. Circular and Star are not reliable.
- Advantages: Suitable for systems with geo-distributed writes.
- Problems: Dealing with write conflicts from multiple leaders. (Last Write wins, Version Vectors)
- **Use Cases: Google Docs, Couch DB**
