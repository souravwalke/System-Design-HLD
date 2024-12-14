**Relational Databases**

**What are relational databases ?**

`A relational database is like your strict grandfather. He has High Moral Values (ACID properties), Goes by the Rule Book (Fixed Schema), Slow but Thorough(Latency), and is very reliable.`



Relational databases are all about organizing data in **tables** and managing relationships between those tables to make querying and data management efficient. Examples: MySQL, PostgreSQL, and Oracle DB

Underlying Architecture of Relational Databases

- Uses **B-Trees** for database indexing (Speeds Up Queries and Range Updates)
- B-Trees are created automatically for primary keys and unique constraints.
- Two-phase locking is used commonly to ensure the "Isolation" of transactions.
- All reads and writes go to the disk.

--------------------------------------------------------------------------------------------------------------------------
**What are the shortcomings of relational databases?**

- Doesn’t scale well horizontally - Sharding a relational database adds overheads on the network making the read/write calls slower.
- 2PL makes the relational databases slower because locking involves multiple steps which adds latency.
- B-Trees makes writing slower.
- Relational databases require a fixed schema. This rigidity made it hard to adapt to dynamic and unstructured data. 
--------------------------------------------------------------------------------------------------------------------------
**When are relational databases not suitable to be used?**

- When you have Huge Volumes of Unstructured or Semi-Structured Data. Eg. IoT devices
- When you have massive scaling needs. Eg. Social media platforms
- When your systems need to process millions of writes/ reads per second. Eg. Real-time analytics systems
- When Low latency is the highest priority. Eg. High-Frequency Trading, Gaming, Streaming Applications
- When schema needs frequent changes.

RDBMS should not be used when your **application demands scalability, flexibility, high throughput, or low latency, or when the data is unstructured or globally distributed**
