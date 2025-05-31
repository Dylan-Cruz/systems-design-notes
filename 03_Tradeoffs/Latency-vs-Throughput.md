## Latency vs Throughput: Essential Notes for System Design Interviews

Understanding the distinction and interplay between *latency* and *throughput* is fundamental for system design interviews, as these metrics directly impact user experience, scalability, and system efficiency.

---

### **Definitions**

| Metric | Description | Typical Units |
| :-- | :-- | :-- |
| Latency | Time taken to process a single request or the delay before a response starts | milliseconds (ms), seconds |
| Throughput | Amount of work or number of requests processed per unit time | requests per second (RPS), queries per second (QPS), MBps, TPS |


---

### **Key Differences**

- **Latency** is about *speed*: how quickly a single operation completes.
*Example*: The time it takes for a user to receive a search result after hitting "Enter".
- **Throughput** is about *capacity*: how many operations the system can handle simultaneously or over a period.
*Example*: How many search queries per second Google can process globally.

---

### **Why They Matter in System Design**

- **User Experience**: Low latency ensures responsiveness (critical for real-time apps like gaming or chat), while high throughput is crucial for handling large traffic volumes (essential for high-traffic web services).
- **Scalability**: High throughput systems scale to serve more users, but must not sacrifice latency to the point of degrading user experience.
- **Trade-offs**: Optimizing for one can impact the other. For example, batching requests can improve throughput but may increase latency for individual requests.

---

### **Common Trade-Offs**

| Scenario | Latency | Throughput | Example Use Case |
| :-- | :-- | :-- | :-- |
| Real-time chat/gaming | Must be low | Moderate-high | User expects instant feedback |
| Batch analytics processing | Can be higher | Must be high | Overnight data aggregation |
| High-traffic web API | Should be low | Must be high | E-commerce, search engines |
| Streaming video | Should be low | High | Smooth playback |


---

### **Examples**

- **Ride-sharing App**:
    - Prioritizing *low latency* matches riders and drivers quickly, but may limit how many requests can be processed during peak times.
    - Prioritizing *high throughput* handles many requests during surges, but may delay individual matches, increasing latency.
- **Web Search**:
    - Google targets <100ms latency per search, but also must handle tens of thousands of queries per second.

---

### **Strategies to Optimize**

**Improving Latency**

- Use caching (e.g., CDNs, in-memory caches).
- Optimize network paths and minimize hops.
- Use faster hardware and efficient protocols (e.g., HTTP/2).
- Optimize database queries and indexing.

**Improving Throughput**

- Load balancing across servers.
- Horizontal scaling (adding more servers).
- Asynchronous and parallel processing.
- Efficient resource management (e.g., thread pools, event-driven architectures).

**Balancing Both**

- Asynchronous processing and batching (improves throughput, may impact latency).
- Profiling, monitoring, and performance testing to identify bottlenecks and tune accordingly.

---

### **How to Discuss in Interviews**

- **Quantify**: Specify expected latency (e.g., “target <100ms per request”) and throughput (e.g., “handle 10,000 RPS”).
- **Justify**: Explain trade-offs based on use case (e.g., “For a chat app, low latency is critical, so I’ll prioritize response time over batch processing”).
- **Mitigate**: Propose strategies to optimize both, or explain why one is prioritized over the other for the business case.
- **Monitor**: Emphasize the importance of real-time monitoring and load testing to ensure both metrics meet SLAs as the system scales.

---

### **Summary Table**

| Aspect | Latency | Throughput |
| :-- | :-- | :-- |
| What | Time per request | Requests handled per second |
| Focus | Speed/responsiveness | Capacity/volume |
| User Impact | Perceived snappiness | System can serve more users |
| Typical Units | ms, s | RPS, QPS, MBps, TPS |
| Optimization | Caching, fast paths, protocol tuning | Load balancing, scaling, concurrency |
| Trade-off | Lowering latency may reduce max throughput | Increasing throughput can increase latency |


---

### **Key Takeaways for Interviews**

- Always define both metrics clearly.
- Discuss expected values and how your design will achieve them.
- Explain trade-offs and mitigation strategies.
- Relate your choices to the specific business or user requirements.

Mastering latency and throughput concepts, and articulating their trade-offs, is essential for success in systems design interviews.
