**Important Concepts**

Version Vectors (Multi-leader Replication)
  - Version vector is a data structure maintained by leader nodes.
  - It is used to resolve write conflicts when the independent writes from multiple nodes are propogated to each other.
  - Each node maintains a version vector which indicates the changes it has seen from the other nodes in the network. Helps establish causal relationships.
  - When the time comes for eventual consistency, these version vectors are compared.
  - Remember the Group diary analogy. Each person will keep a count of changes they have seen.

Anti-entropy (Leaderless Database Replication)
 - Anti-entropy is a background process that runs to ensure all nodes in a distributed system have the same data.
 - It detects and resolves any inconsistencies between nodes by comparing their data and synchronizing them.
 - Think of it like a **housekeeping** task.

