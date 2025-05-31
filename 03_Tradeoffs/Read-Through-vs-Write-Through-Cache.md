## Read-Through vs. Write-Through Cache: System Design Interview Notes

Caching strategies are fundamental in system design interviews, especially when discussing performance optimization and data consistency. Read-through and write-through caches are two essential patterns every candidate should understand.

---

### **Read-Through Cache**

**Definition:**
A read-through cache acts as a proxy between the application and the primary data store. When the application requests data:

- The cache checks if the data is present (cache hit).
- If not (cache miss), the cache itself fetches the data from the database, stores it, and returns it to the application.
- Subsequent requests for the same data are served directly from the cache.

**How It Works:**

- Application always queries the cache.
- On cache miss, the cache loads data from the database and stores it for future use.

**Pros:**

- Simplifies application logic—cache handles population and misses automatically.
- Reduces load on the primary database for frequently accessed data.
- Improves read performance after initial cache fill.

**Cons:**

- First read (cache miss) incurs latency as data is fetched from the database.
- Cache may become stale if data changes in the database outside the cache’s awareness unless paired with appropriate invalidation strategies.

**Use Cases:**

- Read-heavy systems where data is frequently read but not updated often (e.g., product catalogs, news sites).

---

### **Write-Through Cache**

**Definition:**
In a write-through cache, every write (update or insert) operation is performed on both the cache and the primary data store simultaneously:

- When data is written, it is updated in the cache and the database at the same time.
- This ensures the cache is always consistent with the database.

**How It Works:**

- Application writes data to the cache.
- The cache writes the data to the database (or both are written in parallel).
- The cache is immediately updated, so subsequent reads always reflect the latest state.

**Pros:**

- Ensures strong consistency between cache and database.
- No risk of stale data in the cache.
- Simplifies cache invalidation—no need for explicit cache clearing after writes.

**Cons:**

- Slower write performance, as each write must update both cache and database before acknowledging success.
- Increased write latency can be a bottleneck in write-heavy systems.

**Use Cases:**

- Systems where data consistency is critical, such as financial applications, inventory management, or order processing.

---

### **Comparison Table**

| Feature | Read-Through Cache | Write-Through Cache |
| :-- | :-- | :-- |
| **Primary Focus** | Efficient, automated data loading on reads | Consistent, synchronized updates on writes |
| **Cache Miss Handling** | Cache fetches from DB, stores result, returns to app | Not directly applicable (focus is on writes) |
| **Write Handling** | Can be combined with write-through, write-around, or write-back strategies | Every write updates both cache and DB simultaneously |
| **Consistency** | Consistency depends on write strategy | Strong consistency between cache and DB |
| **Performance** | Fast reads after initial miss; initial miss incurs DB latency | Writes are slower due to double-write; reads always up-to-date |
| **Best For** | Read-heavy workloads (e.g., product catalogs, news feeds) | Consistency-critical, write-sensitive workloads (e.g., banking, inventory) |
| **Complexity** | Simplifies read code; cache manages population | Simplifies consistency; may slow down writes |


---

### **Key Points for Interviews**

- **Read-through** is about how data is loaded into the cache on demand (on read).
- **Write-through** is about how data is written to both cache and persistent storage in sync (on write).
- These strategies can be used together: a system can use read-through for reads and write-through for writes, ensuring both performance and consistency.
- Be prepared to discuss trade-offs: read-through optimizes read latency but may serve stale data if writes aren't handled properly; write-through ensures consistency but at the cost of write performance.
- Mention alternatives like write-back (faster writes, eventual consistency, risk of data loss if cache fails) and write-around (writes skip cache, good for write-heavy, read-rarely scenarios).

---

### **Example Scenarios**

- **Read-Through Example:**
E-commerce product catalog: Products are rarely updated but frequently read. Read-through cache ensures fast retrieval after the first access.
- **Write-Through Example:**
Banking system: Account balances must always be accurate and consistent. Write-through cache ensures every update is reflected in both cache and database immediately.

---

Understanding these patterns and their trade-offs is vital for system design interviews, especially when discussing scalable, high-performance, and consistent architectures.
