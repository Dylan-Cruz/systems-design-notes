## Quorum in Systems Design: Essential Interview Notes

**Definition and Importance**

- A *quorum* is the minimum number of nodes (servers or replicas) in a distributed system that must agree for an operation (read or write) to be considered successful.
- Quorums are fundamental for achieving data consistency, reliability, and fault tolerance in distributed databases, especially when nodes may fail or become unreliable.
- They are widely used in leaderless replication systems (e.g., Cassandra, DynamoDB) and consensus algorithms (e.g., Paxos, Raft).

---

## How Quorums Work

- Each distributed operation (read or write) requires responses from a subset of nodes, called a quorum, to ensure the operation's validity and consistency.
- The key rule: **Any two quorums must overlap** (share at least one node) to prevent conflicting data versions and ensure consistency.
- Quorums are defined by:
    - **N**: Total number of replicas/nodes.
    - **W**: Number of nodes that must acknowledge a write (write quorum).
    - **R**: Number of nodes that must respond to a read (read quorum).

---

## Quorum Formula

- The critical formula for strong consistency:

$$
W + R > N
$$

This ensures that every read quorum overlaps with every write quorum, so at least one node always has the latest data.

---

## Types of Quorum Systems

| Type | Description | Pros | Cons |
| :-- | :-- | :-- | :-- |
| Simple Majority Quorum | More than half the nodes form a quorum (e.g., 3 out of 5 nodes) | Easy to implement, robust | Lower availability if many nodes fail |
| Tunable Quorum | System allows configuring W and R per operation (e.g., Cassandra) | Flexible, adaptable | Misconfiguration can hurt consistency or availability |
| Sloppy Quorum | Allows writes to any available node, not just the preferred replica set | Higher availability | May increase temporary inconsistency |


---

## Trade-offs: Consistency, Availability, and Fault Tolerance

- **Higher W or R**: Increases consistency but reduces availability (system can’t proceed if enough nodes are down).
- **Lower W or R**: Increases availability but risks stale reads or lost writes.
- **Sloppy Quorums**: Used to maximize availability during network partitions or node outages, but require background processes (e.g., hinted handoff, read repair) to restore consistency.

---

## Practical Examples

- **3-node cluster, N=3**:
    - Strong consistency: W=2, R=2 (since 2+2 > 3)
    - High availability: W=1, R=1 (but risks stale reads if a node is out of sync)

---

## Interview Tips

- Be able to explain the quorum formula and why overlap is crucial for consistency.
- Discuss real-world systems (Cassandra, DynamoDB, Riak) and how they use tunable or sloppy quorums.
- Articulate the trade-offs between consistency, availability, and performance, and how quorum configuration influences these.
- Understand failure scenarios and how quorum systems maintain data integrity during node/network failures.
- Mention mechanisms like *read repair* and *anti-entropy* for reconciling inconsistencies after failures.

---

## Key Takeaways

- Quorums are essential for designing scalable, reliable, and consistent distributed systems.
- The choice of quorum size/configuration directly impacts system behavior under failure, latency, and consistency requirements.
- Mastery of quorum concepts and their trade-offs is a must-have for systems design interviews at top tech companies.
