**Database Indexing**

Database indexing is a technique used to improve the speed of data retrieval operations on a database table by creating a data structure (called an index) that acts as a shortcut.

**Types of Indexing**

1. <ins>Hash indexes:<ins> Ideal for smaller datasets. Hash-based data structures perform work well in a disk.
2. <ins>SS Tables and LSM Trees:<ins> Perfect for write-heavy workloads (e.g., logs or messaging systems). Reads take longer due to scanning of SS tables.
3. <ins>B-Trees:<ins> Best for read-heavy workloads.

-------------------------------------------------------------------------------------------------------------------------------------------

**Hash Indexing**

- Hash indexes use a hash function to map keys to specific locations in the index, making equality comparisons lightning-fast.
- Performance can degrade with disk-based systems if the hash table grows too large.
- Not suitable for range queries

**SS Tables and LSM Trees**

- Sorted String Tables (SS Tables): Immutable files that store sorted key-value pairs.
- Log-Structured Merge Trees (LSM Trees): A technique that writes new data to a log file (in memory), periodically merges it with disk-based SS Tables, and compacts them to reduce fragmentation.
- Excellent write performance due to sequential writes.
- Reads can be slower because multiple SS Tables may need to be searched.

**B-Trees**

- A self-balancing tree structure where all keys are stored in sorted order.
- Best for read-heavy workloads or databases with both reads and writes.
- Write performance is slower than hash indexes because tree rebalancing may be required.

