**Hadoop Distributed File System**

**What is HDFS?**

 It is a distributed file system optimized for large-scale data processing. It breaks down large files into smaller chunks and distributes these chunks across a cluster of commodity hardware nodes.

 **What is the design principle behind HDFS ?**

  - HDFS uses a Write-Once, Read-Many Model. Files are written once and then read multiple times. (Batch Processing)
  - HDFS excels at storing and processing large files (gigabytes to petabytes in size). Files are broken into blocks.
  - Data blocks are replicated (default: 3 copies) across multiple nodes.
  - HDFS consists of multiple types of nodes. A Namenode stores metadata (e.g., file locations, permissions). DataNode (Worker Nodes) Stores the actual data blocks.

**When should you use HDFS ?**

 - Batch Processing: HDFS is highly suitable if you need to perform Batch processing where large datasets are analyzed.
 - Data Lakes: Storing raw, semi-structured, or unstructured data for analytics.
 - Log Processing: Handling terabytes of server logs or clickstream data.

```Think of HDFS as a library where instead of keeping the entire book in one place, the pages are split into chapters and stored across multiple shelves (nodes). There's a librarian (NameNode) who keeps track of where each chapter is stored.```
