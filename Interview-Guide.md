**Quick Interview Guide**

1. Almost all system design problems will require you to store some data and you're most likely going to be storing it in a database or Blob Storage.
  
2. Choose PostgreSQL for relational databases and DynamoDB for NoSQL in most cases.
    - When data relationships are complex (e.g., foreign keys), querying is heavy, and transactions require ACID guarantees, PostgreSQL shines.
    - When you need massive scalability, fault tolerance, and serverless architecture, DynamoDB is hard to beat. DynamoDB integrates seamlessly with AWS services.
       
3. Blob Storage (S3 or Google Cloud Storage) is perfect for storing large unstructured blobs of data like videos, photos, etc. Often used for static data along with CDN.

4. If full-text search is a part of the design, we need to use search-optimized databases (ElastiSearch). They build inverted indexes to make full-text searches faster.

5. An API gateway sits in front of your system and is responsible for routing incoming requests to the appropriate backend service. Use it as your first point of contact for your     
   clients.
   
6. You need a load balancer wherever you have multiple machines capable of handling the same request. Add one only to the front of the design as an abstraction.

7. 
