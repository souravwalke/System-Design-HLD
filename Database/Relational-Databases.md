**Relational Databases**

**What are relational databases ?**

Relational databases are all about organizing data in **tables** and managing relationships between those tables to make querying and data management efficient. Examples: MySQL, PostgreSQL, and Oracle DB

Underlying Architecture of Relational Databases

- Uses **B-Trees** for database indexing (Speeds Up Queries and Range Updates)
- B-Trees are created automatically for primary keys and unique constraints.
- Two-phase locking is used commonly to ensure the "Isolation" of transactions.
- All reads and writes go to the disk.

--------------------------------------------------------------------------------------------------------------------------
