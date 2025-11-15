# Azure DP 900 Exam

## Exam Details

|                     |                 |
| ------------------- | --------------- |
| Exam Duration       | 60 Minutes      |
| Number Of Questions | 40-60           |
| Passing Marks       | 700/1000 Points |

## Data

Data is a collection of facts (numbers, descriptions, observations used in decision making)

## Data Warehouse

- Data warehouses are optimized for read access.

## Data Classification

- Structured Data (Tabular Data, ex. Datawarehouse, ERP,CRM)
- Semi Structured Data (Structured is not fixed, Ex CSV, XML, JSON)
- Unstructured Data (No Structure, ex. Audio, Video, Binary Data Files)

## Structured Data

- In structured data, sometimes called relational data, all data has the same fields or properties.
- All the data has the same organization and shape, or schema.
- The shared schema allows this type of data to be easily searched by using query languages like Structured Query Language (SQL).
- This capability makes this data style perfect for applications like CRM systems, reservations, and inventory management.
- Structured data often is stored in database tables with rows and columns.
- In the table, a key column indicates how one row in a table relates to data in another row of another table.

## Semi Structured Data

- Semi-structured data is less organized than structured data.
- Semi-structured data isn't stored in a relational format because the fields don't fit neatly into tables, rows, and columns.
- Semi-structured data contains tags that make the organization and hierarchy of the data apparent.
- One example is key/value pairs. Semi-structured data is also referred to as non-relational or not only SQL (NoSQL) data.
- JSON documents with varying fields per entity best fit the definition of semi-structured data.

## Data Storage in Cloud

- Azure SQL DB for Structured Data
- Azure Cosmos DB for Semi Structured Data
- Azure Blob Storage for Unstructured Data

## Data Scientist vs. Data Analyst vs. Data Engineer vs DBAs

While these three roles often work together in data-driven organizations, they have distinct responsibilities and skillsets.

- **Data Scientists** ask "What will happen?"
- **Data Analysts** ask "What happened?"
- **Data Engineers** ask "How can we get the data?"
- **DBAs** ask "How can we keep the data safe and accessible?"

- **Data Engineer:** Builds the house (data infrastructure).
- **Data Analyst:** Furnishes the house (cleans and prepares the data).
- **Data Scientist:** Lives in the house (analyzes the data and draws insights).
- **DBA:** Maintains the house (ensures the foundation and structure are sound).

### Data Scientist

- **Focus:** Uncovering insights and making predictions from data.
- **Skills:** Strong statistical and machine learning knowledge, programming (Python, R), data mining, and data visualization.
- **Tasks:** Building predictive models, conducting A/B tests, and developing algorithms.

### Data Analyst

- **Focus:** Interpreting and analyzing data to uncover trends and patterns.
- **Skills:** SQL, data visualization tools (Tableau, Power BI), statistical analysis, and business acumen.
- **Tasks:** Creating reports, dashboards, and visualizations, and answering business questions using data, Responsible for identifying which business rules must be applied to the data of a company.

### Data Engineer

- **Focus:** Building and maintaining the infrastructure and pipelines that support data science and analytics.
- **Skills:** Programming (Python, Java, Scala), database management (SQL, NoSQL), cloud platforms (AWS, GCP, Azure), and data warehousing.
- **Tasks:** Designing data pipelines, ETL processes, and data warehouses, and ensuring data quality and security, data cleansing routines, preparing data. They develop, construct, test & maintain complete architecture.

### Database Administrator (DBA)

- **Focus:** Managing and maintaining databases.
- **Skills:** SQL, database administration tools, performance tuning, and security.
- **Tasks:** Installing, configuring, and maintaining databases, ensuring data integrity, and optimizing database performance.

## Data File Formats

- Delimited Text Files
  - Plain Text Format with specific field delimiters and row terminators
  - Common Formats: CSV (Comma Separated Values), TSV (Tab Separated Values)
  - Advantages:
    - Easy to read and parse
  - Disadvantages:
    - Difficult to parse if data itself has specific field delimiters (ex. commas)
    - Data Type is not forced consistent (ex. number field, email field)
- Extensible Markup Language (XML)
  - Uses tags enclosed in angle brackets (<.../>) to define elements and attributes
- JavaScript Object Notation (JSON)
  - Alternative for XML
- Binary Large Object (BLOB)
  - Stored as binary data (1's or 0's)
  - Ex. Images, Audio, Multimedia Objects

## Optimized File Formats

- CSV, JSON, XML, BLOB
  - Human readable, but not optimized for storage space or processing
- Optimized File Formats
  - Enable Compression, Indexing, and efficient storage and processing
  - Avro, ORC, Parquet

## Avro

- Created by Apache
- Row based format
- Compact, fast, Binary Data Format
- Header describes the structure of data in the record
- Header is stored in JSON
- Application uses the info in header to parse the binary data and extract the fields it contains
- Good format for compressing data and minimizing storage and network bandwidth requirements
- Can't read data without using avro tools

## ORC

- ORC - Optimized Row Columnar Format
- Organizes data into columns rather than rows
- ORC only supports Hadoop HIVE and PIG
- File Structure
  - File Footer Stores Auxiliary info
    - List of stripes in the File
    - Number of rows per stripes
    - Each column's data Type
    - Column-level aggregates count, min, max, and sum
  - Strip Footer contains a directory of stream locations
  - Row data is used in table scans
  - Index data includes min and max values of each column and the row positions within each column

## Parquet

- Columnar Data Format
- Contains row groups
  - Data for each column is stored together in the same row group
- Includes metadata that describes the set of rows found in each chunk
- Specialized in storing and processing nested data types efficiently
- Support very efficient compression and encoding schemes
- Available to any project in Hadoop ecosystem
- Exceptionally good for read intensive jobs

## AVRO vs Parquet vs ORC

| Features                                       | AVRO       | Parquet | ORC        |
| ---------------------------------------------- | ---------- | ------- | ---------- |
| Row/Column                                     | Row        | Column  | Column     |
| Compression                                    | Good       | Great   | Excellent  |
| Read Performance                               | Low        | High    | High       |
| Write Performance                              | High       | Low     | Low        |
| Ability to split files for parallel processing | Yes        | Yes     | Yes (Best) |
| Schema Evolution Support                       | Yes (Best) | Yes     | Yes        |

## How to choose file format

|                     |         |
| ------------------- | ------- |
| Large Files         | Avro    |
| ETL Jobs            | Avro    |
| Ease of maintenance | Parquet |
| Spark               | Parquet |
| Hive                | ORC     |

## OLTP vs OLAP

