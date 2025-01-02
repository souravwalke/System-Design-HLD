**Important Concepts**
---------------------------------------------------------------------------------------------------------------------------------------------------

**Version Vectors (Multi-leader Replication)**: A version vector is a **data structure** maintained by leader nodes. It **resolves write conflicts** when the independent writes from multiple nodes are propagated to each other. Each node maintains a version vector that indicates the changes it has seen from the other nodes in the network. It helps **establish causal relationships**. When the time comes for eventual consistency, these version vectors are compared. Remember the **Group diary analogy**. Each person will keep a count of the changes they have seen.

---------------------------------------------------------------------------------------------------------------------------------------------------
**Anti-entropy (Leaderless Database Replication)**: Anti-entropy is a background process that runs to ensure all nodes in a distributed system have the same data. It detects and resolves any inconsistencies between nodes by comparing and synchronizing their data. Think of it like a **housekeeping** task.

---------------------------------------------------------------------------------------------------------------------------------------------------
**Database Transaction**: A transaction in a database is a **logical unit of work** that consists of one or more operations (e.g., queries, updates, inserts) executed as a single entity. Sending money from one account to another is a database transaction.

---------------------------------------------------------------------------------------------------------------------------------------------------
*ACID Properties*: 
  - **Atomicity**: All operations within the transaction are completed, or none are applied (all-or-nothing).
  - **Consistency**: ensures that a database follows all its rules, constraints, and relationships before and after a transaction.
  - **Isolation**: Transactions are isolated to avoid conflicts or interference.
  - **Durability**: Once a transaction is successfully committed, its changes are permanent.

---------------------------------------------------------------------------------------------------------------------------------------------------
**Dirty Read**: A dirty read occurs when a transaction reads data modified by another transaction but has not been committed yet.

**Dirty Write**: Two transactions update the same piece of data simultaneously without knowing about each other's changes.

**Read Skew**: This problem occurs when one transaction is reading through data executing multiple read queries and in between this execution, another transaction updates the data that was read before resulting in inconsistent or incorrect data being used by the first transaction.

---------------------------------------------------------------------------------------------------------------------------------------------------
**TimeStamp Conflict Resolution**: Timestamps cannot be reliable in resolving conflicts because nodes have independent clocks, and even with synchronization protocols like NTP (Network Time Protocol), there can still be clock skew or drift.

---------------------------------------------------------------------------------------------------------------------------------------------------
**Analytical Databases** Analytical databases analyze large datasets and run complex queries. They focus on read-heavy workloads.

**ETL (Extract, Transform, Load)** is moving data from a transactional database (or any other source) to an analytical database for analysis.

---------------------------------------------------------------------------------------------------------------------------------------------------
**Batch Processing** Batch processing is a method of processing large volumes of data in batches. Data is collected over time and processed all at once, often during off-peak hours. Tools used: Hadoop, Apache Spark. Typically used on top of a distributed file system. Useful in Data Warehousing, Payroll systems, etc.

**Stream Processing** is a method of processing data in real-time as it arrives. It works on a continuous stream of incoming data like sensor data, and stock prices.

---------------------------------------------------------------------------------------------------------------------------------------------------
**Consistent Hashing** is a hashing technique used to distribute data across a dynamic set of nodes (servers) while minimizing the need for data reorganization when nodes are added or removed. It consists of a Hash Ring. Both data (keys) and nodes are mapped onto this hash ring using a hash function. Each data key is assigned to the next node clockwise on the ring.
When a node is added or removed, only a small portion of the data needs to be redistributed to maintain balance, unlike traditional hashing, which might require rehashing all data.

---------------------------------------------------------------------------------------------------------------------------------------------------
**Wide Column Databases** are a type of NoSQL database where data is stored as rows, but each row can contain any number of columns. It provides more flexibility than relational databases as it does not enforce any fixed schema. Popular wide-column databases are Apache Cassandra, and HBase.

Eg: Row 1: {Name, Age, Address} , Row 2: {Name, Email, LastLogin}

---------------------------------------------------------------------------------------------------------------------------------------------------
**Dynamo-Style Architecture** refers to the design principles outlined in Amazon's Dynamo paper

  - Writes are distributed to multiple nodes, and the system eventually synchronizes data. (Eventual Consistency)
  - Data is replicated across multiple nodes for fault tolerance. (Data Replication)
  - If a node is unavailable, another temporarily takes over its responsibilities and hands back the data when the original node recovers. (Hinted Handoff)
  - The system uses a quorum mechanism (e.g., majority reads/writes) to balance consistency and availability. (Quorum)
  - Partition is done among nodes using consistent hashing.

---------------------------------------------------------------------------------------------------------------------------------------------------

**Search Indexes** are specialized data structures that speed up data retrieval by mapping terms to their occurrences, allowing efficient searches in databases or text collections. 

**Lucene**, a powerful Java-based search library, builds and manages such indexes using an inverted index to map terms to document IDs. It excels at full-text search, handling prefix queries (e.g., app*) efficiently through lexicographical ordering and Finite State Transducers (FSTs).

---------------------------------------------------------------------------------------------------------------------------------------------------
