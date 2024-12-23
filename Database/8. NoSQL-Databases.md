**What are Non-relational Databases?**

`A NoSQL database is like your cool cousin. He is Flexible (Schema-less), fast but Sometimes Messy (Eventual Consistency), and Easily Scales (Distributed Nature)`

Non-relational databases (often referred to as NoSQL databases) are databases that store data in a non-tabular format. They provide more flexibility in data structure and are designed to handle large volumes of unstructured, semi-structured, or rapidly changing data.

**Underlying Architecture of No-SQL Databases**

  - Objects are **self-contained documents** in NoSQL databases. i.e. it refers to the fact that each document holds all the data for an object.
  - Data is stored in a **single disk block** (or nearby blocks) making read/write faster.
  - Follows **eventual consistency**, updates to the database might not be immediately visible across all nodes but will eventually propagate to all replicas over time.
  - Best supports **horizontal scaling** via sharding.

---------------------------------------------------------------------------------------------------------------------------------------------------------------

**What are the shortcomings of non-relational databases?**

- Data duplication is a major concern. The application has to ensure that data duplication is handled.
- NoSQL databases do not have a universal query language or standardization. Each has its own query language.
- Relational databases have been around for decades and are highly mature, well-documented, and battle-tested.
- Causes data inconsistencies due to the usage of eventual consistency methods. 

---------------------------------------------------------------------------------------------------------------------------------------------------------------