| OLTP (Online Transaction Processing)                | OLAP (Online Analytical Processing)         |
| --------------------------------------------------- | ------------------------------------------- |
| Many Small Transaction                              | Low Volume but complex queries              |
| Current Data                                        | Historic, Non Volatile Data                 |
| Used to run the business                            | Used to analyze the business                |
| Highly detailed                                     | Consolidated and Summarized                 |
| Typically in the GB Scale                           | TB and Above Scale                          |
| Processing Performance Limit                        | No Limit, Pause/Resume compute              |
| Heavy writes, moderate reads                        | heavy read, low write workloads             |
| A retail point of sale (POS) system, banking system | Data warehouse, business intelligence tools |
| Normalized                                          | Denormalized for Faster Query               |

## ACID vs BASE

| ACID                                                          | BASE                                                                   |
| ------------------------------------------------------------- | ---------------------------------------------------------------------- |
| ACID stands for Atomicity, Consistency, Isolation, Durability | BASE stands for Basically Available, Soft State, Eventually Consistent |
| RDBMS Gold Standard                                           | Used in Many NoSQL Systems                                             |

## ACID Properties

ACID is an acronym that stands for four key properties that guarantee the reliability of database transactions:

- **Atomicity**: Ensures that a transaction is treated as a single, indivisible unit of work. Either all operations within the transaction are completed successfully, or none of them are. This prevents a transaction from leaving the database in an inconsistent state.
- **Consistency**: Guarantees that a database transaction moves the database from one consistent state to another. This means that the transaction must adhere to all database integrity rules.
- **Isolation**: Ensures that concurrent transactions do not interfere with each other. Each transaction operates independently, as if it were the only one executing. This prevents data corruption and anomalies.
- **Durability**: Ensures that once a transaction is committed, its changes are permanent and will survive system failures like power outages or crashes. The changes are written to non-volatile storage, such as a hard disk.

- **Durability** means that committed changes are permanent.
- **Atomicity** means that all transactions either succeed or fail completely.
- **Consistency** guarantees relate to how a given state of the data is observed by simultaneous operations.
- **Isolation** refers to how simultaneous operations potentially conflict with one another.

---

## Schema on Write

In a schema-on-write database, the schema (data structure) of a table or collection is defined upfront, before data is inserted. This means that the structure of the data is fixed and cannot be changed easily after the table or collection is created.

**Examples of Schema-on-Write Databases:**

- **Relational Databases:** SQL Server, MySQL, PostgreSQL
- **NoSQL Databases:** MongoDB (with strict schema)

## Schema on Read

In a schema-on-read database, the schema is determined at runtime, based on the data being inserted. This allows for greater flexibility and adaptability, as the structure of the data can evolve over time.

**Examples of Schema-on-Read Databases:**

- **NoSQL Databases:** MongoDB (with flexible schema), Apache Cassandra, Amazon DynamoDB

## Schema on Write vs. Schema on Read

| Feature           | Schema on Write                            | Schema on Read                                            |
| ----------------- | ------------------------------------------ | --------------------------------------------------------- |
| Schema Definition | Defined upfront                            | Determined at runtime                                     |
| Flexibility       | Less flexible                              | More flexible                                             |
| Performance       | Can be more performant for structured data | Can be less performant for complex queries                |
| Use Cases         | Structured data, OLTP workloads            | Semi-structured and unstructured data, big data analytics |

**Choosing the Right Approach:**

The choice between schema-on-write and schema-on-read depends on your specific use case and data requirements. Consider the following factors:

- **Data Structure:** If your data has a well-defined structure, schema-on-write is a good choice. For less structured or evolving data, schema-on-read offers more flexibility.
- **Query Patterns:** If you know the types of queries you'll be running in advance, schema-on-write can be optimized for those queries. For ad-hoc queries, schema-on-read can be more flexible.
- **Performance Requirements:** Schema-on-write databases can often offer better performance for simple queries, while schema-on-read databases can be more performant for complex analytics queries.

---

## Types of Databases

- Relational (ex. SQL)
- Non-Relational (ex. No-SQL)

## RDBMS

- Relational DB
- SQL based
- Tabular Format
- Is best example of Structured Data
- Each entity object instance represents a row in the database table and stores its data. There is only one instance per row.

## NoSQL Databases

NoSQL database is non-relational, so it scales out better than relational databases as they are designed with web applications in mind.

### Types of NoSQL Databases

- Key-value Pair Based (Ex. DynamoDB, Riak, Tokyo Cabinet, Redis Server, Memcached, Scalaris)
- Column-oriented (Ex. Google BigQuery, Amazon Redshift, Snowflake, BigTable, Cassandra, HBase, Hypertable)
- Graphs based (Ex. Neo4J, InfoGrid, Infinite Graph, Flock DB, OrientDB)
- Document-oriented (Ex. MongoDB, CouchDB, OrientDB, RavenDB)

### Key Value Pair Based

- Data is stored in key/value pairs. It is designed in such a way to handle lots of data and heavy load.
- Key-value pair storage databases store data as a hash table where each key is unique, and the value can be a JSON, BLOB(Binary Large Objects), string, etc.
- Is optimized for simple lookup
- Redis, Dynamo, Riak are some NoSQL examples of key-value store DataBases. They are all based on Amazon’s Dynamo paper.

### Column-based

