## Essential Knowledge for System Design Estimations

**System design estimations**—often called "back-of-the-envelope" calculations—are a critical skill for tech interviews and real-world architecture planning. They help you quickly assess feasibility, resource needs, and potential bottlenecks before committing to detailed designs.

---

### **Core Estimation Types**

You should be comfortable estimating the following system characteristics:

- **Load Estimation:** Requests per second, user traffic, or data volume.
- **Storage Estimation:** Total data stored, growth rate, and retention needs.
- **Bandwidth Estimation:** Network throughput required for data transfer.
- **Latency Estimation:** Expected response times, both sequential and parallel.
- **Resource Estimation:** Number of servers, CPU, memory, or other hardware resources.

---

### **Key Estimation Techniques**

- **Break Down the Problem:** Divide large problems into smaller, manageable components. Estimate each part, then aggregate.
- **Use Reasonable Assumptions:** When data is missing, make clear, logical assumptions based on industry standards, benchmarks, or analogous systems.
- **Round Numbers:** Use simple, round numbers for calculations to keep math quick and manageable.
- **Scientific Notation:** Express large numbers in scientific notation to avoid errors and simplify calculations (e.g., 1 billion = $10^9$).
- **Sanity Checks:** Always validate your results against real-world expectations or known benchmarks.
- **Leverage Experience:** Use knowledge from similar systems or previous projects to inform your estimates.

---

### **Estimation Workflow**

1. **Clarify Requirements:** Understand what needs to be estimated (e.g., peak load, storage per day, etc.).
2. **Ask Clarifying Questions:** Don’t hesitate to probe for missing details or constraints.
3. **State Assumptions:** Clearly articulate any assumptions you make, such as average object size or user activity patterns.
4. **Perform Calculations:** Use the techniques above to arrive at rough numbers.
5. **Communicate Thought Process:** Explain your reasoning and calculations as you go.
6. **Adjust as Needed:** Be ready to revise estimates if new information or constraints are introduced.

---

### **Common Examples**

- **Storage:** For 500 million users uploading 2 photos/day at 2 MB/photo:
  $500,000,000 \times 2 \times 2 \text{ MB} = 2,000,000,000 \text{ MB/day}$.
- **Bandwidth:** 10 million users streaming at 4 Mbps:
  $10,000,000 \times 4 \text{ Mbps} = 40,000,000 \text{ Mbps}$.
- **Latency:** For sequential API calls with 50 ms, 100 ms, and 200 ms:
  Total = $50 + 100 + 200 = 350$ ms (sequential);
  Max = $200$ ms (parallel).

---

### **Best Practices for Interviews**

- **Practice estimation frequently** with real-world scenarios (e.g., messaging apps, video streaming, social media platforms).
- **Be explicit about trade-offs** and how estimates influence design choices (e.g., sharding, replication, caching).
- **Use estimation to guide architectural decisions** and justify why certain components (e.g., CDN, load balancer) are necessary.
- **Manage your time:** Allocate a portion of your interview to estimation, but don’t get bogged down in excessive detail.

---

### **Summary Table: Estimation Essentials**

| Aspect        | What to Do                         | Example/Tip                       |
| :------------ | :--------------------------------- | :-------------------------------- |
| Load          | Estimate QPS, DAU, peak traffic    | Requests/sec = total/day ÷ 86,400 |
| Storage       | Calculate total and growth         | Users × items/user × size/item    |
| Bandwidth     | Estimate for peak and average      | Users × bitrate                   |
| Latency       | Add (sequential) or max (parallel) | 50ms + 100ms + 200ms = 350ms      |
| Resource      | Servers, CPU, RAM                  | Based on above estimates          |
| Assumptions   | State clearly                      | "Assume avg photo is 2 MB"        |
| Sanity Checks | Compare to real-world systems      | "Instagram stores X PB/year"      |

---

### **Final Tips**

- Focus on ballpark accuracy, not perfection.
- Communicate all steps and assumptions.
- Use estimation to drive and justify design trade-offs.
- Regular practice with diverse scenarios will sharpen your intuition and speed.

Mastering these estimation skills will make you stand out in system design interviews and help you design scalable, robust systems in practice.
