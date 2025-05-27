## Essential Notes on Indexes for System Design Interviews

**What is an Index?**

- An index is a data structure that improves the speed of data retrieval operations on a database table at the cost of additional storage space and write overhead.
- Think of it as a "table of contents" for your data: instead of scanning every row, the database can jump directly to the relevant data using the index.

---

**Why Use Indexes?**

- **Faster Data Retrieval:** Indexes dramatically reduce the time needed to locate rows, especially as data volume grows.
- **Avoid Full Table Scans:** Without indexes, queries may require scanning every row, which is slow and resource-intensive.
- **Support for Sorting and Filtering:** Indexes help optimize queries involving `WHERE`, `ORDER BY`, and join operations.

---

**Types of Indexes**

| Index Type            | Description                                                                      | Best Use Case                                      |
| :-------------------- | :------------------------------------------------------------------------------- | :------------------------------------------------- |
| **B-Tree**            | Balanced tree structure; supports range queries and is the default in most RDBMS | General-purpose, range queries                     |
| **Hash**              | Uses hash functions; efficient for exact-match lookups                           | Equality searches                                  |
| **Bitmap**            | Uses bitmaps for each value; efficient for low-cardinality columns               | Data warehousing, columns with few distinct values |
| **Primary**           | Automatically created on primary key; ensures uniqueness                         | Fast lookups by primary key                        |
| **Clustered**         | Determines physical data order; only one per table                               | Range queries, sorting                             |
| **Non-clustered**     | Logical ordering; contains pointers to actual data                               | Secondary lookups                                  |
| **Composite**         | Index on multiple columns                                                        | Multi-column searches                              |
| **Dense/Sparse**      | Dense: entry for every record; Sparse: entry for blocks                          | Varies by data distribution                        |
| **Filtered**          | Indexes a subset of rows based on a condition                                    | Partial indexes, filtered queries                  |
| **Covering**          | Includes all columns needed for a query                                          | Eliminates need to read table data                 |
| **Full-Text/Spatial** | Specialized for text search or geographic data                                   | Text search, spatial queries                       |

---

**How Indexes Work**

- Indexes maintain pointers to the locations of data rows, allowing the database to jump directly to the relevant data.
- Most modern databases use B-Tree or B+ Tree structures, which are self-balancing and optimized for disk storage.
- Indexes are stored separately from the table data and must be kept up-to-date as data changes.

---

**Trade-offs and Costs**

- **Write Overhead:** Every insert, update, or delete operation must also update all relevant indexes, which can slow down write-heavy workloads.
- **Storage Overhead:** Indexes consume additional disk space, sometimes significantly so for large tables or many indexes.
- **Maintenance:** Unused or redundant indexes waste resources and should be periodically reviewed and dropped.

---

**When to Use Indexes**

- On columns frequently used in `WHERE`, `ORDER BY`, or `JOIN` clauses.
- For tables with large numbers of rows, especially in read-heavy applications.
- Avoid excessive indexing on tables with high write rates or on columns rarely queried.

---

**Best Practices**

- Index only the columns that are frequently searched, filtered, or sorted.
- Monitor query performance and index usage to avoid unnecessary indexes.
- Regularly review and maintain indexes as data and query patterns evolve.
- Consider composite indexes for queries filtering on multiple columns.
- Use specialized indexes (e.g., bitmap, full-text) for specific data types and query patterns.

---

**Summary Table: Key Points**

| Aspect        | Key Point                                                                            |
| :------------ | :----------------------------------------------------------------------------------- |
| Purpose       | Speed up data retrieval, reduce full table scans                                     |
| Main Types    | B-Tree, Hash, Bitmap, Clustered, Non-clustered, Composite, Dense/Sparse, Specialized |
| Benefits      | Faster queries, better scalability, efficient sorting/filtering                      |
| Drawbacks     | Slower writes, extra storage, maintenance overhead                                   |
| When to Use   | Read-heavy tables, frequent queries on specific columns                              |
| When to Avoid | Write-heavy tables, rarely queried columns                                           |

---

**Real-World Analogy**

> An index in a database is like the index of a book: instead of reading every page to find a topic, you use the index to jump directly to the right page.

---

**In Interviews, Be Prepared To:**

- Explain how indexes work and why they’re needed.
- Discuss different index types and their ideal use cases.
- Analyze trade-offs between read and write performance.
- Suggest indexing strategies for given query patterns.
- Identify situations where too many or the wrong indexes can hurt performance.
