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

