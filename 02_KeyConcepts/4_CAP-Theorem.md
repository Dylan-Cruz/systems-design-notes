## CAP Theorem: Essential Notes for System Design Interviews

**Definition and Core Idea**

- The CAP theorem, formulated by Eric Brewer, states that in a distributed system, it is impossible to simultaneously guarantee all three of the following properties:
  - **Consistency (C):** Every read receives the most recent write or an error. All nodes see the same data at the same time.
  - **Availability (A):** Every request receives a (non-error) response, even if it is not the most recent data.
  - **Partition Tolerance (P):** The system continues to operate despite arbitrary network partitions (communication breakdowns between nodes).

**Key Implications**

- In practice, partition tolerance is non-negotiable for distributed systems because network failures are inevitable. This means, during a partition, you must choose between consistency and availability.
- The theorem is often summarized as: **In the presence of a network partition, a distributed system must choose either Consistency or Availability**.

## CAP Theorem Properties Explained

| Property                | Description                                                                             | Example Scenario                   |
| :---------------------- | :-------------------------------------------------------------------------------------- | :--------------------------------- |
| Consistency (C)         | All nodes return the same data at the same time.                                        | Banking systems, ticket booking    |
| Availability (A)        | Every request gets a response, but data may be stale.                                   | Social media feeds, caches         |
| Partition Tolerance (P) | System continues to function even if network failures split nodes into isolated groups. | Any large-scale distributed system |

**CA, CP, AP Explained**

- **CA (Consistency + Availability):** Only possible if there is no partition. Rare in real-world distributed systems.
- **CP (Consistency + Partition Tolerance):** System remains consistent and tolerates partitions, but may become unavailable during a partition (e.g., banking systems).
- **AP (Availability + Partition Tolerance):** System remains available and tolerates partitions, but may return stale data (e.g., social media, caches).

## Practical Trade-offs and System Design

**How to Apply in Interviews**

- **Start with Requirements:** Always clarify if the system should favor consistency or availability during network partitions.
- **Discuss Trade-offs:** Show you understand the impact of each choice on user experience and system reliability.
- **Use Real-world Examples:**
  - _Consistency Priority (CP):_ Financial transactions, ticket booking, e-commerce inventory.
  - _Availability Priority (AP):_ Social media timelines, product catalogs, DNS, caches.

**Technology Choices**

- **Consistency-first (CP):** Traditional RDBMS (PostgreSQL, MySQL), Google Spanner, DynamoDB (strong consistency mode).
- **Availability-first (AP):** NoSQL databases (Cassandra, DynamoDB default), caching systems.

## Common Interview Questions

- Explain the CAP theorem and its relevance to distributed systems.
- Given a scenario (e.g., global chat app, e-commerce site), which CAP properties would you prioritize and why?
- How would you handle data consistency in a globally distributed application?
- Provide examples of systems that prioritize availability over consistency and explain why.

## Tips for Discussing CAP in Interviews

- **Demonstrate Understanding:** Clearly define each CAP property and why partition tolerance is essential.
- **Analyze Trade-offs:** Relate your design choices to user expectations and business requirements.
- **Reference Real Systems:** Use known architectures to illustrate your points (e.g., why Amazon Dynamo favors AP, why Google Spanner targets CP).
- **Discuss Impact:** Explain how your choice affects latency, user experience, and system reliability.

## Common Misconceptions

- **Consistency in CAP ≠ ACID Consistency:** CAP consistency refers to all nodes seeing the same data, not transactional consistency.
- **CA Systems Are Rare:** In distributed systems, network partitions are inevitable, so CA is not a practical option.

---

**Summary:**
The CAP theorem is foundational for system design interviews. In distributed systems, you must choose between consistency and availability during network partitions. Understand the trade-offs, relate them to real-world scenarios, and articulate your reasoning clearly in interviews.
