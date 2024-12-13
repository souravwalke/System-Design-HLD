**Important Concepts**
---------------------------------------------------------------------------------------------------------------------------------------------------

*Version Vectors (Multi-leader Replication)*: A version vector is a **data structure** maintained by leader nodes. It **resolves write conflicts** when the independent writes from multiple nodes are propagated to each other. Each node maintains a version vector that indicates the changes it has seen from the other nodes in the network. It helps **establish causal relationships**. When the time comes for eventual consistency, these version vectors are compared. Remember the **Group diary analogy**. Each person will keep a count of the changes they have seen.

---------------------------------------------------------------------------------------------------------------------------------------------------
*Anti-entropy (Leaderless Database Replication)*: Anti-entropy is a background process that runs to ensure all nodes in a distributed system have the same data. It detects and resolves any inconsistencies between nodes by comparing and synchronizing their data. Think of it like a **housekeeping** task.

---------------------------------------------------------------------------------------------------------------------------------------------------
*Database Transaction*: A transaction in a database is a **logical unit of work** that consists of one or more operations (e.g., queries, updates, inserts) executed as a single entity. Sending money from one account to another is a database transaction.

---------------------------------------------------------------------------------------------------------------------------------------------------
*ACID Properties*: 
  - **Atomicity**: All operations within the transaction are completed, or none are applied (all-or-nothing).
  - **Consistency**: ensures that a database follows all its rules, constraints, and relationships before and after a transaction.
  - **Isolation**: Transactions are executed in isolation to avoid conflicts or interference.
  - **Durability**: Once a transaction is successfully committed, its changes are permanent.

---------------------------------------------------------------------------------------------------------------------------------------------------
*Dirty Read*: A dirty read occurs when a transaction reads data that has been modified by another transaction but has not been committed yet.

*Dirty Write*: Two transactions update the same piece of data simultaneously without knowing about each other's changes.

*Read Skew*: This problem occurs when one transaction is reading through data executing multiple read queries and in between this execution, another transaction updates the data that was read before resulting in inconsistent or incorrect data being used by the first transaction.

---------------------------------------------------------------------------------------------------------------------------------------------------



