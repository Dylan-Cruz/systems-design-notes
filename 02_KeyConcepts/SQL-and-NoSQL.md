# Essential Notes on SQL and NoSQL for System Design Interviews

When preparing notes about SQL and NoSQL for systems design interviews, focus on their core differences, strengths, and the scenarios where each excels. Here’s what’s essential to know:

## Core Concepts

**SQL Databases (Relational)**

- Use structured, table-based data models with predefined schemas (tables, rows, columns).
- Data relationships are enforced using keys (primary, foreign).
- Query language: SQL (Structured Query Language), which is declarative and standardized.
- Examples: MySQL, PostgreSQL, Oracle, Microsoft SQL Server.

**NoSQL Databases (Non-Relational)**

- Use flexible, dynamic schemas suitable for structured, semi-structured, or unstructured data.
- Store data in various formats: document (JSON, BSON), key-value pairs, wide-column, or graph structures.
- No standardized query language; each database may have its own approach.
- Examples: MongoDB (document), Cassandra (wide-column), Redis (key-value), Neo4j (graph).

## Key Differences

| Feature        | SQL Databases                      | NoSQL Databases                        |
| :------------- | :--------------------------------- | :------------------------------------- |
| Data Model     | Relational (tables, rows, columns) | Non-relational (docs, key-value, etc.) |
| Schema         | Fixed, predefined                  | Flexible, dynamic                      |
| Query Language | SQL (standardized)                 | Varies (JSON, custom APIs, etc.)       |
| Scalability    | Vertical (scale up server)         | Horizontal (add more servers)          |
| Consistency    | Strong (ACID)                      | Eventual (BASE), some offer tunable    |
| Transactions   | Strong, multi-row                  | Limited, varies by type                |
| Use Cases      | Structured data, complex queries   | Big data, unstructured, fast scaling   |

## Strengths and Weaknesses

**SQL Strengths**

- Strong consistency and data integrity (ACID properties).
- Mature technology, broad community support, and robust tooling.
- Ideal for applications with complex queries and relationships (e.g., banking, ERP).

**SQL Weaknesses**

- Rigid schema makes adapting to changing data requirements harder.
- Vertical scaling can be expensive and limiting for very large datasets.

**NoSQL Strengths**

- Flexible, schema-less design for evolving or unpredictable data.
- Horizontal scaling supports large, distributed, high-traffic systems.
- Handles diverse data types (documents, graphs, etc.) and massive volumes.

**NoSQL Weaknesses**

- Weaker consistency guarantees (eventual consistency is common).
- Less mature, with less standardized tooling and community support.
- Limited support for complex queries and multi-record transactions.

## When to Use Each

**Choose SQL when:**

- Data is highly structured and relationships are important.
- Strong consistency and integrity are required.
- Complex queries, joins, and transactions are needed.

**Choose NoSQL when:**

- Data is unstructured, semi-structured, or rapidly evolving.
- Application demands high scalability and availability (e.g., IoT, real-time analytics, social networks).
- Flexibility and speed of development are priorities over strict consistency.

## Types of NoSQL Databases

- **Document Stores**: Store data as documents (e.g., MongoDB).
- **Key-Value Stores**: Simple key-value pairs (e.g., Redis).
- **Wide-Column Stores**: Data stored in columns, efficient for sparse data (e.g., Cassandra).
- **Graph Databases**: Nodes and edges for highly connected data (e.g., Neo4j).

## Summary Table

| SQL (Relational)         | NoSQL (Non-Relational)          |
| :----------------------- | :------------------------------ |
| Structured, tabular data | Flexible, varied data formats   |
| Predefined schema        | Dynamic schema                  |
| ACID transactions        | BASE/eventual consistency       |
| Vertical scaling         | Horizontal scaling              |
| Mature, strong community | Rapidly evolving, less mature   |
| Best for complex queries | Best for big data, fast scaling |

## Interview Insights

- Be ready to discuss trade-offs: consistency vs. scalability, flexibility vs. integrity.
- Know real-world use cases for each (e.g., banking for SQL, social media for NoSQL).
- Understand that modern SQL databases can sometimes handle unstructured data, and some NoSQL systems offer tunable consistency.

This foundational understanding will help you articulate the right choice for a given system design scenario and explain the reasoning clearly in interviews.
