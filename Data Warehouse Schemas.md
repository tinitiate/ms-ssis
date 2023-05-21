 ![tinitiate.com ssis](/images/tiniaitessis.png)

# Data Warehouse Schemas

## Star Schema

- In a star schema, the data warehouse is structured around a central fact table surrounded by dimension tables.
- The fact table contains the measurements or metrics of the business process being analyzed.
- Dimension tables provide descriptive attributes related to the fact table and represent the different dimensions or perspectives of the data.
- The star schema is simple, easy to understand, and provides fast query performance for aggregations and reporting.
- Data redundancy is high.

## Snowflake Schema

- The snowflake schema is an extension of the star schema where dimension tables are further normalized into multiple related tables.
- The normalization reduces data redundancy but increases the complexity of queries and joins.
- In a snowflake schema, dimension tables are connected through a series of one-to-many relationships.
- The snowflake schema is suitable when the dimension tables have a large number of attributes or when data integrity is critical.
- Data redundancy is low when compared to star schema.

## Fact Constellation (Galaxy) Schema

- A fact constellation schema, also known as a galaxy schema, consists of multiple fact tables sharing dimension tables.
- It is used when there are multiple related business processes or when there are complex relationships between fact tables.
- Fact constellation schema provides more flexibility in representing complex business scenarios and relationships.
- Can result in increased complexity in query design and maintenance.

## Hybrid Schema

- A hybrid schema combines elements of both star and snowflake schemas.
- Some dimension tables are normalized (snowflake) while others are denormalized (star).
- The hybrid schema is used to strike a balance between query performance and data integrity.
- It allows for flexibility in modeling depending on the specific requirements of different dimensions.