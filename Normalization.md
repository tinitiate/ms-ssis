 ![tinitiate.com ssis](/images/tiniaitessis.png)
# Normalization

- Normalization is the process of designing a database schema to minimize redundancy and improve data integrity.
- It involves decomposing a database into multiple related tables, ensuring each table has a well-defined purpose and follows specific normalization rules.
- The goal of normalization is to eliminate data anomalies, such as insertion, deletion, and update anomalies, and ensure data consistency.
- Normalization follows a set of normal forms (e.g., First Normal Form, Second Normal Form, etc.) that define specific requirements for table structure and relationships.
- By adhering to normalization principles, data is stored efficiently with minimal redundancy, making it easier to maintain, update, and query.

## Normal Forms

### First Normal Form (1NF)

- 1NF requires that each column in a table contains only atomic (indivisible) values.
- It eliminates repeating groups and ensures that each column holds a single value for each row.
- Each table must have a primary key that uniquely identifies each row.

### Second Normal Form (2NF)

- 2NF builds upon 1NF and requires that every non-key column is functionally dependent on the entire primary key.
- It eliminates partial dependencies, where non-key columns depend on only part of the primary key.
- If a table has composite (multi-column) primary key, each non-key column should depend on the entire composite key, not just a subset of it.

### Third Normal Form (3NF)

- 3NF builds upon 2NF and requires that every non-key column is dependent only on the primary key and not on other non-key columns.
- It eliminates transitive dependencies, where a non-key column depends on another non-key column through the primary key.
- To achieve 3NF, non-key columns that are functionally dependent on other non-key columns should be moved to separate tables.

### Boyce-Codd Normal Form (BCNF)

- BCNF is an advanced normal form that deals with more complex dependencies.
- It extends 3NF by requiring that every determinant (a column or set of columns that determines other columns' values) is a candidate key.
- BCNF ensures that there are no non-trivial dependencies where a non-key column determines another non-key column.

## Denormalization

- Denormalization is the process of deliberately introducing redundancy into a normalized database schema.
- It involves combining tables or duplicating data to optimize query performance, improve data retrieval speed, and simplify complex queries.
- Denormalization is typically done in data warehouses or analytical systems, where query performance is crucial, and data integrity is of secondary importance.
- By denormalizing data, redundant information is stored in additional tables, reducing the need for complex joins and increasing query performance.
- However, denormalization can lead to increased storage space and increased complexity for data maintenance, as redundant data must be carefully managed to ensure consistency.
