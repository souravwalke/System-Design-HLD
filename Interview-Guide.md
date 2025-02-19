**Quick Interview Guide**

1. Almost all system design problems will require you to store some data and you will most likely be storing it in a database or Blob Storage.
  
2. Choose PostgreSQL for relational databases and DynamoDB for NoSQL in most cases.
    - When data relationships are complex (e.g., foreign keys), querying is heavy, and transactions require ACID guarantees, PostgreSQL shines.
    - When you need massive scalability, fault tolerance, and serverless architecture, DynamoDB is hard to beat. DynamoDB integrates seamlessly with AWS services.
       
3. Blob Storage (S3 or Google Cloud Storage) is perfect for storing large unstructured blobs of data like videos, photos, etc. Often used for static data along with CDN.

4. If full-text search is a part of the design, we need to use search-optimized databases (ElastiSearch). They build inverted indexes to make full-text searches faster.

5. An API gateway sits in front of your system and is responsible for routing incoming requests to the appropriate backend service. Use it as your first point of contact.
   
6. You need a load balancer wherever you have multiple machines capable of handling the same request. Add one only to the front of the design as an abstraction.

7. Message Queues (Apache Kafka) serve as buffers for burst traffic or as a means of distributing work across a system. Queues are suited for asynchronous processing and add latency   
   to the system. Hence don't use queues when strong low latency is a requirement.

8. Streams are a continuous flow of data that can be processed and consumed in near real-time. Use streams (Apache Flink/Kafka) when asked to design systems that need real-time 
   analytics, continuous tracking of GPS locations, or real-time chat application.

9. Distributed locks are perfect for situations where you need to lock something across different systems or processes for a reasonable time. Useful for use cases like ticket booking 
   applications, e-commerce cart checkout, flash sales, and online auctions.

10. One common way to scale your system and achieve low latency is by using a distributed cache. You'll want to use a cache to save aggregated metrics or speed Up Expensive 
    queries. The two most common in-memory caches are Redis and Memcached.

11. CDN is a type of cache that delivers content to users based on their geographic location. It is typically used to cache static media assets like images and videos. 

------------------------------------------------------------------------------------------------------------------------------------------------

**Important Facts**

-  Access Time Comparisons: Memory (RAM) < SSD < HDD (Hard Disk)
-  1 Day = 86400 secs
-  Maximum Known Capacity: Memory (8TB) < SSD (100 terabytes) < HDD (PB)

------------------------------------------------------------------------------------------------------------------------------------------------

**Questions to ask about Non-functional requirements**

1. Should I prioritize the consistency of the system over availability? or are there certain aspects of the system where I need to prioritize availability?
2. What is the number of daily active users (DAU)?
3. What is the read-to-write ratio of the system?
4. Are there any scalability trends I need to know?
5. What should be the latency requirement of the system?

------------------------------------------------------------------------------------------------------------------------------------------------

**General Guidelines**

1. Always avoid passing user ID or sensitive identifiers in the request body. Use authentication mechanisms like JWT or session cookies to ensure security and minimize the risk of tampering or unauthorized access.

2. While designing APIS, use the following notations in the correct context
   - GET - Used when a request to read from the database and no write is involved.
   - POST - Used when a request adds data to the database. I am not updating a column but adding a new row.
   - PUT/PATCH - Used when a request updates an existing row.

3. There are three ways of reducing latency in any system
   - Optimizing the database querying and introducing appropriate indexing.
   - Introducing a Redis cache and caching data whenever possible and reducing disk fetches.
   - By Processing the tasks asynchronously using a message queue. (Amazon SQS)

------------------------------------------------------------------------------------------------------------------------------------------------

1. First I would like to establish an agenda for structuring the design interview.
2. I will initially gather some functional and non-functional requirements for the system we will be designing and agree upon a couple of core functionalities to be implemented.
3. Ideally candidates do some kind of capacity estimations here but I would like to do these calculations on the fly and as and when it would impact my design choices.
4. Next I will define the core entities that would be persisted and exchanged in the APIs.
5. Then I will design the core APIs that will serve as some kind of agreement between the client and server and in a way implement the functional requirements.
6. Next I would design a high-level design to satisfy the core functional requirements.
7. We can then discuss parts of the design that would need a deeper dive and discuss any tradeoffs.
