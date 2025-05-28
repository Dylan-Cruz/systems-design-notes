# Systems Design Interview

Systems design interviews are held to gauge whether you can apply engineering knowledge to real-world system architecture challenges. Problems are meant to be open ended so there isn't a single correct answer. The emphasis is on your approach and reasoning behind your design. Interviewers want to see how you think through problems and make decisions.

## What is assessed

- **Problem solving skills**: can you navigate complex ambiguous problems and figure out a viable design?
- **Evaluate Technical Knowledge**: gauge understanding of system architecture components
- **Scalability and Reliability**: does your system meet the characteristics of a distributed system?
- **Trade-off analysis**: why you chose a certain approach compared to another
- **Communication and collaboration**: can you articulate your ideas well

## Approach

1. Establish and Clarify Requirements
   - Clarify what parts of the system we should be focusing on
   - What are the functional requirements (What does it do)?
   - What are the Non functional requirements (How does it do it)?
2. Estimation
   - Consider things like:
     - Storage requirements - amount of data stored and replication for durability
     - Network throughput - determine bandwidth for traffic in/out
     - Response latency - time taken for api to response to a request
     - Traffic estimation - expected load or requests per second (DAUs)
     - Memory estimation - memory requirements for caching
     - Bandwidth estimation - data transfer rate between servers or clients
     - Resource estimation - evaluate the number of servers, CPUs, GPUs or other resources required to handle loads
     - Cost analysis - Roughly estimate infrastructure costs
     - Load estimation - Predict peak loads and average loads
     - Availability numbers - Factor in redundancy and fault tolerance to meet service level agreements
3. System Interface Definition
   - Define the api expected from the system
4. Data Model
   - Identify the major data entities
   - Use these to help inform aspects of the system
5. High Level Design
   - Draw a block diagram with 5-6 boxes representing the core components of the system
   - Identify enough components to solve the problem end to end
6. Detailed Design
   - Dig deeper into two or three major components
   - Present different approaches, their pros and cons, and explain why an approach is preferred
7. Identify and Resolve Bottlenecks
   - Discuss as many bottlenecks as possible and approaches to mitigate them
