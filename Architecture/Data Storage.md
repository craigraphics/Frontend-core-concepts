## Relational Databases
### Data is stored in tables.
- Each row in the table represents a single record.
- Records are related to each other through a predefined set of columns that they all have.
- Each column in a table has a name, a type and optionally a set of constraints.
- Each record in a table is uniquely identified by a primary key which can be represented by one column or a set of columns in a table.

### Schema
- The structure (schema) of each table is defined ahead of time.
- This gives us the knowledge of what each record must have.
- Because of this, we can use a robust query language to analyze and update the table data.

### SQL - Structured Query Language
- The industry-standard scripting language to perform such queries is called SQL.
- Different relational database implementations have their own additional features to their version of that language.
- The majority of standard operations are the same for all relational databases.

### Advantages
- Ability to form complex and flexible queries.
- Efficient storage.
- Natural structure of data for humans.
- ACID transactions (atomicity, consistency, isolation, durability) - a sequence of operations that for an external observer should appear a single operation.
    - Atomicity - Each set of operations that are part of one transaction either appear all at once or don't appear at all.
    - Consistency - Guarantees that a transaction that was already committed is seen by all future queries/transactions. Also guarantees constraints.
    - Isolation - related to atomicity in the context of concurrent operations performed on our database.
    - Durability - once a transaction is complete, its final state will persist and remain permanently inside the database.
      
### Disadvantages
- Rigid structure
    - the schema has to be defined ahead of time before we can use the table.
    - If we want to change the schema of a table by adding/removing a column, we would have some maintenance time.
    - We need to plan ahead in designing the scheme of our tables, so as to not change the schema very often or at all.
- Hard to maintain.
- Slower read operations.

### When to choose a relational database
- Perform complex and flexible queries to analyze our data.
- Guarantee ACID transactions between different entities in our database.

### When Not to choose a relational database
- There isn't any inherent relationship between different records that justifies storing our data in tables.
- Read performance is the most important quality that we need for providing a good user experience.

## Non-relational Databases
- A relatively new concept that became popular in the mid-2000s.
- Solved drawbacks of relational databases.
- Don't store data in tables.
- Support more native data structures to programming languages.
- This eliminates the need for an ORM (Object Relational Mapping).
- Non-Relational Databases are designed for faster queries in contrast with Relational Databases that are designed for efficient storage.

### Trade-offs
- When we allow flexible schemas, we lose the ability to easily analyze those records.
- Analyzing multiple groups of records (join operations) also becomes hard.
- ACID transactions are rarely supported by non-relational databases.

### Categories
- Key/Value store - can be seen as a large-scale hashtable or dictionary.
    - It has very few constraints on the type of values we have for each key.
- Document Store
    - We can store collections of documents with more structure inside each document.
    - Each document is an object with different attributes.
    - Those attributes can be of different types.
    - Documents inside a document store are easily mapped to objects inside a programming language.
-  Graph Database
    - Extension of a document store with additional capabilities to link, traverse analyze multiple records more efficiently.
    - Optimized for navigating and analyzing relationships between different records.
    - Fraud detection
### When to choose a non-relational database
- Analyze our use case.
- Figure out which properties of a database are the most important to us.
- Are superior when it comes to query speed.
- Perfect choice for caching.
- Handling real-time big data.
- Data is not structured.
- Different records can contain different records.
### Examples
- User profiles
- Content management

### Solutions
#### Key/Value Stores Examples
- Redis
- Aerospike
- Amazon DynamoDB
#### Document Store Examples
- Cassandra
- MongoDB
#### Graph Databases Examples
- Amazon Neptune
- NEO4J

## Techniques to improve performmance, availability & scalability of databases.
- Indexing - which improves the performance of database by speeding up search and retrieval operations.
- Replication - which improves our system availability and performance through increased throughput.
- Partioning - improves database scalability by splitting up our data across on multiple databases running on different computers.

## CAP Theorem
- In the presence of a Network Partition, a distributed database cannot guarantee both Consistency and Availability and has to choose only one of them. - Eric Brewer
- C (Consistency)
    - Every read request receives either the most recent write or an error.
    - A consistent Database will return the value of the record that corresponds to the most recent write operation.
    - All clients see the same value at the same time regardless of which instance of database they talk to.
- A (Availability)
    - Every request receives a non-error response, without the guarantee that it contains the most recent write.
    - Different clients may get different versions of a particular record.
    - All requests return succesfully with a valid value.
- P (Partition Tolerance)
    - The system continues to operate despite an arbitrary number of messages being lost or delayed by the network between different computers.
- CAP Theorem tells us that when we either choose or configure a database, we have to drop one of those three properties:
    - CA - no Partition Tolerance.
    - CP - no Availability.
    - AP - no Consistency.

## Unstructured Data
- Data that doesn't follow a particular structure, schema or model.
- Examples are audio, video, image or documents.
- Blob - Binary Large Object.

### Where to store unstructured data?
- Some databases allow storing blobs.
- Relational/non-relational databases are not optimized for unstructured data.
- Databases have size limits on binary objects (~megabytes).

### Use Cases
- Upload user data. This data can be compressed, transcoded or shared, or used for backup purposes.
- Backup and Archiving. We can take snapshots that will be stored in binary formats of our databases for disaster recovery or for archiving.
- Web Hosting - images, thumbnails and digital downloads.
- Machine Learning and Big Data Analytics.

### Distributed File System (DFS) Solution
- Provide us with the same abstraction as we store data on our local hard drive, that instead of using a single storage device we have a network of storage devices.
### Object Store
- Scalable storage solution for storing unstructured data at internet scale.
- It has linear scalability.
- No limit to the number of objects we can store.
- Very high limit on a single object size (~5-10 Terabytes).
- Provides an HTTP + REST API.
- Support for Versioning out of the box.
### Cloud and Open Source Solutions
#### Cloud-Based
- Amazon S3 - Amazon's highly scalable cloud storage service that stores object data within buckets. Designed to store and protect any amount of data for various use cases, such as websites, cloud-native applications, backups, archiving machine learning and analytics.
- GCP Storage - Google's service for storing unstructured data.
- Azure Blob Storage - Fully managed enterprise-ready Object Storage Service to store and access any amount of data from anywhere.
#### Open Source
- OpenIO -  software-defined open-source object storage solution ideal for Big Data, HPC and AI. It is S3 compatible and can be deployed on-premises or cloud-hosted on any hardware that you choose.
- MinIO - High performance, S3-compatible object storage. It is native to Kubernetes and 100% open source under GNU AGPL v3.
- Cepth - reliable and scalable storage that provides an unified storage service with object, block and file interfaces from a single cluster.
