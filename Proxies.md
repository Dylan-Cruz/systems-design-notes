## Essential Notes on Proxies for System Design Interviews

**Definition and Core Role**

A proxy is an intermediary server that sits between a client and an application server, forwarding requests and responses between the two. Proxies are fundamental in system design for improving security, performance, scalability, and control over network traffic.

---

**Types of Proxies**

| Type          | Description                                                                                    | Common Use Cases                                                   |
| :------------ | :--------------------------------------------------------------------------------------------- | :----------------------------------------------------------------- |
| Forward Proxy | Sits between clients and the internet. Manages outgoing requests from a client or client pool. | Content filtering, access control, anonymity, caching for clients. |
| Reverse Proxy | Sits between the internet and backend servers. Manages incoming requests to servers.           | Load balancing, SSL termination, caching for servers, security.    |

Other specialized proxies include:

- **API Proxies:** Decouple frontend APIs from backend services, enabling monitoring, protocol translation, and security.
- **CDN Proxies:** Cache and serve static content closer to users for faster delivery.
- **DNS, SMTP, TOR, SEO Proxies:** Serve specific functions like DNS resolution, email filtering, anonymity, and web scraping.

---

**Key Functions and Benefits**

- **Caching:** Proxies can store frequently requested resources, reducing latency and bandwidth usage.
- **Security:** They can filter malicious traffic, block unwanted content, and hide internal network details.
- **Anonymity:** Forward proxies can mask client IP addresses; reverse proxies can hide backend server details.
- **Load Balancing:** Reverse proxies distribute incoming requests across multiple servers, improving scalability and reliability.
- **Access Control \& Monitoring:** Proxies can enforce policies, monitor usage, and log traffic for compliance or troubleshooting.
- **Request/Response Transformation:** Proxies can alter headers, encrypt/decrypt data, or compress traffic.

---

**Drawbacks and Considerations**

- **Single Point of Failure:** If not properly architected (e.g., without redundancy), proxies can become bottlenecks or points of failure.
- **Configuration Complexity:** Setting up and maintaining proxies, especially for large-scale systems, can be challenging.
- **Latency:** Additional network hops can introduce latency, especially if proxies are overloaded or poorly placed.
- **Security Risks:** If compromised, a proxy can expose sensitive traffic or become a vector for attacks.
- **Cost:** High-availability proxy infrastructure can be expensive to deploy and maintain.

---

**When to Use Proxies in System Design**

- To enforce security boundaries between clients and servers.
- To improve performance via caching or load balancing.
- To centralize authentication, logging, or access control.
- To enable protocol translation or legacy system integration.
- To provide anonymity or geo-location masking for clients or services.

---

**Common Interview Scenarios**

Proxies are relevant in system design interview questions involving:

- Designing scalable web applications (e.g., Twitter, e-commerce platforms).
- Building web crawlers or APIs that need rate limiting or security layers.
- Architecting systems that require high availability, redundancy, or global distribution.

---

**Summary Table: Forward vs. Reverse Proxy**

| Feature          | Forward Proxy                     | Reverse Proxy                            |
| :--------------- | :-------------------------------- | :--------------------------------------- |
| Sits between     | Client and Internet               | Internet and Backend Servers             |
| Main Purpose     | Client privacy, content filtering | Load balancing, SSL termination, caching |
| Common Users     | Corporations, individuals         | Web services, APIs, large websites       |
| Example Use Case | Blocking sites for employees      | Distributing traffic among web servers   |
