**Cassandra Database**

**What is Cassandra?**

Apache Cassandra is a No-SQL, wide-column database suitable for applications with write-heavy workloads. Cassandra’s design philosophy prioritizes availability, scalability, and performance for large-scale, distributed systems. Cassandra is optimized for single partition reads and writes.

  - *Data-Organization:* Uses a **wide-column** data organization model. Each table row can have any number and type of columns and must have a **partition key** for accessing data.
  - *Storage Engine:* Uses **LSM-Trees + SS Tables** resulting in faster writes. 
  - *Replication:* All writes are sent to every replica. Write is considered successful based on feedback from a **quorum** of replicas. An **Anti-entropy** process is run in the background to achieve eventual consistency.
  - *Write-Conflict Handling:* Uses the **last write-wins model** to handle conflicts based on time stamps. **Read repair** is also used.
  - *Fault-Tolerance:* All replicas can handle reads and writes.
  - *Indexing:* Clustering Keys are used to create indexes within a partition. It suggests how rows are organized which helps for faster lookup.

------------------------------------------------------------------------------------------------------------------------------------------------------------
**When is it best to use Cassandra?**

Cassandra works best for **Write-heavy Applications** and for applications where data is generally self-contained (no complicated relationships with other rows).

Eg. Logging Systems, Chat applications, Maps, and repository implementations.

------------------------------------------------------------------------------------------------------------------------------------------------------------
**When not to use Cassandra?**

- Read-heavy workloads with complex queries.
- Strong consistency requirements (i.e., where you need strict guarantees about data consistency at all times).
- Complex transactions involving multiple rows or tables.
- Applications that need complex joins or relational-style queries.
- Real-time analytics or aggregation-heavy workloads.
- Small-scale deployments with single-node setups.

------------------------------------------------------------------------------------------------------------------------------------------------------------
