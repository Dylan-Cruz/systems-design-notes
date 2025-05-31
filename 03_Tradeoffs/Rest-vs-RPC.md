<img src="https://r2cdn.perplexity.ai/pplx-full-logo-primary-dark%402x.png" class="logo" width="120"/>

# Prepare notes on Rest v RPC essential to the systems design interview process

Here are concise, interview-focused notes on REST vs RPC essential for systems design interviews:

## REST vs RPC: Essential Comparison for Systems Design Interviews


---

### 1. **Architectural Style and Focus**

- **REST (Representational State Transfer)**
    - Resource-oriented architecture.
    - Interacts with resources identified by URIs.
    - Uses standard HTTP methods (GET, POST, PUT, DELETE) for CRUD operations.
    - Stateless: Each request contains all info needed; server does not maintain client state.
    - Emphasizes uniform interface and resource representation (JSON, XML).
- **RPC (Remote Procedure Call)**
    - Action-oriented architecture.
    - Focuses on executing specific functions or procedures remotely.
    - Can use multiple protocols (HTTP, TCP, etc.).
    - Can be stateless or stateful depending on implementation.
    - Client calls remote methods as if local, passing parameters; server executes and returns results.

---

### 2. **Communication and Protocol**

| Aspect | REST | RPC |
| :-- | :-- | :-- |
| Protocol | Primarily HTTP | HTTP, TCP, or other protocols |
| Methods/Verbs | Standard HTTP verbs (GET, POST, PUT, DELETE) | Usually GET and POST; method calls |
| Data Format | Flexible (JSON, XML, etc.) | Often specific formats (XML-RPC, JSON-RPC, gRPC uses Protobuf) |
| Statelessness | Always stateless | Can be stateless or stateful |
| Interface | Uniform interface with resource URIs | Interface Definition Language (IDL) defines methods |


---

### 3. **Design Principles**

- **REST:**
    - Statelessness: Server does not store client context.
    - Client-server separation.
    - Uniform interface simplifies interaction.
    - Cacheability to improve performance.
    - Layered system architecture for scalability and security.
- **RPC:**
    - Remote invocation of procedures.
    - Uses stubs and skeletons generated from interface definitions.
    - May maintain session or state on server.
    - Requires interface specifications (IDL) for client-server contract.
    - Often used for tightly coupled, internal services needing low latency.

---

### 4. **Use Cases**

- **REST:**
    - Public-facing APIs.
    - Applications requiring scalability, caching, and loose coupling.
    - CRUD operations on resources (e.g., user profiles, products, orders).
    - Web services where standard HTTP semantics are beneficial.
- **RPC:**
    - Internal microservices communication.
    - Action-oriented operations like payment processing, inventory updates.
    - Performance-critical, low-latency scenarios.
    - When you need to invoke specific procedures rather than manipulate resources.

---

### 5. **Advantages and Disadvantages**

| Aspect | REST Advantages | REST Disadvantages | RPC Advantages | RPC Disadvantages |
| :-- | :-- | :-- | :-- | :-- |
| Simplicity | Uses standard HTTP verbs, easy to understand | Can cause over-fetching or under-fetching | Straightforward function calls | Can be complex due to interface definitions |
| Scalability | Statelessness improves scalability | Lack of strict standardization | Efficient for tightly coupled systems | Less flexible, often tightly coupled |
| Performance | Leverages HTTP caching | May require multiple calls for complex operations | Low latency, efficient communication | May maintain state, reducing scalability |
| Flexibility | Supports multiple data formats | Limited to CRUD operations | Supports various protocols | Less suited for public APIs |


---

### 6. **Example**

- **REST Example:**
Managing products in an e-commerce app via endpoints like `/products` using GET to fetch, POST to create, PUT to update, DELETE to remove products.
- **RPC Example:**
Internal payment service exposing a method `ProcessPayment(amount, accountId)` invoked remotely by clients to perform payment transactions.

---

### 7. **Summary**

| Feature | REST | RPC |
| :-- | :-- | :-- |
| Orientation | Resource-based | Action-based |
| Protocol | HTTP | HTTP, TCP, others |
| State | Stateless | Stateful or stateless |
| Interface | Uniform interface, URIs | Interface Definition Language (IDL) |
| Use Case | Public APIs, CRUD operations | Internal services, commands |
| Scalability | High | Moderate |
| Complexity | Lower | Higher due to interface specs |


---

These notes cover the core distinctions and practical considerations of REST vs RPC in systems design interviews, helping articulate when and why to choose each approach effectively[^1_1][^1_2][^1_4][^1_5][^1_6][^1_7][^1_8].

<div style="text-align: center">⁂</div>

[^1_1]: https://codesignal.com/learn/courses/ai-interviews-system-architecture-and-design/lessons/principles-of-restful-api-design

[^1_2]: https://blog.stackademic.com/designing-rest-api-ba7ff258ea63?gi=b645b2811b36

[^1_3]: https://www.youtube.com/watch?v=q-XBIen19Pw

[^1_4]: https://iq.opengenus.org/rpc-vs-rest/

[^1_5]: https://www.youtube.com/watch?v=w2NrdAGrhCI

[^1_6]: https://www.linkedin.com/pulse/distinguishing-rpc-rest-architectural-approaches-lavkesh-dwivedi-ulojc

[^1_7]: https://aws.amazon.com/compare/the-difference-between-rpc-and-rest/

[^1_8]: https://www.designgurus.io/course-play/grokking-the-system-design-interview/doc/rest-vs-rpc

[^1_9]: https://www.tryexponent.com/blog/system-design-interview-guide

[^1_10]: https://www.designgurus.io/answers/detail/what-are-the-5-basic-principles-of-rest-api

[^1_11]: https://www.hellointerview.com/learn/system-design/core-concepts/networking-essentials

[^1_12]: https://gist.github.com/kanglicheng/4069796f4404fe5a704f7e06999b0e42

[^1_13]: https://www.designgurus.io/blog/system-design-interview-fundamentals

[^1_14]: https://interviewing.io/guides/system-design-interview/part-two

[^1_15]: https://www.reddit.com/r/cscareerquestionsEU/comments/r7ozqp/how_to_prepare_for_a_systems_design_interview/

[^1_16]: https://www.hellointerview.com/learn/system-design/in-a-hurry/core-concepts

[^1_17]: https://learn.microsoft.com/en-us/azure/architecture/best-practices/api-design

[^1_18]: https://blog.stackademic.com/cracking-front-end-system-design-interviews-a-comprehensive-guide-07d9e5c06b57?gi=401e15c17fef

[^1_19]: https://www.youtube.com/watch?v=SHkbPm1Wrno

[^1_20]: https://www.joinleland.com/library/a/20-common-system-design-interview-questions-with-sample-answers

[^1_21]: https://people.engr.tamu.edu/bettati/Courses/662/2007A/Slides/Handouts/hRPC.pdf

[^1_22]: https://www.reddit.com/r/computerscience/comments/j4djbh/rpc_vs_rest/

[^1_23]: https://softwareengineering.stackexchange.com/questions/345256/why-is-rest-commonly-used-instead-of-rpc-like-mechanisms-in-web-applications

[^1_24]: https://www.cs.cornell.edu/info/people/chichao/ew98-1.pdf

[^1_25]: https://softwareengineering.stackexchange.com/questions/228475/rest-and-rpc-in-multi-tier-api

