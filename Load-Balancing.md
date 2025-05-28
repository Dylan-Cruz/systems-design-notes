## Essentials of Load Balancing for System Design Interviews

**Definition and Importance**

Load balancing is the process of distributing incoming network or application traffic across multiple backend servers, ensuring no single server becomes a bottleneck or point of failure. It is fundamental to building scalable, highly available, and reliable distributed systems.

**Key Benefits**

- **High Availability:** Prevents downtime by redirecting traffic if a server fails.
- **Scalability:** Enables horizontal scaling by allowing more servers to be added or removed seamlessly.
- **Performance:** Reduces latency and improves response times by spreading load evenly.
- **Redundancy:** Eliminates single points of failure (though the load balancer itself must also be redundant).
- **Abstraction:** Clients interact with the load balancer, not individual servers, simplifying service discovery and deployment.

## Core Concepts and Terminology

- **Load Balancer:** Hardware or software component that distributes requests to backend servers.
- **Backend Servers:** The pool of servers receiving traffic from the load balancer.
- **Health Checks:** Periodic checks to ensure backend servers are available; unhealthy servers are removed from rotation.
- **Session Persistence (Sticky Sessions):** Ensures requests from the same client are routed to the same server to maintain state.
- **SSL/TLS Termination:** Decrypts secure traffic at the load balancer, offloading backend servers.

## Types of Load Balancers

| Type         | Layer       | Routing Basis         | Example Uses                 |
| :----------- | :---------- | :-------------------- | :--------------------------- |
| Layer 4 (L4) | Transport   | IP address, TCP/UDP   | Network load balancing       |
| Layer 7 (L7) | Application | HTTP headers, cookies | Web application balancing    |
| Hardware     | Physical    | Dedicated appliances  | High-throughput, low-latency |
| Software     | Software    | Runs on commodity HW  | Flexible, cloud deployments  |

- **Cloud Load Balancers:** Managed services (e.g., AWS ELB) that integrate with cloud infrastructure and auto-scaling.

## Common Load Balancing Algorithms

- **Round Robin:** Assigns requests to servers in turn; simple and effective for homogeneous environments.
- **Least Connections:** Directs traffic to the server with the fewest active connections; good for variable request loads.
- **Weighted Round Robin/Least Connections:** Assigns weights to servers based on capacity.
- **IP Hash:** Uses client IP to consistently route requests, supporting session persistence.
- **Random:** Randomly selects a server; simple but less optimal for uneven loads.
- **Power of d Choices:** Picks d random servers, then selects the least loaded among them; balances randomness and load-awareness.

## Placement in System Architecture

Load balancers can be used at multiple layers:

- Between clients and web servers.
- Between web servers and application/cache servers.
- Between application servers and databases.

## Best Practices

- **Redundancy:** Deploy multiple load balancers to prevent a single point of failure.
- **Health Monitoring:** Continuously check server health and remove unhealthy nodes.
- **Security:** Use SSL/TLS termination, DDoS protection, and ensure the load balancer itself is protected.
- **Monitoring and Metrics:** Track performance, latency, and error rates to detect and resolve issues quickly.
- **Algorithm Selection:** Choose based on server heterogeneity, request patterns, and system requirements.

## Limitations and Considerations

- **Load Balancer as a Bottleneck:** If not properly scaled or redundant, the load balancer can itself become a point of failure.
- **Session State:** Stateless applications are easier to load balance; stateful sessions may require sticky sessions or distributed caches.
- **Not a Cure-All:** Load balancing cannot fix inefficient backend logic or slow databases; holistic system design is required.

## Interview Tips

- Be ready to discuss when and why to introduce load balancing in a system.
- Explain trade-offs between different algorithms and types of load balancers.
- Demonstrate awareness of failure scenarios and mitigation strategies (e.g., active-passive load balancer pairs).
- Understand how load balancing integrates with other system components (caching, rate limiting, etc.).

---

**Summary:**
Load balancing is essential for building scalable, reliable, and performant distributed systems. Mastery of its algorithms, types, placement, and best practices is critical for system design interviews and real-world architectures.
