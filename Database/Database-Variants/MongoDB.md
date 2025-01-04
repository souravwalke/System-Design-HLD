**MongoDB**

MongoDB is a NoSQL database that stores data in a flexible, document-oriented format instead of traditional rows and columns like relational databases. It is one of the most popular NoSQL databases in the world, widely used for modern, scalable applications.

------------------------------------------------------------------------------------------------------------------

**What are some of the best features of MongoDB?**

1. Data is stored as **JSON-like documents**. Each document can have its own unique structure, making it ideal for unstructured or semi-structured data.
2. MongoDB **doesn’t** require a **fixed schema**, so fields in documents can vary.
3. MongoDB is designed for **horizontal scaling**.
4. Supports powerful querying with filters, projections, aggregations, and indexes.
5. MongoDB supports quorum reads and writes through the use of read concerns and write concerns. 

-------------------------------------------------------------------------------------------------------------------

**What Does Document-Style Storage Mean?**

In MongoDB, document-style storage means that data is stored as documents, which are JSON-like objects (internally stored as BSON). Each document is a self-contained, flexible data structure with fields (key-value pairs) and documents within another document do not need the same structure. This makes it different from the rigid rows and columns in a relational database.

{
    "_id": "64afc0b1e2d1",
    "name": "John Doe",
    "email": "johndoe@example.com",
    "address": {
      "street": "123 Elm St",
      "city": "Springfield",
    },
    "hobbies": ["reading", "gaming", "traveling"],
    "isActive": true
  }

-------------------------------------------------------------------------------------------------------------------

**When should I pick MongoDB over relational databases ?**

You can choose MongoDB:
    
- If your data structure changes often or varies across records.
- If you need to handle large volumes of writes and want to scale rapidly.
- If you want to avoid complex joins and have most of your data self-contained in a document.
- MongoDB’s schema-less nature is a good fit for agile projects or prototypes.
- MongoDB’s support for geospatial indexes makes it ideal for location-based applications.

-------------------------------------------------------------------------------------------------------------------
