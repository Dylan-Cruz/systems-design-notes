## Consistent Hashing: Essential Notes for System Design Interviews

**Consistent hashing** is a foundational concept in distributed systems, frequently discussed in systems design interviews, especially when addressing scalability, reliability, and efficient data distribution across clusters.

---

### **What Problem Does Consistent Hashing Solve?**

- **Minimizes Data Movement:** In traditional hash-based sharding (e.g., using modulo), adding or removing a server requires remapping nearly all keys, causing massive data movement and potential downtime.
- **Consistent hashing** ensures that when a node is added or removed, only a small fraction of keys need to be redistributed, dramatically reducing operational overhead and improving system availability.

---

### **How Does Consistent Hashing Work?**

- **Hash Ring Concept:** Both servers (nodes) and data keys are hashed onto a virtual circle (hash ring), typically using a hash function that maps values to a fixed range (e.g., 0 to $2^{32}-1$).
- **Data Placement:**
  - To store or retrieve a key, hash the key to a position on the ring.
  - Move clockwise until you find the first server node; that node is responsible for the key.
- **Node Addition/Removal:**
  - **Adding a Node:** Only keys that fall between the new node and its predecessor (counter-clockwise) need to move to the new node.
  - **Removing a Node:** Only keys mapped to the removed node are reassigned to its successor; all other keys remain unaffected.

---

### **Comparison: Consistent Hashing vs. Modulo-based Sharding**

| Feature                      | Modulo-based Sharding    | Consistent Hashing           |
| :--------------------------- | :----------------------- | :--------------------------- |
| Data movement on node change | Almost all keys remapped | Only a small subset remapped |
| Scalability                  | Poor                     | Excellent                    |
| Fault tolerance              | Low                      | High                         |
| Load balancing               | Can be uneven            | Improved with virtual nodes  |

---

### **Key Concepts for Interviews**

- **Virtual Nodes (VNodes):** To improve load balancing, each physical node can be assigned multiple positions (virtual nodes) on the ring. This helps distribute keys more evenly, preventing hot spots.
- **Binary Search for Lookup:** Server hash values are stored in sorted order, allowing O(log S) lookup time for finding the responsible node, where S is the number of servers.
- **Practical Use Cases:** Consistent hashing is integral to systems like Redis Cluster, Apache Cassandra, Amazon DynamoDB, and CDNs for distributing data, cache, or content.

---

### **When to Use Consistent Hashing in Interviews**

- **Designing distributed databases, caches, or message brokers:** When asked how to partition or shard data across nodes, consistent hashing is a robust answer.
- **Discussing scalability and fault tolerance:** Highlight how consistent hashing allows seamless scaling with minimal data movement.
- **Handling node failures and rebalancing:** Explain how the algorithm minimizes disruption during node changes.

---

### **Sample Interview Explanation**

> Consistent hashing distributes both data and nodes on a hash ring. When a node is added or removed, only a subset of keys—specifically those between the affected node and its predecessor—need to be reassigned, minimizing data movement. This makes consistent hashing ideal for scalable, fault-tolerant distributed systems. To further improve load balancing, we can use virtual nodes, assigning multiple positions on the ring to each physical node. This approach is used in systems like Cassandra and DynamoDB.

---

### **Summary Table: Consistent Hashing Key Points**

| Aspect                | Description                                       |
| :-------------------- | :------------------------------------------------ |
| Main benefit          | Minimizes data movement on cluster changes        |
| Data distribution     | Keys and nodes mapped to positions on a hash ring |
| Node addition/removal | Only a fraction of keys remapped                  |
| Load balancing        | Improved with virtual nodes (VNodes)              |
| Lookup efficiency     | O(log S) with sorted node positions               |
| Real-world usage      | Redis Cluster, Cassandra, DynamoDB, CDNs          |

---

Consistent hashing is a must-know topic for systems design interviews, especially when discussing distributed data partitioning, scalability, and resilience.
