# Data Storage

# OLTP (Online Transaction Processing)

- OLTP refers to the processing of real-time transactions and day-to-day operations in a database system.
- It focuses on rapid transaction processing, ensuring data integrity, and supporting high volumes of concurrent transactions.
- OLTP systems are optimized for efficient inserts, updates, and deletes of individual records.
- OLTP databases are commonly used in transactional systems such as e-commerce, banking, order processing, and inventory management.

## ODS (Operational Data Store)

- An Operational Data Store is a database that integrates data from multiple operational systems in near real-time.
- Its purpose is to provide a central repository of current and integrated data for operational reporting and analysis.
- ODS acts as a staging area between operational systems and data warehouses or data marts.
- It captures and transforms data from various sources, performs minimal data validation, and consolidates it for operational reporting and querying.

## OLAP (Online Analytical Processing)

- OLAP is a technology used for organizing, analyzing, and reporting on large volumes of data in a multidimensional format.
- It is designed to support complex analytical queries and provide insights into business performance, trends, and patterns.
- OLAP databases are optimized for fast query response times and provide capabilities like drill-down, roll-up, slicing, and dicing for data analysis.
- OLAP is commonly used in data warehousing and business intelligence applications for decision-making and strategic planning.

## Differences between OLAP, OLTP, and ODS

| OLTP                                                         | OLAP                                                         |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| OLTP is an online transactional system.                      | OLAP is an online analysis and data retrieving process.      |
| It is characterized by large numbers of short online transactions. | It is characterized by a large volume of data.               |
| OLTP is an online database modifying system.                 | OLAP is an online database query management system.          |
| OLTP uses traditional DBMS.                                  | OLAP uses the data warehouse.                                |
| Insert, Update, and Delete information from the database.    | Mostly select operations                                     |
| OLTP and its transactions are the sources of data.           | Different OLTP databases become the source of data for OLAP. |
| OLTP database must maintain data integrity constraints.      | OLAP database does not get frequently modified. Hence, data integrity is not an issue. |
| It’s response time is in a millisecond.                      | Response time in seconds to minutes.                         |
| The data in the OLTP database is always detailed and organized. | The data in the OLAP process might not be organized.         |
| Allow read/write operations.                                 | Only read and rarely write.                                  |
| It is a market-orientated process.                           | It is a customer orientated process.                         |
| Queries in this process are standardized and simple.         | Complex queries involving aggregations.                      |
| Complete backup of the data combined with incremental backups. | OLAP only need a backup from time to time. Backup is not important compared to OLTP |
| DB design is an application-oriented example: Database design changes with the industry like retail, airline, banking, etc. | DB design is subject-oriented. Example: Database design changes with subjects like sales, marketing, purchasing, etc. |
| It is used by Data critical users like clerk, DBA & Data Base professionals. | It is used by Data knowledge users like workers, managers, and CEO. |
| It is designed for real time business operations.            | It is designed for analysis of business measures by category and attributes. |
| Transaction throughput is the performance metric             | Query throughput is the performance metric.                  |
| This kind of Database user allows thousands of users.        | This kind of Database allows only hundreds of users.         |
| It helps to Increase user’s self-service and productivity    | Help to Increase the productivity of business analysts.      |
| Data Warehouses historically have been a development project which may prove costly to build. | An OLAP cube is not an open SQL server data warehouse. Therefore, technical knowledge and experience are essential to managing the OLAP server. |
| It provides a fast result for daily used data.               | It ensures that response to the query is quicker consistently. |
| It is easy to create and maintain.                           | It lets the user create a view with the help of a spreadsheet. |
| OLTP is designed to have fast response time, low data redundancy, and is normalized. | A data warehouse is created uniquely so that it can integrate different data sources for building a consolidated database |

| Criteria         | OLTP                               | ODS                                               | OLAP                                  |
| ---------------- | ---------------------------------- | ------------------------------------------------- | ------------------------------------- |
| Purpose          | Transactional processing           | Operational reporting and integration             | Analytical processing                 |
| Data Type        | Current and detailed data          | Integrated and cleansed data                      | Historical and aggregated data        |
| Use Case         | Day-to-day business operations     | Reporting and data synchronization                | Decision support and analysis         |
| Performance      | Fast response time, simple queries | Moderate response time, moderate complexity       | Complex queries, longer response time |
| Database Design  | Normalized schema                  | Hybrid, combining aspects of both                 | Star or snowflake schema              |
| Data Volume      | Smaller data sets                  | Moderate data sets                                | Large data sets                       |
| Data Updates     | Frequent read and write operations | Read and write operations with moderate frequency | Read-intensive, infrequent updates    |
| Query Complexity | Simple queries and transactions    | Moderate complexity queries                       | Complex queries and aggregations      |