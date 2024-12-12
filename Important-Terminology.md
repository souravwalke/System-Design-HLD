**Important Concepts**

*Version Vectors (Multi-leader Replication)*: A version vector is a **data structure** maintained by leader nodes. It **resolves write conflicts** when the independent writes from multiple nodes are propagated to each other. Each node maintains a version vector that indicates the changes it has seen from the other nodes in the network. It helps **establish causal relationships**. When the time comes for eventual consistency, these version vectors are compared. Remember the **Group diary analogy**. Each person will keep a count of the changes they have seen.

*Anti-entropy (Leaderless Database Replication)*: Anti-entropy is a background process that runs to ensure all nodes in a distributed system have the same data. It detects and resolves any inconsistencies between nodes by comparing their data and synchronizing them. Think of it like a **housekeeping** task.

*Database Transcation*: A transaction in a database is a logical unit of work that consists of one or more operations (e.g., queries, updates, inserts) executed as a single entity

