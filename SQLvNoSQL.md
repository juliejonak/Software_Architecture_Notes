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



# Additional Reading

[SQL vs NoSQL](https://www.thegeekstuff.com/2014/01/sql-vs-nosql-db)  

[Applications that Work Best with NoSQL](https://www.clariontech.com/blog/applications-that-work-best-with-nosql-database)  

[How NoSQL Developed and Why We Don't Need It Anymore](https://www.memsql.com/blog/why-nosql-databases-wrong-tool-for-modern-application/)  

[On Designing and Deploying Internet-Scale Services](https://www.usenix.org/legacy/event/lisa07/tech/full_papers/hamilton/hamilton_html/index.html) -- an old essay from 2007, but still full of excellent tenets to consider when building a scalable application or system.

> Expect failures. A component may crash or be stopped at any time. Dependent components might fail or be stopped at any time. There will be network failures. Disks will run out of space. Handle all failures gracefully.
 
> Keep things simple. Complexity breeds problems. Simple things are easier to get right. Avoid unnecessary dependencies. Installation should be simple. Failures on one server should have no impact on the rest of the data center.
 
> Automate everything. People make mistakes. People need sleep. People forget things. Automated processes are testable, fixable, and therefore ultimately much more reliable. Automate wherever possible.

