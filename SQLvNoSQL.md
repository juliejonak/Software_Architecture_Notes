# SQL versus NoSQL Databases

When considering possible database options, the main comparison you might be asked about is the choice between SQL and NoSQL. Understanding each and their differences will help validate your decision.

<br>

# SQL Databases

SQL databases are primarily Relational Databases (RDBMS) based on tables. SQL databases represent data in the form of tables that consist of `n` rows of data (like Excel). 

SQL databases have a predefined schema and are _vertically_ scalable by increasing the horse-power of the hardware -- improving the CPU, RAM, SSD on a single server.

They use SQL (structured query language) for defining and manipulating data. SQL databases are a good fit for complex query intensive environments and tend to be more powerful.

SQL databases do not excel with hierarchical data storage. They're a best fit for heavy duty transctional type applications, with the inherent stability that promises data integrity.

SQL has been the standard for many decades, which means more vendors and professionals can provide consulting help.

The core properties of SQL database are ACID: Atomicity, Consistency, Isolation and Durability.

Common SQL databases are MySql, Oracle, Sqlite, Postgres and MS-SQL.

<br>

# NoSQL

NoSQL databases are non-relational or distributed databases. They are based on documents, key-value pairs, graphs or wide-column stores, without standard schema definitions that must be followed.

They have a dynamic schema for unstructured data. They are horizontally scalable by increasing the number database servers in the infrstructure to handle large traffic.

Queries are focused on collection of documents, sometimes call UnQL (Unstructured Query Language), which can vary from database to database.

NoSQL databases are not a good fit for complex queries because they don't have standard interfaces to perform them. They are generally less powerful than SQL databases.

NoSQL fits better for hierarchical data storage like with key-value pair storage similar to JSON data. It's highly preferred for large data sets (i.e. handling Big Data). 

There is less professional support for NoSQL, so many databases are still reliant upon community support to help setup and deploy.

NoSQL follows the CAP theorem: Consistency, Availability and Partition tolerance.

Common NoSQL databases are MongoDB, BigTable, Redis, RavenDb, Cassandra, Hbase, Neo4j, and CouchDb.

# When do I use each?

Not every database fits every business' needs. Many companies rely on relational and non-relational databases for different tasks depending on the need for speed, scalability, and structure.

1. *Do you need ACID compliancy?*

If being ACID (Atomicity, Consistency, Isolation & Durability) is needed to reduce anomalies and protect the integrity of your database, then choose SQL/relational.

If flexibility and speed matter more than data integrity, NoSQL is your best option.

<br>

2. *Is your data structured and rarely changes?*

If business is not growing exponentially or the system doesn't need to handle a variety of data types or high traffic volume, then SQL is your best bet.

If business is expanding rapidly and the needs of the database are in flux, NoSQL is the best choice.

<br>

3. *Do you use cloud computing or storage?*

Cloud-based storage requires data to be easily spread across multiple servers for scaling. Most NoSQL databases are designed to use affordable on-site hardware for testing, but push production to the cloud.

<br>

4. *Are you in rapid development?*

Typically with Agile methodologies, a relational database can be a hinderance due to slow pivoting on the schema. A NoSQL database doesn't require as much preparation and can shift as business needs change.

<br>

# Additional Reading

[SQL vs NoSQL](https://www.thegeekstuff.com/2014/01/sql-vs-nosql-db)  

[SQL or NoSQL - that is the question](https://blog.panoply.io/sql-or-nosql-that-is-the-question)  

[Applications that Work Best with NoSQL](https://www.clariontech.com/blog/applications-that-work-best-with-nosql-database)  

[How NoSQL Developed and Why We Don't Need It Anymore](https://www.memsql.com/blog/why-nosql-databases-wrong-tool-for-modern-application/)  

[On Designing and Deploying Internet-Scale Services](https://www.usenix.org/legacy/event/lisa07/tech/full_papers/hamilton/hamilton_html/index.html) -- an old essay from 2007, but still full of excellent tenets to consider when building a scalable application or system.

> Expect failures. A component may crash or be stopped at any time. Dependent components might fail or be stopped at any time. There will be network failures. Disks will run out of space. Handle all failures gracefully.
 
> Keep things simple. Complexity breeds problems. Simple things are easier to get right. Avoid unnecessary dependencies. Installation should be simple. Failures on one server should have no impact on the rest of the data center.
 
> Automate everything. People make mistakes. People need sleep. People forget things. Automated processes are testable, fixable, and therefore ultimately much more reliable. Automate wherever possible.

