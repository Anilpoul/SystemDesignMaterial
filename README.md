# System Design Interview Preparation Guide

## Introduction
System design interviews evaluate your ability to architect large-scale distributed systems. They test your knowledge of scalability, reliability, security, and trade-offs in system architecture.

## 1. Scalability
Scalability refers to a system's ability to handle increasing workloads by adding resources. There are two types of scalability:
- **Vertical Scaling (Scaling Up)**: Increasing the power of a single machine (e.g., adding more CPU, RAM, or disk).
- **Horizontal Scaling (Scaling Out)**: Adding more machines to distribute the load (e.g., adding multiple servers in a distributed system).

### Example: Scaling a Web Application
- A single-server web app faces slow response times as users increase.
- **Vertical Scaling**: Upgrade the server to a higher CPU and RAM.
- **Horizontal Scaling**: Add more servers behind a Load Balancer to distribute traffic.

## 2. Load Balancing
Load balancers distribute incoming network traffic across multiple servers to ensure reliability and efficiency.

### Types of Load Balancing Algorithms
- **Round Robin**: Requests are distributed sequentially among servers.
- **Least Connections**: Directs traffic to the server with the least active connections.
- **IP Hashing**: Assigns a request to a server based on the user's IP address.

### Example: Handling Traffic Spikes
If a website receives millions of requests per second, a load balancer ensures that no single server is overwhelmed.

## 3. Database Design
### SQL vs NoSQL
- **SQL Databases**: Structured, use relational tables (MySQL, PostgreSQL).
- **NoSQL Databases**: Schema-less, better for scalability (MongoDB, Cassandra).

### Database Partitioning
Partitioning helps distribute data across multiple databases.
- **Range-based Partitioning**: Data is divided based on ranges (e.g., user IDs 1-1000 in one DB, 1001-2000 in another).
- **Hash-based Partitioning**: Data is stored based on a hash function, ensuring even distribution.

### Replication Strategies
- **Master-Slave Replication**: One master database handles writes, while replicas serve reads.
- **Multi-Master Replication**: Multiple databases can handle read and write operations.

### Example: Designing a Database for an E-Commerce System
- **Product Data**: Stored in a relational database for ACID compliance.
- **User Sessions**: Stored in NoSQL for fast retrieval.
- **Orders**: Stored with replication to prevent data loss.

## 4. Caching
Caching stores frequently accessed data in memory to reduce latency.

### Cache Invalidation Strategies
- **Write-Through Cache**: Data is written to cache and database simultaneously.
- **Write-Back Cache**: Data is written to cache first and periodically updated in the database.

### Example: Optimizing a Social Media Feed
Instead of fetching user posts from the database every time, cache popular posts in Redis to reduce response time.

## 5. Microservices Architecture
Microservices break a monolithic system into smaller, independently deployable services.

### Benefits
- Independent scalability.
- Fault isolation.
- Easier deployment and updates.

### Example: Building a Ride-Sharing App
- **User Service**: Handles authentication.
- **Ride Matching Service**: Matches drivers with passengers.
- **Billing Service**: Manages payments.

## 6. Message Queues
Message queues help decouple services by allowing asynchronous communication.

### Popular Message Queues
- **Apache Kafka**: High throughput event streaming.
- **RabbitMQ**: Lightweight messaging.

### Example: Processing Orders in an E-Commerce Platform
Instead of processing an order immediately, an order request is placed in a queue, allowing background workers to handle it asynchronously.

## 7. Rate Limiting
Rate limiting controls the number of requests a user can make in a given timeframe.

### Algorithms
- **Token Bucket**: Requests are only processed if tokens are available.
- **Leaky Bucket**: Requests are processed at a fixed rate to prevent sudden spikes.

### Example: Preventing DDoS Attacks
A rate-limiter ensures users can only send a fixed number of login requests per minute to prevent brute-force attacks.

## 8. CAP Theorem
CAP theorem states that a distributed system can only guarantee two out of three properties:
- **Consistency**: Every read receives the latest write.
- **Availability**: Every request receives a response.
- **Partition Tolerance**: The system continues functioning despite network failures.

### Example: Designing a Banking System
- A bank requires **Consistency** and **Partition Tolerance** to ensure correct balances are displayed.

## 9. Content Delivery Networks (CDNs)
CDNs distribute static content (images, videos, scripts) across multiple geographically dispersed servers.

### Example: Streaming Videos on YouTube
CDNs cache videos on edge servers close to users, reducing latency and server load.

## 10. Security Considerations
Security is critical in system design to protect user data and prevent attacks.

### Best Practices
- **Authentication**: Use OAuth, JWT.
- **Encryption**: Encrypt data in transit (TLS) and at rest (AES).
- **DDoS Protection**: Use rate limiting and CDNs.

### Example: Securing an Online Payment System
A payment gateway must encrypt transaction details using TLS and use token-based authentication to prevent fraud.

## 11. Monitoring & Logging
Monitoring tools track system health and detect failures.

### Example: Monitoring a Cloud-Based Application
- Use **Prometheus** for real-time metrics.
- Use **ELK Stack** (Elasticsearch, Logstash, Kibana) for log aggregation.

## 12. Real-World System Design Examples
### **1. Design a URL Shortener (Like Bit.ly)**
#### Requirements
- Shorten long URLs.
- Handle redirections.
- Expiry mechanism for links.

#### Design Components
- **Database**: Stores short-to-long URL mappings.
- **Hashing**: Generates unique short URLs.
- **Caching**: Stores popular URLs for fast retrieval.
- **Load Balancer**: Distributes requests across multiple servers.

### **2. Design an E-Commerce System (Like Amazon)**
#### Requirements
- Product listing, Cart, Checkout, Order Processing.

#### Design Components
- **Product Service**: Handles inventory.
- **Cart Service**: Manages user carts.
- **Payment Service**: Processes payments.
- **Order Service**: Handles order fulfillment.
- **Message Queue**: Processes asynchronous tasks.

### **3. Design a Chat System (Like WhatsApp)**
#### Requirements
- Real-time messaging.
- Online/Offline status.
- Message storage.

#### Design Components
- **WebSockets**: Enables real-time messaging.
- **Database Replication**: Ensures message durability.
- **Caching**: Stores recent messages for fast retrieval.

## Conclusion
System design is a critical skill for software engineers. By understanding core concepts, architectural trade-offs, and real-world use cases, you can build scalable, efficient, and reliable systems. Keep practicing different system design problems and refining your approach!

