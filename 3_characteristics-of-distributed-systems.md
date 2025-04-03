# Characteristics of Distributed Systems

## Scalability

The capability of a system, process, or network to grow to manage increased demand.

### Horizontal vs Vertical Scaling

- **Horizontal Scaling**:
  - Scale by adding more servers into your resource pool. Tasks are distributed amongst the servers in the pool.
  - Ex.) MongoDB
- **Vertical Scaling**:
  - Add capacity by increasing resources (CPU, RAM, Storage) within a single server.
  - Ex.) MySQL.

## Reliability

- The ability for the system to continue to deliver it's services in the event one or several of its software or hardware components fail.
- Ex.) a server housing a user's shopping cart data goes down, a new replica server is stood up in it's place and the data restored

## Availability

- The percentage of time that a system, service, or machine remains operational under normal conditions.
- Ex.) An aircraft that can be flown for many hours a month without much downtime has high availability.

## Reliability Vs Availability

- If a system is reliable, it is also available.
- An available system is not always reliable.

## Efficiency

- Two standard measures of efficiency are response time and throughput.
- **Response Time**: denotes the delay to obtain the response to a call/request
- **Throughput**: the number of responses delivered in a given time unit

## Serviceability or Manageability

How easy a distributed system is to operate and maintain.
