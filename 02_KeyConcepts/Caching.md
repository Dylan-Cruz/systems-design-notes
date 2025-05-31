## Essential Notes on Caching for System Design Interviews

**Definition and Purpose**

- Caching is a high-speed data storage layer that stores frequently accessed or computationally expensive data, enabling faster retrieval and reducing load on backend systems.
- The primary goals: reduce latency, improve system performance, enhance scalability, and lower operational costs.

**Where to Cache: Caching Layers**

- **Client-side cache:** Data is stored on the user’s device or browser. Ideal for static, infrequently changing data.
- **Edge cache/CDN:** Content is cached on geographically distributed edge servers to deliver static assets (images, videos, scripts) closer to end users.
- **Application-level cache:** Frequently accessed data is cached within the application process or server memory.
- **Database cache:** Results of common queries or objects are cached to reduce database load and latency.
- **Distributed cache:** Data is cached across multiple nodes for scalability and high availability, commonly using solutions like Redis or Memcached.
- **Operating system and hardware cache:** Includes CPU caches (L1, L2, L3), disk caches, and file system caches that optimize low-level data access.

**Benefits of Caching**

- **Performance:** Reduces data retrieval time, improving user experience.
- **Scalability:** Offloads backend systems, allowing support for more concurrent users.
- **Availability and Reliability:** Cached data can be served even if the backend is temporarily unavailable.
- **Cost reduction:** Fewer backend operations and reduced bandwidth usage lower infrastructure costs.

**Core Caching Strategies**

- **Eviction Policies:** Determine which data to remove when the cache is full:
  - _Least Recently Used (LRU):_ Evicts the least recently accessed items.
  - _Most Recently Used (MRU):_ Evicts the most recently accessed items.
  - _First-In-First-Out (FIFO):_ Evicts items in the order they were added.
  - _Random Replacement:_ Randomly evicts items.
- **Write Policies:**
  - _Write-Through:_ Data is written to both cache and storage simultaneously (ensures consistency, higher write latency).
  - _Write-Behind (Write-Back):_ Data is written to cache first, then asynchronously to storage (faster writes, risk of data loss on failure).
- **Expiration and Invalidation:**
  - _Time-to-Live (TTL):_ Cached items expire after a set period.
  - _Manual/Programmatic Invalidation:_ Items are removed or refreshed based on application logic or data changes.
- **Sharding and Consistency:**
  - _Sharding:_ Distributes cache data across nodes for scalability (key-based, range-based, hash-based, consistent hashing).
  - _Consistency:_ Ensuring cache and source of truth remain synchronized, especially in distributed systems.

**Best Practices and Considerations**

- **Cache Hit/Miss:** Aim for a high cache hit rate (data found in cache) to maximize benefits; misses require fetching from the source.
- **Data Selection:** Cache data that is expensive to recompute, slow to fetch, or frequently requested.
- **Staleness and Consistency:** Understand trade-offs between performance and data freshness. Some systems tolerate stale data for speed, others require strict consistency.
- **Fault Tolerance:** Use distributed cache clusters and redundancy to avoid single points of failure.
- **Cache Size and Resource Management:** Balance cache size with available memory and system resources to avoid evicting valuable data too soon.

**Common Use Cases**

- Caching web pages, API responses, database query results, images, videos, and computed values.
- Reducing load on microservices and supporting distributed architectures.

**Summary Table: Caching Layers and Examples**

| Layer/Type        | Example Use Case                    | Typical Technology             |
| :---------------- | :---------------------------------- | :----------------------------- |
| Client-side       | Browser caching of images/scripts   | Browser cache, Service Workers |
| Edge/CDN          | Static asset delivery               | Cloudflare, Akamai             |
| Application-level | In-memory caching of user sessions  | Local memory, Guava            |
| Database          | Query result caching                | Redis, Memcached               |
| Distributed cache | Shared cache for microservices      | Redis Cluster, Memcached       |
| OS/Hardware       | Disk, file, CPU instruction caching | OS disk cache, CPU L1/L2/L3    |

**Key Takeaways**

- Caching is fundamental for building performant, scalable, and reliable systems.
- Understand the trade-offs between speed, consistency, and complexity.
- Be ready to discuss eviction, expiration, and invalidation strategies, and to justify caching choices based on system requirements.
