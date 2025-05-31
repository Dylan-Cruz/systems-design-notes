## PACELC Theorem: Essential Notes for System Design Interviews

The PACELC theorem is a foundational concept in distributed systems, especially relevant for system design interviews. It extends the CAP theorem by introducing latency as a critical factor, providing a more comprehensive framework for understanding trade-offs in distributed data systems.

---

**What is the PACELC Theorem?**

- **PACELC** stands for: **Partition, Availability, Consistency, Else, Latency, Consistency**.
- The theorem states:

> If a network partition (P) occurs, a distributed system must choose between Availability (A) and Consistency (C) — as per the CAP theorem. Else (E), even when the system is running normally (without partitions), the system must choose between Latency (L) and Consistency (C).

---

## Key Concepts

**1. CAP Theorem Recap (PAC):**

- **Consistency (C):** Every read receives the most recent write or an error.
- **Availability (A):** Every request receives a (non-error) response, without guarantee that it contains the most recent write.
- **Partition Tolerance (P):** The system continues to operate despite arbitrary partitioning due to network failures.

**2. PACELC Extension (ELC):**

- **Else (E):** When there is no partition,
- **Latency (L):** The system can respond quickly, possibly at the cost of consistency.
- **Consistency (C):** The system ensures all nodes see the same data, possibly at the cost of higher latency.

---

## Why PACELC Matters

- **CAP theorem** only considers the system under partition, ignoring trade-offs during normal operation.
- **PACELC theorem** highlights that even without partitions, distributed systems must balance between:
  - **Low latency** (faster responses)
  - **Strong consistency** (up-to-date, synchronized data)
- This is crucial for designing real-world systems where performance (latency) is as important as availability and consistency.

---

## System Classifications under PACELC

| Partition (P) | Else (E)                     | Example Systems                                                              | Description |
| :------------ | :--------------------------- | :--------------------------------------------------------------------------- | :---------- |
| PA / EL       | DynamoDB, Cassandra          | Prioritize Availability during partitions; prioritize low Latency otherwise. |             |
| PC / EC       | BigTable, HBase, CockroachDB | Prioritize Consistency always, both during partitions and normal operation.  |             |
| PA / EC       | MongoDB (default config)     | Prioritize Availability during partitions; prioritize Consistency otherwise. |             |
| PC / EL       | (Less common)                | Prioritize Consistency during partitions; prioritize Latency otherwise.      |             |

- **PA/EL:** High-availability, low-latency (common in NoSQL databases).
- **PC/EC:** Strong consistency, higher latency (common in traditional SQL/NewSQL databases).

---

## Interview Tips

- **Understand trade-offs:** Be prepared to discuss why a system might prioritize one property over another based on use-case (e.g., financial transactions need consistency, social feeds may favor availability and latency).
- **Use PACELC for system choices:** When asked to design a distributed system, explicitly mention the PACELC trade-offs your design makes.
- **Give examples:** Reference real-world systems and their PACELC classification to demonstrate your understanding.

---

## Summary Table

| Scenario               | Trade-off                   | Key Question                                                                     |
| :--------------------- | :-------------------------- | :------------------------------------------------------------------------------- |
| During Partition (P)   | Availability vs Consistency | "Should the system remain available or consistent when parts can't communicate?" |
| Else (no partition, E) | Latency vs Consistency      | "Should the system respond quickly or ensure all data is consistent?"            |

---

## Conclusion

The PACELC theorem is essential for system design interviews because it provides a nuanced framework for reasoning about distributed system trade-offs, not just during failures but also in normal operation. Mastery of PACELC enables you to design systems tailored to specific business needs, balancing consistency, availability, and latency.
