**Blob Storage**

--------------------------------------------------------------------------------------------------------------------------------------

**What is Blob storage and why is it used?**

Blob storage refers to storing large amounts of unstructured data, such as text, images, videos, or binary files, in an efficient, scalable, and secure manner. 

Sometimes you'll need to store large, unstructured blobs of data. This could be **images, videos, or other files**. Storing these large blobs in a **traditional database** is **expensive and inefficient** and should be avoided when possible. Instead, you should use a blob storage service like **Amazon S3 or Google Cloud Storage**. 

Some common examples of when to use blob storage:

- Design YouTube -> Store videos in blob storage, and store metadata in a database.
- Design Instagram -> Store images & videos in blob storage, and store metadata in a database.
- Design Dropbox -> Store files in blob storage, and store metadata in a database.

--------------------------------------------------------------------------------------------------------------------------------------

**How does Blob Storage work?**

Blob storage services are simple. You can upload a blob of data and that data is stored and get back a URL. You can then use this URL to download the blob of data. Often blob storage is used in conjunction with CDN for faster retrieval of static data. 

--------------------------------------------------------------------------------------------------------------------------------------

**Why can't we use blob storage instead of a traditional database as our primary data store?**

Although blob storage is simple and inexpensive, it has several limitations.
  - Blob storage lacks rich querying capabilities like SQL-based joins, aggregations
  - Blob storage is optimized for large, sequential reads or writes, not for low-latency random access
  - Blob storage is optimized for write-once, read-many workloads. While updates are possible, they can be inefficient because you often need to rewrite the entire blob.

--------------------------------------------------------------------------------------------------------------------------------------
