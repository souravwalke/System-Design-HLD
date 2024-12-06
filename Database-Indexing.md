#Database Indexing

Database indexing is a technique used to improve the speed of data retrieval operations on a database table by creating a data structure (called an index) that acts as a shortcut.

#Types of Indexing

1. Hash indexes: Ideal for smaller datasets. Hash-based data structures perform work well in a disk.
2. SS Tables and LSM Trees: Better for write-heavy workloads. Reads take longer due to scanning of SS tables.
3. B-Trees: Best for read-heavy workloads.

-------------------------------------------------------------------------------------------------------------------------------------------

#Hash Indexing

W
