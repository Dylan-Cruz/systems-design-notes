## Token Bucket vs Leaky Bucket: Essential Notes for Systems Design Interviews

Understanding the differences between the Token Bucket and Leaky Bucket algorithms is crucial for system design interviews, especially when discussing rate limiting, traffic shaping, or API protection. Below is a concise, interview-focused comparison.

---

### **Token Bucket Algorithm**

- **Mechanism**
    - Tokens are generated at a fixed rate and placed into a bucket with a maximum capacity.
    - Each incoming request must consume a token to proceed.
    - If tokens are available, requests are allowed immediately—even in bursts—until tokens run out.
    - If no tokens are available, requests are delayed or rejected until tokens are replenished.
- **Key Properties**
    - **Allows bursts:** Can handle sudden spikes in traffic up to the number of available tokens.
    - **Configurable:** Both the token generation rate and bucket size can be adjusted to control throughput and burst tolerance.
    - **Average Rate:** Over time, the average processing rate is limited by the token refill rate.
    - **Discard Policy:** If the bucket is full, additional tokens are discarded, but incoming requests are not dropped unless there are no tokens.
- **Use Cases**
    - APIs that need to allow occasional spikes (e.g., user actions that come in bursts).
    - Video streaming or file downloads where initial bursts are desirable for buffering.
- **Pros**
    - Flexible; supports bursty traffic.
    - Fine-grained control over rate and burst size.
- **Cons**
    - Requires state management for tokens.
    - Can be exploited if bursts are not properly bounded.

---

### **Leaky Bucket Algorithm**

- **Mechanism**
    - Incoming requests are added to a fixed-size queue (the bucket).
    - Requests are processed and leave the bucket at a constant, steady rate (the "leak" rate).
    - If the queue is full when a new request arrives, the request is dropped or delayed.
- **Key Properties**
    - **Smooths Traffic:** Enforces a uniform output rate regardless of input burstiness.
    - **No Burst Handling:** Does not allow for bursts; excess requests are dropped if the bucket is full.
    - **Simple Implementation:** Easy to reason about and implement.
- **Use Cases**
    - Scenarios requiring a steady, predictable flow (e.g., VoIP, live streaming, or payment processing).
    - Protecting backend resources from sudden load spikes.
- **Pros**
    - Predictable and consistent output rate.
    - Simple and reliable for smoothing traffic.
- **Cons**
    - Inflexible; cannot accommodate bursts.
    - May cause higher request loss under bursty loads.

---

### **Comparison Table**

| Feature | Token Bucket | Leaky Bucket |
| :-- | :-- | :-- |
| Burst Handling | Allows bursts up to bucket size | No burst; smooth, constant rate |
| Output Rate | Variable (up to burst limit), then average | Constant, steady |
| When Bucket is Full | Extra tokens discarded; requests wait or drop | Incoming requests dropped or delayed |
| Flexibility | High (configurable rate and burst size) | Low (fixed leak rate) |
| Complexity | Slightly higher (token management) | Simpler (queue management) |
| Typical Use Cases | APIs, streaming, bursty user actions | Real-time systems, steady resource usage |
| Packet/Request Loss | Only if no tokens; can queue/delay requests | If bucket full, incoming requests dropped |


---

### **Key Interview Points**

- **Token Bucket** is preferred when you need to allow short bursts while still enforcing an overall rate limit.
- **Leaky Bucket** is ideal when you need a guaranteed, smooth output rate and can’t tolerate bursts.
- Both can be implemented in distributed systems, but token bucket offers more flexibility for dynamic workloads.
- Be ready to explain trade-offs: burst tolerance (token bucket) vs. predictability (leaky bucket).

---

> Token bucket allows for bursts of data until the bucket's tokens are exhausted, making it suitable for applications where such bursts are common. In contrast, the leaky bucket smooths out the data flow, releasing packets at a steady, constant rate.

---

Use these notes to clearly explain which algorithm you would choose for a given scenario and justify your decision based on system requirements.
