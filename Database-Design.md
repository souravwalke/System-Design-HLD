<h2> Databases </h2>

<u>What is a Database?<u>

A database is an organized collection of data that can be easily accessed, managed, and updated. 

<ins>Objective of a Database</ins>
<ul>
  <li> Provide fast and efficient reads</li>
  <li> Provide fast writes</li>
  <li> Persistent and Reliable storage</li>
</ul>

<ins>Key Components of a Database</ins>
<ul>
  <li>Data: Actual information stored in the database</li>
  <li>Database Managment System: A software used to manage the database Eg. MySQL, Oracle, PostgreSQL</li>
  <li>Schema: The blueprint or structure of the database</li>
  <li>Query Language: A language used to interact with the database. Eg. SQL</li>
</ul>

-------------------------------------------------------------------------------------------------------

<h3> Implementations of a Database </h3>

<b> Naive Implementation using Array of Tuples </b>

<p> This implementation involves the usage of array data structure to implement a database. Each tuple is a row, and the elements of the tuple correspond to the columns. To read the data, it takes 0(n) time as we need to scan through the array. Even update takes O(n) time. Writes are constant time. </p>
<ins>Drawbacks</ins>: Not scalable and cannot handle complex relationships.

<b> Append-only Log </b>

<p> This implementation involves adding a new entry at the end of the log. This way write and update will be constant time. But read would have to be done from bottom to up. This is typically useful when immutability and auditability is crucial. For eg. Blockchain Technology, Banking Applications</p>
<ins>Drawbacks</ins>: Scanning the log for queries is slow and not suitable for large databases.
<ins>Real-World Use Cases</ins>: Apache Kafka, Git

<b> Database Implementation using HashMaps </b>

<p>Here, Data is organized as key-value pairs, where the key is unique, and the value is associated data. This provides constant time read and write access.</p>
<ins>Drawbacks</ins>: When the dataset grows beyond memory capacity and moves to disk, the performance of hash-based operations suffers significantly.

-------------------------------------------------------------------------------------------------------