- Column-oriented databases work on columns and are based on BigTable paper by Google. Every column is treated separately. Values of single column databases are stored contiguously.
- They deliver high performance on aggregation queries like SUM, COUNT, AVG, MIN etc. as the data is readily available in a column.
- Column-based NoSQL databases are widely used to manage data warehouses, business intelligence, CRM, Library card catalogs,
- HBase, Cassandra, Hypertable are NoSQL query examples of column based database.
- ![ColumnarDB vs Row Based DB](https://databasetown.com/wp-content/uploads/2023/10/Columnar-Databases-Use-Cases-Examples.jpg)
- [Video](https://youtu.be/xnoHOvvF1I4)

### Document-Oriented

- Document-Oriented NoSQL DB stores and retrieves data as a key value pair but the value part is stored as a document. The document is stored in JSON or XML formats. The value is understood by the DB and can be queried.
- Whats the difference between KeyValue and Document Oriented DB? one is simple and other has more capability to query the nested data [Reference](https://nosql.mypopescu.com/post/659390374/comparing-document-databases-to-key-value-stores)

### Graph-Based

- A graph type database stores entities as well the relations amongst those entities.
- The entity is stored as a node with the relationship as edges.
- An edge gives a relationship between nodes.
- Every node and edge has a unique identifier.
- Graph Databases natively supports the analysis of relationships between entities

## Time-series database (TSDB)

- A time-series database (TSDB) is a database specifically designed to efficiently store and retrieve time-stamped data. This type of data is characterized by a sequence of values recorded at specific points in time.
- Time-series databases are neither strictly SQL nor NoSQL.
- Time-series databases are not categorized as RDBMS, Key-Value, Columnar, or Graph databases. They represent a distinct category of databases optimized for handling time-stamped data efficiently.
- Ex. InfluxDB, TimescaleDB, Prometheus
- Generally used in IoT (Storing and analyzing sensor data from devices.), Telecom (Monitoring network performance and usage patterns.), Finance (Tracking stock prices, trading volumes, and other financial metrics.), IT operations (Monitoring server metrics, log data, and application performance)

## Types of Data Analytics

- Descriptive Analytics (Business Intelligence and Data Mining)
- Diagnostic Analytics
- Predictive Analytics (Forecasting)
- Prescriptive Analytics
- Cognitive Analytics

| Analytics Types        | Description                                     |
| ---------------------- | ----------------------------------------------- |
| Descriptive Analytics  | What occurred in the past                       |
| Diagnostic Analytics   | Why something happened in the past              |
| Predictive Analytics   | What is most likely to happen in the future     |
| Prescriptive Analytics | Which action you can perform to affect outcomes |
| Cognitive Analytics    | Uses AL/ ML to understand human interactions    |

## Cognitive Analytics

- Transcribing audio files is an example of Cognitive Analytics

## ETL Process

- ETL Stands for Extract, Transform, and Load
- ETL is a data pipeline used to collect data from various sources, transform the data according to business rules and load it into a destination data store.
- ETL Process requires data that is fully processed before being loaded to the target data store.

## ELT Process

- ELT Stands for Extract, Load, and Transform
- The CRM System (Data is Extracted)
- The Data Warehouse (Data is Loaded)
- An in-memory data integration tool (Data is transformed)
- A stand alone data analysis tool (Data is transformed)

## Batch Processing

- Batch processing can output data to a file store.
- Big Data solutions often use long-running batch jobs to filter, aggregate, and otherwise prepare the data for analysis. Usually these jobs involve reading source files from scalable storage (like HDFS, Azure Data Lake Store, and Azure Storage), Processing them, and writing the output to new files in scalable storage.
- In batch processing, latency in delivering data processing results is acceptable.

## Database Normalization

- Normalizing a database reduces data redundancy
- Normalization improves data integrity
- Normalization involves establishing relationships between database tables
- Normalizing a database decreases the throughput of writing transactions. Normalization often involves breaking down data into smaller tables, which can increase the number of write operations required. This can potentially decrease the throughput of writing transactions, especially if there are many joins involved in updating related data.
- Transactional systems are more normalized than Analytics systems. Transactional systems often have a higher degree of normalization to ensure data integrity and consistency. Analytics systems, on the other hand, may prioritize performance and denormalization to optimize query performance.
- Normalizing a database results in queries that require more joins. This is generally true. Normalization involves breaking down data into smaller tables, which can lead to more complex queries that require multiple joins to retrieve the desired information.

## JSON

- It is an example of semi-structured data

```JSON
{
    "customer":{
        "name":"akash",
        "address":{
            "line1":"Rajasthan",
            "line2":"India"
        },
        "socialMedia":[
            {
                "service":"github",
                "handle":"aasisodiya"
            },
            {
                "service":"linkedin",
                "handle":"aasisodiya"
            }
        ]
    }
}
```

- **Root Object** : `customer` is root object
- **Nested Object** : `name`, `address` are nested objects
- **Nested Array** : `socialMedia` is a nested array

## Visualizations

- **Tree Map** are charts of colored rectangles with size representing value. They can be hierarchical, with rectangles nested within the main rectangles.
- **Key Influencer** chart displays the major contributors to a selected result or value
- **Scatter and Bubble Charts** display relationships between 2 (scatter) or 3 (bubble) quantitative measures - whether or not, in which order, etc.

- **Line Chart**
  - Purpose: Shows trends and patterns over time.
  - How it works: Connects data points with lines to reveal trends and fluctuations.
  - Best for: - Tracking website traffic over months   - Monitoring stock prices over years  
    Visualizing sales figures by quarter
- **Matrix**
  - Purpose: Compares and contrasts data across multiple categories.
  - How it works: Organizes data into rows and columns to reveal relationships and patterns.
  - Best for:
    - Comparing sales figures across different regions and product categories
    - Analyzing survey results with multiple questions and answer choices
- **Scatter Plot**
  - Purpose: Shows the relationship between two numerical variables.
  - How it works: Plots data points on a graph with x and y axes to reveal correlations and clusters.
  - Best for:
    - Identifying correlations between variables like height and weight
    - Analyzing the relationship between advertising spend and sales
- **Treemap**
  - Purpose: Displays hierarchical data as nested rectangles.
  - How it works: Sizes of rectangles represent the value of each category, and colors often represent additional dimensions.
  - Best for:
    - Visualizing hierarchical data like file system structures
    - Comparing market share of different product categories

## Star Schema vs Snowflake Schema

| Points             | Snowflake Schema                                                                                     | Star Schema                                                                                 |
| ------------------ | ---------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------- |
| Structure          | Consists of a centralized fact table connected to multiple-dimension tables in a hierarchical manner | Consists of a centralized fact table connected to dimension tables in a star-like structure |
| Normalization      | Highly normalized design                                                                             | Partially denormalized design                                                               |
| Query Performance  | Excellent for complex queries and aggregations                                                       | Better for simple queries and aggregations                                                  |
| Storage Efficiency | Highly efficient for storing data                                                                    | Less efficient due to denormalization                                                       |
| Scalability        | Highly scalable due to the separation of data                                                        | Limited scalability due to denormalization                                                  |
| Data Integrity     | Ensures high data integrity                                                                          | Lower data integrity due to denormalization                                                 |
| Complexity         | More complex to design and maintain                                                                  | Simpler to design and maintain                                                              |
| Flexibility        | More flexible for changes in the data model                                                          | Less flexible for changes in the data model                                                 |
| Usage              | Suitable for large, complex data warehouses                                                          | Suitable for small to medium-sized data warehouses                                          |
| Storage Overhead   | Requires less storage space                                                                          | Requires more storage space                                                                 |

## Fact Table vs Dimension Table

| Fact Table                                                                 | Dimension Table                                                                                      |
| -------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------- |
| Fact table contains quantitative measures (facts) of a business process.   | Dimension table contains descriptive attributes that provide context for the facts.                  |
| In fact table, There is less attributes than dimension table.              | While in dimension table, There is more attributes than fact table.                                  |
| In fact table, There is more records than dimension table.                 | While in dimension table, There is less records than fact table.                                     |
| Fact table forms a vertical table.                                         | While dimension table forms a horizontal table.                                                      |
| The attribute format of fact table is in numerical format and text format. | While the attribute format of dimension table is in text format.                                     |
| It comes after dimension table.                                            | While it comes before fact table.                                                                    |
| The number of fact table is less than dimension table in a schema.         | While the number of dimension is more than fact table in a schema.                                   |
| It is used for analysis purpose and decision making.                       | While the main task of dimension table is to store the information about a business and its process. |

![Fact-vs-Dimension-Table](https://i.sstatic.net/aB9k9.jpg)

## Indexes

- **Clustered Index** is an object associated with a table that sorts and stores the data rows in the table based on their key values.
- A clustered index defines the order in which data is physically stored in a table. Table data can be sorted in only way, therefore, there can be only one clustered index per table. In SQL Server, the primary key constraint automatically creates a clustered index on that particular column

## Clustered vs. Non-Clustered Indexes

In a relational database, indexes are used to optimize query performance by creating a sorted structure of data. There are two main types of indexes: clustered and non-clustered.

### Clustered Index

- **One per Table:** A table can have only one clustered index.
- **Physical Order:** Determines the physical order of the data rows in the table.
- **Best for Frequent Searches:** Ideal for queries that frequently access data based on the indexed column(s).
- **Impact on Updates and Inserts:** Updating or inserting data can be slower than non-clustered indexes, especially for large tables.

### Non-Clustered Index

- **Multiple per Table:** A table can have multiple non-clustered indexes.
- **Logical Order:** Creates a separate structure that points to the actual data rows.
- **Best for Specific Searches:** Useful for queries that frequently filter data based on specific columns.
- **Less Impact on Updates and Inserts:** Generally has a lower impact on performance compared to clustered indexes.

**When to Use Which:**

- **Clustered Index:** Use a clustered index on the column(s) that are most frequently used in `WHERE` clauses, `JOIN` conditions, or `ORDER BY` clauses.
- **Non-Clustered Index:** Use non-clustered indexes on columns that are frequently used in filtering or sorting operations, but not necessarily as the primary access path.

**Key Considerations:**

- **Performance:** The choice of index type can significantly impact query performance.
- **Storage Overhead:** Indexes consume additional disk space.
- **Update and Insert Performance:** Clustered indexes can affect update and insert performance, so use them judiciously.
- **Query Patterns:** Analyze your query patterns to determine which columns should be indexed.

## Stored Procedures

- A stored procedure is a block of code that runs in a database. It can be used to perform a variety of tasks such as:
  - Retrieving data: Stored procedures can be used to query data from one or more tables.
  - Updating data: Stored procedures can be used to insert, update, or delete data in tables.
  - Performing calculations: Stored procedures can be used to perform complex calculations.
  - Controlling transactions: Stored procedures can be used to control transactions, ensuring that data changes are committed or rolled back as needed.
- Stored procedures are often used to encapsulate complex database operations and to improve the performance and security of database applications

## Aggregate Functions

Transact-SQL provides the following aggregate functions:

- APPROX_COUNT_DISTINCT
- AVG
- CHECKSUM_AGG
- COUNT
- COUNT_BIG
- GROUPING
- GROUPING_ID
- MAX
- MIN
- STDEV
- STDEVP
- STRING_AGG
- SUM
- VAR
- VARP

## Databases

- **Relational Database** is appropriate for scenarios that involve a high volume of transactional writes
- **Relational Database** are optimized for writes
- **Relational Database** are optimized for consistency and availability
- **Relational Database** has advantage of simplicity, ease of data retrieval, data integrity, and flexibility.
- **Non Relational Database** doesn't perform ACID transactions.

## DML Data Manipulation Language

Data Manipulation Language (DML) affect the information stored in the database. Use these statements to insert, update, and change the rows in the database.

- INSERT
- SELECT
- DELETE
- UPDATE
- BULK INSERT
- MERGE

## Data Definition Language

Data Definition Language (DDL) statements defines data structures. Use these statements to create, alter, or drop data structures in a database. These statements include:

- ALTER
- Collations
- CREATE
- DROP
- DISABLE TRIGGER
- ENABLE TRIGGER
- RENAME
- UPDATE STATISTICS
- TRUNCATE TABLE

## View

- A view is a virtual table whose contents are defined by a query.
- A view acts as a filter on the underlying tables referenced in the view.
- The query that defines the view can be from one or more tables or from other views in the current or other databases.

## Azure Storage

- Locally Redundant Storage (LRS)
- Zone Redundant Storage (ZRS)
- Read Access Geo Redundant Storage (RA-GRS)
- Geo Redundant Storage (GRS)

Azure Storage offers 2 options for copying your data to a secondary region:

- Geo Redundant Storage (GRS)
- Geo-Zone Redundant Storage (GZRS)

With GRS or GZRS the data in the secondary region isn't available for read or write access unless there is a failover to secondary region. For read access to the secondary region configure your storage account to use read-access geo redundant storage (RA-GRS) or read-access geo redundant storage (RA-GZRS).

- Azure Blob storage is suitable for image files.
- Azure CosmosDB table API is a key-value storage hosted in the cloud.
- One-to-many relationships between business domain objects occur frequently: for example, one department has many employees. There are several ways to implement one-to-many relationships in the Azure Table service.

Azure Resource Group > Azure Storage Account > File Share > Folders > Files

- Copying data from ADLS (Azure Data Lake Storage) from another region will incur cost
- You can use blob,file and table storage in the same Azure Storage Account
- You implement ADLS (Azure Data Lake Storage) by creating Azure Storage Account
- The default access tier for a new general-purpose v2 storage account is set to the hot tier by default.

## Azure Data Factory

- Used for tabular datasets
- **Dataset** : A representation of data structure within datastore. Datasets must be created from paths in Azure datastores or public web URLs, for the data to be accessible by Azure Machine Learning.
- **Linked Service** : The information used to connect to external resources. Linked services are much like connection strings, which define the connection information needed for Data Factory to connect to external resources.
- **Pipeline** : A logical grouping of activities that performs a unit of work and can be scheduled. A pipeline is a logical grouping of activities that together perform a task.

## Data Store Models

- Relational Database Management System (RDBMS)
- Key/Value stores
- Document Databases
- Graph Databases
- Data Analytics
- Column-family databases
- Search Engine Databases
- Time series databases
- Object storage
- Shared files

## Real Time Data Processing

Real time processing deals with streams of data that are captured in real-time and processed with minimal latency to generate real-time (or near-real-time) reports or automated responses.

- Low Latency is expected
- Data is processed as it is created

## Azure SQL DB

- You can use existing Microsoft SQL Server License to reduce the cost of Azure SQL DB
- By default each azure sql db is protected by a server level firewall
- **Managed Backup Service**: Azure SQL Database provides a built-in managed backup service that automatically backs up your databases to ensure data durability and disaster recovery.
- **Built-in High Availability**: Azure SQL Database offers built-in high availability features, such as automatic failover and geo-redundancy, to minimize downtime and ensure data accessibility.
- **Azure Defender**: Azure SQL Database integrates with Azure Defender, a cloud-native security service that provides advanced threat protection and security analytics.
- The Azure SQL Database firewall lets you decide which IP addresses may or may not have access to either your Azure SQL Server or your Azure SQL database.
- SQL Database is a fully managed service that has built-in high availability, backups, and other common maintenance operations.
- Serverless is a compute tier for single databases in Azure SQL Database that automatically scales compute based on workload demand and bills for the amount of compute used per second. The serverless compute tier also automatically pauses databases during inactive periods when only storage is billed and automatically resumes databases when activity returns.
- Scenarios well suited for serverless compute
- Single databases with intermittent, unpredictable usage patterns interspersed with periods of inactivity, and lower average compute utilization over time.
- Single databases in the provisioned compute tier that are frequently rescaled and customers who prefer to delegate compute rescaling to the service.
- New single databases without usage history where compute sizing is difficult or not possible to estimate prior to deployment in SQL Database.

## Azure SQL Database elastic pool

- Azure SQL Database elastic pools are a simple, cost-effective solution for managing and scaling multiple databases that have varying and unpredictable usage demands.
- The databases in an elastic pool are on a single server and share a set number of resources at a set price.
- Elastic pools in SQL Database enable software as a service (SaaS) developers to optimize the price performance for a group of databases within a prescribed budget while delivering performance elasticity for each database.

## Azure SQL Managed Instance

- Azure SQL Managed Instance is the intelligent, scalable cloud database service that combines the broadest SQL Server database engine compatibility with all the benefits of a fully managed and evergreen platform as a service.
- Azure SQL Managed Instance is designed to provide near-perfect compatibility with the latest SQL Server (Enterprise Edition) Database Engine used for on-premises databases. These instances enable you to deploy a native virtual network (VNet) that mimics on-premises deployments and increases security.

## Azure SQL Edge: A Powerful Tool for Edge Computing

- Azure SQL Edge is a distributed database engine designed for IoT and edge computing scenarios.
- It allows you to process and analyze data locally on edge devices, reducing latency and improving the responsiveness of your applications.

### Key features and benefits of Azure SQL Edge

- **Real-time data processing**: Process and analyze data as soon as it's generated, without relying on cloud connectivity.
- **Reduced latency**: By processing data locally, you can significantly reduce latency and improve response times.
- **Offline capabilities**: Azure SQL Edge can operate in disconnected or intermittent connectivity environments.
- **Advanced analytics**: Leverage SQL queries, time-series analysis, and machine learning capabilities to extract valuable insights from your data.
- **Seamless integration with Azure**: Easily integrate with other Azure services, such as Azure IoT Hub and Azure IoT Edge, to create comprehensive IoT solutions.
- **Security**: Benefits from Azure's robust security measures to protect your data.

### Common Use Cases

- **IoT Edge Devices**: Process and analyze sensor data locally to reduce network traffic and improve response times.
- **Remote and Edge Computing**: Perform data processing and analytics in remote locations without relying on cloud connectivity.
- **Real-time Analytics**: Gain real-time insights from streaming data, such as sensor readings or telemetry data.

---

## Azure Cosmos DB

- With Availability Zone (AZ) support, Azure Cosmos DB will ensure replicas are placed across multiple zones within a given region to provide high availability and resiliency to zonal failures.
- Note: Azure Cosmos DB provides high availability in two primary ways. First, Azure Cosmos DB replicates data across regions configured within a Cosmos account. Second, Azure Cosmos DB maintains 4 replicas of data within a region.
- When provisioning an Azure Cosmos DB account, you need to specify which type of API you will use.
- Azure Cosmos DB supports multi-region writes
- The API determines the type of account to create. Azure Cosmos DB provides five APIs: Core (SQL) and MongoDB for document data, Gremlin for graph data, Azure Table, and Cassandra. Currently, you must create a separate account for each API.
- Azure Cosmos DB uses partitioning to scale individual containers in a database to meet the performance needs of your application. In partitioning, the items in a container are divided into distinct subsets called logical partitions.
- Logical partitions are formed based on the value of a partition key that is associated with each item in a container.

## Azure Cosmos DB API

Azure Cosmos DB is a powerful NoSQL database

- **Core SQL API** — As mentioned earlier, this is the default offering for Azure Cosmos DB and satisfies most scenarios. The API stores the data in a document format, it provides the ability to query the data using SQL. It is important to note that the language is not SQL but very SQL like. This is also a good option for users who are trying to migrate from other databases such as Oracle, Dynamo DB, and HBase. This is the primary NoSQL document API, providing flexible schema and querying capabilities with SQL-like syntax.
- **MongoDB API** — This API allows you to use Cosmos DB as if it were a Mongo DB instance and even extends the use of Mongo DB drivers, tools and SDKs. Mongo DB fills the gap between key-value stores and RDBMS systems which allows for more advanced query functionality. Allows you to interact with Cosmos DB using the same MongoDB driver and protocol, making it ideal for migrating existing MongoDB applications.
- **PostgreSQL API** - Allows you to interact with Cosmos DB using the same PostgreSQL driver and protocol
- **Gremlin API** — This allows the users to make graph queries and store data as edges and vertices. This is mainly used in cases where data may not be easily modeled by relational databases. The Gremlin API essentially enables us to utilize the power of graph databases. Used for storing and querying graph data using the Apache TinkerPop framework and Gremlin query language.
- **Cassandra API** — Cassandra is a distributed database from Apache that is designed to manage very large amounts of structured data. It provides high availability with no single point of failure. This API is meant to store data in a columnar structure. Just like the Mongo DB API, Cassandra API also uses a wire protocol to enable access to tools and SDKs specific to Cassandra DB.
- **Table API**: Provides a simple key-value store similar to Azure Table Storage. Supports a multi-master model
- [Reference](https://learn.microsoft.com/en-us/azure/cosmos-db/choose-api)

## Azure CosmosDB Core SQL API

Two settings that can be configured at the container level in an Azure Cosmos DB account using the Core (SQL) API are:

1. **Indexing Policy:**

   - You can define the indexing policy for a container to optimize query performance.
   - This involves specifying which fields to index and the indexing mode (hash or range).

2. **Throughput:**
   - You can set the throughput for a container, which determines the number of Request Units (RUs) allocated to the container.
   - RUs are the unit of capacity in Azure Cosmos DB, and they determine the throughput and storage capacity of a container.

By carefully configuring these settings, you can optimize the performance and cost-effectiveness of your Azure Cosmos DB application.

---

## Azure Blob Storage Tiers

Azure Blob Storage offers different tiers to optimize storage costs based on your data access patterns and performance requirements. Here are the primary tiers:

### Hot Access Tier

- **Best for:** Frequently accessed data.
- **Performance:** High performance for read and write operations.
- **Cost:** Higher storage costs compared to other tiers.

### Cool Access Tier

- **Best for:** Infrequently accessed data that you may need to access in the future.
- **Performance:** Lower performance compared to Hot Access, but still suitable for most workloads.
- **Cost:** Lower storage costs than Hot Access.

### Archive Access Tier

- **Best for:** Data that is rarely accessed, such as long-term backups or historical records.
- **Performance:** Lowest performance tier, but suitable for long-term storage.
- **Cost:** Lowest storage costs of all tiers.

### Choosing the Right Tier

To select the appropriate tier for your data, consider the following factors:

- **Access Frequency:** How often do you need to access the data?
- **Performance Requirements:** What level of performance is required for read and write operations?
- **Data Retention:** How long do you need to retain the data?
- **Cost Considerations:** What is your budget for storage costs?

By carefully selecting the right tier for your data, you can optimize storage costs and ensure that your data is accessible when needed.

---

## POSIX-compliant Access Control Lists (ACLs) vs. Role-Based Access Control (RBAC)

Both ACLs and RBAC are mechanisms used to control access to resources, but they differ in their approach and granularity.

### POSIX-compliant Access Control Lists (ACLs)

- **Granular Control:** ACLs provide fine-grained control over access to individual files and directories.
- **User and Group Permissions:** Permissions can be assigned to specific users and groups.
- **Complex Configuration:** ACLs can become complex to manage, especially in large-scale environments.

### Role-Based Access Control (RBAC)

- **Role-Based Permissions:** Users are assigned roles, and roles are associated with specific permissions.
- **Simplified Management:** RBAC simplifies access control by reducing the number of permissions to manage.
- **Scalability:** RBAC is more scalable for large organizations with many users and resources.

### Key Differences

| Feature     | ACLs                        | RBAC                  |
| ----------- | --------------------------- | --------------------- |
| Granularity | Fine-grained                | Coarse-grained        |
| Focus       | Individual users and groups | Roles and permissions |
| Complexity  | More complex                | Simpler to manage     |
| Scalability | Less scalable               | More scalable         |

### Choosing the Right Approach

The choice between ACLs and RBAC depends on your specific security requirements and organizational structure.

- **ACLs** are well-suited for scenarios where you need precise control over individual files and directories, such as in file systems.
- **RBAC** is often used in large-scale environments where managing individual permissions for many users would be impractical.

By understanding the differences between ACLs and RBAC, you can choose the appropriate access control mechanism to protect your resources.

---

## Azure Data Lake Storage Gen2 (ADLS Gen2)

- Azure Data Lake Storage Gen2 (ADLS Gen2) provides native support for **POSIX-compliant access control lists (ACLs)**. This allows for granular control over file and directory access, making it suitable for environments that require fine-grained security and compatibility with existing POSIX-based tools and workflows.
- Azure Data Lake Storage Gen2 supports **role-based access control (RBAC)** at the file and folder level. This allows you to grant specific permissions to different users and groups, ensuring fine-grained control over access to your data.
- With RBAC, you can define roles like "Reader," "Contributor," and "Owner," each with specific permissions. This helps you maintain data security and privacy by limiting access to authorized individuals.

## Azure Blob Storage vs ADLS Gen2

| Feature     | Azure Blob Storage                                                              | Azure Data Lake Storage Gen2                                                                                                |
| ----------- | ------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------- |
| Namespace   | Flat                                                                            | Hierarchical                                                                                                                |
| Performance | Good for general-purpose storage and retrieval                                  | Optimized for high-throughput, low-latency access to large datasets                                                         |
| Security    | Supports standard security features like encryption and access control          | Offers advanced security features like POSIX ACLs and role-based access control                                             |
| Cost        | Generally more cost-effective for smaller datasets and simple storage scenarios | Can be more cost-effective for large-scale data analytics workloads due to its optimized performance and storage efficiency |

## Azure Table storage

- Azure Table storage is a powerful and versatile NoSQL data store that offers a flexible, scalable, and cost-effective solution for storing large amounts of structured data.
- It's well-suited for a wide range of applications, making it a valuable tool in the Azure ecosystem.
- Doesn't supports a multi-master model
- To store data by using Azure Table storage, First create an Azure storage account, then use Table service in the Azure portal to create a table.
- Note: An Azure storage account contains all of your Azure Storage data objects: blobs, files, queues, and tables.
- [Choose Azure Cosmos DB for Table or Azure Table Storage](https://learn.microsoft.com/en-us/azure/cosmos-db/table-support?toc=https%3A%2F%2Flearn.microsoft.com%2Fen-us%2Fazure%2Fstorage%2Ftables%2Ftoc.json&bc=https%3A%2F%2Flearn.microsoft.com%2Fen-us%2Fazure%2Fbread%2Ftoc.json)

## Azure Queue storage

- Azure Queue storage is a service for storing large numbers of messages that can be accessed from anywhere in the world via HTTP or HTTPS. It's a reliable and scalable solution for storing and processing messages asynchronously.
- Azure Queue storage is a powerful and versatile service that can be used to build reliable, scalable, and efficient applications.
- It's a great choice for a variety of use cases, including asynchronous processing, message passing, task queuing, and real-time processing.

## Azure Files

- Azure Files is a fully managed file share service provided by Microsoft Azure.
- It allows you to store and share files in the cloud, accessible via industry-standard protocols like SMB (Server Message Block) and NFS.
- By using Azure Files, you can simplify your file storage and sharing needs, improve performance, and enhance security for your applications and data.
- Microsoft Azure offers two service tiers for its storage services: Standard Storage and Premium Storage. The Premium tier stores data on modern solid state drives (SSDs), while the Standard tier uses hard disk drives (HDDs).

### Key Differences between Azure Files and ADLS Gen 2

| Feature         | Azure Files                                     | ADLS Gen2                                                           |
| --------------- | ----------------------------------------------- | ------------------------------------------------------------------- |
| Access Protocol | SMB, NFS                                        | HTTP/HTTPS                                                          |
| File System     | Hierarchical file system                        | Hierarchical namespace (similar to a file system)                   |
| Performance     | Optimized for general-purpose file operations   | Optimized for high-throughput, low-latency access to large datasets |
| Security        | Supports standard file permissions and ACLs     | Supports POSIX ACLs for granular access control                     |
| Use Cases       | File shares, home directories, application data | Data lakes, data warehouses, big data analytics                     |

## Azure Data Studio

- A lightweight editor that can run on-demand SQL queries and view and save results as text, JSON, or Microsoft Excel files. Edit data, organize your favorite database connections, and browse database objects in a familiar object browsing experience.
- Azure Data Studio is a powerful, cross-platform tool designed to manage and query various data sources, including Azure SQL Database, Azure SQL Managed Instance, and on-premises SQL Server.
- Rich Notebook Experience: Create interactive notebooks to combine code, text, and visualizations.
- Document Formatting: Support for markdown, code blocks, and rich text.
- Can be used to restore databases

### Benefits of Azure Data Studio

- **Improved Productivity**: Streamline your data management and analysis tasks.
- **Enhanced Collaboration**: Share and collaborate on notebooks with your team.
- **Deeper Insights**: Gain valuable insights from your data through visualizations and analysis.
- **Simplified Management**: Manage your data sources efficiently.

## Microsoft SQL Server Data Tools (SSDT)

- A modern development tool for building SQL Server relational databases, Azure SQL databases, Analysis Services (AS) data models, Integration Services (IS) packages, and Reporting Services (RS) reports. With SQL Server Data tools (SSDT), you can design and deploy any SQL Server content type with the same ease as you would develop an application in Visual Studio.
- A development tool for building Azure SQL databases, Microsoft SQL Server relational databases, SQL Server Analysis Services (SSAS) data models, SQL Server Integration Services (SSIS) packages, and SQL Server Reporting Services (SSRS) reports.
- SQL Server Data Tools (SSDT) is a modern development tool for building SQL Server relational databases, databases in Azure SQL, Analysis Services (AS) data models, Integration Services (IS) packages, and Reporting Services (RS) reports.
- With SSDT, you can design and deploy any SQL Server content type with the same ease as you would develop an application in Visual Studio.

## Microsoft SQL Server Management Studio (SSMS)

- Manage a SQL Server instance or database with full GUI support. Access, configure, manage, administer, and develop all components of SQL Server, Azure SQL Database, and Azure Synapse Analytics. Provides a single comprehensive utility that combines a broad group of graphical tools with many rich script editors to provide access to SQL for developers and database administrators of all skill levels.
- A graphical tool for managing SQL Server or Azure SQL databases that supports access, configuration, management, and administration tasks.
- SQL Server Management Studio (SSMS) is an integrated environment for managing any SQL infrastructure, from SQL Server to Azure SQL Database.

## SSDT vs SSMS

- SSMS is a versatile tool for a wide range of database tasks, but it lacks the advanced features for complex database development offered by SSDT.
- SSDT is specifically designed for database development and provides a more structured and efficient approach to building and managing databases.

When to Use Which:

- SSMS: For quick queries, ad-hoc tasks, and general database administration.
- SSDT: For complex database development, version control, and automated deployment.

## Azure Resource Manager template

- Used to automate the creation of an interdependent group of Azure resources in a repeatable way
- You can automate deployments and use the practice of infrastructure as code.
- In code, you define the infrastructure that needs to be deployed
- To implement infrastructure as code for your Azure solutions, use Azure Resource Manager templates (ARM templates).
- The template is a JavaScript Object Notation (JSON) file that defines the infrastructure and configuration for your project.
- The template uses declarative syntax, which lets you state what you intend to deploy without having to write the sequence of programming commands to create it.
- In the template, you specify the resources to deploy and the properties for those resources.

Command-line tools
The following tools are the main command-line tools.

| Tool                  | Description                                                                                                                                  |
| --------------------- | -------------------------------------------------------------------------------------------------------------------------------------------- |
| bcp                   | The bulk copy program utility (bcp) bulk copies data between an instance of Microsoft SQL Server and a data file in a user-specified format. |
| mssql-conf            | mssql-conf configures SQL Server running on Linux. Linux                                                                                     |
| sqlcmd                | The sqlcmd utility lets you enter Transact-SQL statements, system procedures, and script files at the command prompt.                        |
| sqlpackage            | sqlpackage is a command-line utility that automates several database development tasks.                                                      |
| SQL Server PowerShell | SQL Server PowerShell provides cmdlets for working with SQL.                                                                                 |

## Azure HDInsight

**Azure HDInsight** is a managed, open-source, cloud-based analytics service that supports big data frameworks such as **Apache Hadoop, Spark, Hive, Kafka, Storm**, and others. It allows you to process massive amounts of data efficiently for various use cases.

### Key Features

1. **Big Data Processing**: Allows batch processing, interactive queries, streaming analytics, and real-time analytics.
2. **Integration**: Supports integration with Azure Data Lake, Azure Storage, and Power BI for visualizations.
3. **Scalability**: Easily scales resources to handle large workloads.
4. **Cost-Effective**: Pay-as-you-go pricing for processing big data.
5. **Use Cases**:
   - Log analysis
   - IoT (Internet of Things) solutions
   - Machine learning at scale
   - Real-time stream processing

---

## Azure Synapse Analytics

**Azure Synapse Analytics** is a cloud-based analytics service that brings together big data and data warehousing into a single platform. It enables advanced analytics with the integration of structured and unstructured data.

### Key Features of Azure Synapse Analytics

1. **Massively Parallel Processing (MPP) Engine**: Distributes processing across compute nodes.
2. **Data Warehousing**: A massively parallel processing (MPP) architecture supports petabyte-scale data warehousing.
3. **Serverless and Dedicated Options**: Offers serverless SQL pools for on-demand queries and dedicated SQL pools for predictable workloads.
4. **Data Integration**: Seamless integration with Azure Data Lake, Power BI, Azure Machine Learning, and other Azure services.
5. **Unified Analytics**: Combines data integration, data exploration, and data visualization into a single platform.
6. **Use Cases**:
   - Enterprise data warehouses
   - Real-time analytics and reporting
   - Data lakehouse implementation
   - Business intelligence and data modeling

---

## PolyBase

PolyBase is an Azure Synapse Analytics feature that allows you to query data stored in external data sources, including Azure Blob Storage, using T-SQL queries. This enables you to analyze data from various sources in a unified way, without needing to move or transform the data.

## A hierarchical namespace

This is a general term for a file system-like structure used to organize data. It's not specific to Azure Synapse Analytics or data retrieval from Azure Blob Storage.

## Azure Synapse Link

This feature allows you to integrate real-time data from operational databases like Azure SQL Database into Azure Synapse Analytics. It's not specifically designed for querying data from Azure Blob Storage.

## The Data Movement Service (DMS)

This service is used for bulk data movement between on-premises and cloud data stores. It's not directly related to querying data from Azure Blob Storage using T-SQL.

---

## Key Differences Between Azure HDInsight and Azure Synapse Analytics

Both services are highly capable, but they target different analytics scenarios. Let me know if you’d like to dive deeper into either of them!

| Feature         | **Azure HDInsight**                              | **Azure Synapse Analytics**                             |
| --------------- | ------------------------------------------------ | ------------------------------------------------------- |
| **Purpose**     | Big data processing using open-source frameworks | Unified analytics for big data and data warehousing     |
| **Use Case**    | IoT, log processing, real-time analytics         | Data warehousing, business intelligence                 |
| **Technology**  | Hadoop, Spark, Hive, Kafka, etc.                 | SQL-based analytics, integrated tools                   |
| **Scalability** | Scales with cluster size                         | Scales with SQL pools and integrated services           |
| **Ease of Use** | Requires familiarity with open-source tools      | Simplified with integrated tools and serverless options |

---

## Azure Synapse Data Explorer

Azure Synapse Data Explorer is a powerful, fully managed data analytics service built for real-time analysis over large volumes of data. It's ideal for analyzing log, telemetry, and time-series data.

### Key Features

- **High-Performance Query Engine:** Enables rapid analysis of petabytes of data.
- **Time-Series Analytics:** Optimized for time-series data, allowing for efficient trend analysis.
- **Data Ingestion:** Supports high-speed ingestion from various sources like IoT devices, applications, and logs.
- **Rich Visualization:** Offers built-in visualizations to explore and understand data.
- **Security and Compliance:** Provides robust security features, including encryption and access controls.
- **Integration with Azure Ecosystem:** Seamlessly integrates with other Azure services.

### Common Use Cases

- **Log Analytics:** Analyzing logs from applications and infrastructure.
- **IoT Analytics:** Processing and analyzing IoT device data.
- **Application Performance Monitoring (APM):** Monitoring app performance and identifying bottlenecks.
- **Security Analytics:** Detecting security threats and anomalies.
- **Customer Analytics:** Analyzing customer behavior and preferences.

---

## KQL (Kusto Query Language)

KQL is a powerful query language used to interact with data stored in Azure Data Explorer. It allows you to efficiently query and analyze large volumes of structured, semi-structured, and unstructured data.

### Key Features of KQL

- **Time-Series Analysis:** KQL is particularly well-suited for analyzing time-series data, allowing you to visualize trends, patterns, and anomalies over time.
- **Flexible Querying:** It provides a flexible query language that enables you to filter, aggregate, and transform data in various ways.
- **Rich Function Library:** KQL offers a wide range of built-in functions for data manipulation, statistical analysis, and visualization.
- **Seamless Integration with Azure Data Explorer:** KQL is tightly integrated with Azure Data Explorer, allowing you to query and analyze data stored in this service.

### Example KQL Query

```kql
// Query to find the top 10 users by page views in the last 7 days
StormEvents
| where TimeGenerated > ago(7d)
| summarize Count = count() by User
| sort by Count desc
| take 10
```

---

## TDE (Transparent Data Encryption)

- TDE encrypts the data at rest within the database files. This means that the data is encrypted while it's stored on disk, protecting it from unauthorized access even if the physical storage device is compromised.
- TDE works by encrypting the entire database, including data files, log files, and backups.
- It uses a combination of encryption keys to protect the data, and the encryption process is transparent to the application

## Azure Active Directory (Azure AD)

- Azure Active Directory (Azure AD) is Microsoft's cloud-based identity and access management (IAM) service.
- It provides a central platform to manage user identities, groups, and permissions across various Microsoft cloud services like Azure, Microsoft 365, and other third-party applications
- Use this to ensure that users use multi-factor authentication (MFA) when connecting to an Azure SQL database

## Azure Networking Services: A Comparative Overview

Azure offers a variety of networking services to help you build secure, scalable, and high-performance applications. Here's a comparison of Azure Private Link, Azure DNS, Azure Traffic Manager, and Azure Application Gateway:

### Azure Private Link

- **Purpose:** Privately connect your virtual networks to other Azure services or on-premises resources.
- **How it works:** Creates private endpoints that allow you to access services like Azure Storage, Azure SQL Database, and Azure Cosmos DB without exposing them to the public internet.
- **Benefits:** Enhanced security, reduced latency, and improved reliability.

### Azure DNS

- **Purpose:** Host DNS domains and manage DNS records.
- **How it works:** Provides a global DNS service that is highly available and scalable.
- **Benefits:** Simplified DNS management, improved performance, and enhanced security.

### Azure Traffic Manager

- **Purpose:** Distributes traffic across multiple endpoints.
- **How it works:** Directs traffic to the most appropriate endpoint based on various factors, such as performance, geographic location, and health.
- **Benefits:** Improved performance, high availability, and geographic load balancing.

### Azure Application Gateway

- **Purpose:** Load balances incoming traffic across multiple backend servers.
- **How it works:** Distributes traffic based on various load-balancing algorithms and provides additional features like SSL termination, web application firewall (WAF), and URL rewriting.
- **Benefits:** Enhanced security, improved performance, and advanced traffic management capabilities.

**Choosing the Right Service:**

- **Azure Private Link:** Use when you need to connect to Azure services or on-premises resources securely and privately.
- **Azure DNS:** Use to host your DNS domains and manage DNS records.
- **Azure Traffic Manager:** Use to distribute traffic across multiple endpoints based on various criteria.
- **Azure Application Gateway:** Use to load balance incoming traffic, provide SSL termination, and apply web application firewall protection.

---

## Azure Databricks

- Azure Databricks can consume data from Azure SQL Database, Azure Event Hubs, and Azure Cosmos DB.

## Reference

- [Dump](https://www.itexams.com/exam/DP-900?)
- [Dump](https://www.certlibrary.com/exam/DP-900)
- [Dump](https://www.examtopics.com/exams/microsoft/dp-900/)
- [Dump](https://free-braindumps.com/microsoft/free-dp-900-braindumps.html?p=2)
- [Dump](https://free-braindumps.com/amazon/free-saa-c02-braindumps.html?p=2)
- [OLTP](https://learn.microsoft.com/en-us/azure/architecture/data-guide/relational-data/online-transaction-processing)
- [Columnar Database](https://databasetown.com/columnar-databases/)
- [DP-900: Microsoft Azure Data Fundamentals Course - Feb 2024](https://www.udemy.com/course/azure-dp-900/)
- [Azure Cosmos DB API Services](https://medium.com/codex/azure-cosmos-db-api-services-dc14a4cafd2c)
- [NoSQL Tutorial: What is, Types of NoSQL Databases & Example](https://www.guru99.com/nosql-tutorial.html)
- [Youtube Dumps](https://www.youtube.com/watch?v=wi3PkLK_gNc)
- [Dumps](https://www.itexams.com/exam/DP-900?)
- [Dumps](https://www.dumpsbase.com/freedumps/updated-microsoft-azure-data-fundamentals-dp-900-dumps-for-good-preparation.html)
- [Data Store](https://learn.microsoft.com/en-us/azure/architecture/guide/technology-choices/data-store-overview)
- [CMD Tools](https://learn.microsoft.com/en-us/sql/tools/overview-sql-tools?view=sql-server-ver15)
