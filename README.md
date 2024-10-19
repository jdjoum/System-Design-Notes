# System-Design-Notes
  This repository contains notes and example code based on what I learned from the FreeCodeCamp [System Design Course](https://www.youtube.com/watch?v=F2FmTdLtb_4). It covers essential system design concepts, architectural patterns, scalability techniques, and practical design examples.

## Table of Contents
  1. [Computer Architecture](#computer-architecture)
  - [Bits and Bytes](#bits-and-bytes)
  - [Computer Storage](#computer-storage)
  - [CPU](#cpu)
  - [Compiler](#compiler)
  2. [Production App Architecture](#production-app-architecture)
  - [Continuous Integration & Continuous Deployment (CI/CD)](#continuous-integration--continuous-deployment-cicd)
  - [Load Balancer](#load-balancer)
  - [Storage](#storage)
  - [Logging & Monitoring](#logging--monitoring)
  - [Staging Environment](#staging-environment)
  3. [What is Good Design?](#what-is-good-design)
  - [Scalability](#scalability)
  - [Maintainability](#maintainability)
  - [Efficiency](#efficiency)
  - [Reliability](#reliability)
  4. [Data Management](#data-management)
  - [Moving Data](#moving-data)
  - [Storing Data](#storing-data)
  - [Transforming Data](#transforming-data)
  - [CAP Theorem](#cap-theorem)


## Computer Architecture
  
### Bits and Bytes

  At the core of all computing systems is binary data, represented by bits and bytes.

  Bits:

  A bit (short for binary digit) is the smallest unit of data in a computer. It can have only two possible values:

  - 0 or 1. These binary values are the foundation of all digital data. Every bit represents a state, such as:
  - On (1) or Off (0)
  - True (1) or False (0)

  Bytes:

  A byte is a group of 8 bits. This grouping is significant because 8-bit combinations (bytes) allow computers to represent a wide range of data, including text, numbers, and instructions.

  - A byte can represent 2⁸ (or 256) different values, ranging from 0 to 255 in decimal.
  - For example, the ASCII (American Standard Code for Information Interchange) encoding uses 1 byte to represent characters such as letters, digits, and punctuation.

  Common Units of Digital Data:

  Bytes are the fundamental building blocks for measuring data. As data size increases, larger units are used to quantify the amount of information:

  - Kilobyte (KB): 1 KB = 1,024 bytes (2¹⁰ bytes)
  - Megabyte (MB): 1 MB = 1,024 KB (2²⁰ bytes)
  - Gigabyte (GB): 1 GB = 1,024 MB (2³⁰ bytes)
  - Terabyte (TB): 1 TB = 1,024 GB (2⁴⁰ bytes)
  - Petabyte (PB): 1 PB = 1,024 TB (2⁵⁰ bytes)

  Data Representation:

  - Binary: Data in computers is represented in binary (base-2) using bits. For example, the number 5 in binary is written as 101.
  - Hexadecimal: To simplify reading binary numbers, hexadecimal (base-16) is often used. It represents each group of 4 bits with a single digit (0-9, A-F).
    - Example: The byte 11110000 in binary is F0 in hexadecimal.

  Storage and Memory:

  Bytes are critical in representing and storing:

  - Characters: Each character in text (e.g., 'A', 'B') is typically represented by one byte in encoding systems like ASCII or Unicode.
  - Integers: Small integers may be stored in 1 byte, while larger ones require 2, 4, or more bytes.
  - Floating-Point Numbers: Often use 4 or 8 bytes, depending on precision.

  Data Transfer:

  When transferring data across networks or storing it in files, the amount of data is often measured in bits per second (bps) or bytes per second (Bps):

  - Bit Rate: In network communication, data speed is often expressed in bits per second (e.g., Mbps = Megabits per second).
  - Bandwidth: Refers to the maximum rate of data transfer, measured in bps.

  Importance of Bits and Bytes in Computer Architecture:

  Bits and bytes are foundational in computer architecture because they determine:

  - Word Size: The number of bits the CPU can process at once (e.g., 32-bit or 64-bit processors).
  - Memory Addressing: The maximum amount of memory the system can address is determined by the number of bits in the address bus (e.g., a 32-bit address bus can address 4 GB of memory).
  - Instruction Representation: Machine instructions are typically encoded as a sequence of bits, where different groups of bits represent operation codes (opcodes) and operands.

  Understanding bits and bytes is essential for grasping how data is processed, stored, and communicated in digital systems.

### Computer Storage

  Computer storage refers to any computing hardware and media used to store, retain, and retrieve data. It allows systems to keep and access information, both temporarily and permanently, depending on the nature of the storage. It is one of the core components of computing, impacting everything from system performance to the ability to run applications and manage large datasets. Storage can be categorized into primary and secondary storage based on its role in data processing.

  Primary Storage (Volatile):

  Primary storage is the main memory used by a computer's CPU to perform tasks. It is fast and typically temporary, meaning data is lost when the system powers off. Primary storage is often referred to as volatile memory because of this characteristic.

  - RAM (Random Access Memory):
    - Volatile memory where data is stored for quick access by the CPU.
    - Data is lost when the computer shuts down.
    - Used for running applications and the operating system.
  - Cache Memory:
    - Very small, fast memory located inside or close to the CPU.
    - Stores frequently accessed data to reduce the time needed to retrieve it from slower main memory (RAM).
    - There are typically multiple levels (L1, L2, L3) that vary in size and proximity to the CPU cores.

  Secondary Storage (Non-Volatile):

  Secondary storage is where data is stored permanently or semi-permanently. It is slower than primary storage but can hold much larger amounts of data.

  - Hard Disk Drives (HDDs):
    - Traditional storage technology that uses spinning disks to read and write data magnetically.
    - Offers large storage capacities (multiple terabytes) at low costs.
    - Slower than modern solid-state drives.
  - Solid-State Drives (SSDs):
    - Use flash memory to store data electronically with no moving parts.
    - Faster than HDDs in terms of read/write speeds, but historically more expensive per gigabyte.
    - More durable because they are less prone to mechanical failure.

### CPU

  A **CPU (Central Processing Unit)** is the primary component of a computer responsible for interpreting and executing instructions from programs. It functions as the "brain" of the system, handling all basic operations such as arithmetic, logic, control, and input/output processes.

  - Components:
    - Control Unit (CU): Directs operations by fetching and decoding instructions from memory.
    - Arithmetic Logic Unit (ALU): Handles arithmetic (addition, subtraction) and logic operations (AND, OR).
    - Registers: Small, fast storage locations inside the CPU used to hold temporary data and instructions.

  - Operations:
    - Fetch: Retrieves instructions from memory.
    - Decode: Interprets the instructions.
    - Execute: Carries out the operation (e.g., calculation, data movement).
    - Store: Writes the result back to memory if necessary.

  - Performance Factors:
    - Clock Speed: Measured in GHz, it determines how many cycles per second the CPU can execute.
    - Cores: Modern CPUs have multiple cores, allowing parallel processing for better multitasking.
    - Cache: A small, high-speed memory in the CPU that stores frequently accessed data.

  - Multithreading: Many CPUs support executing multiple threads simultaneously, improving performance in multi-threaded applications.

  In summary, the CPU plays a critical role in running programs by executing the instructions that make up the software.

### Compiler

  A **compiler** is a program that translates source code written in a high-level programming language (like C, Java, or Python) into machine code or intermediate code that a computer's processor (CPU) can execute.

  Key Phases of a Compiler:

  1. Lexical Analysis: The source code is scanned and divided into tokens (like keywords, operators, and identifiers).
  2. Syntax Analysis (Parsing): The tokens are checked for grammatical correctness, ensuring they follow the language's rules.
  3. Semantic Analysis: The meaning of the code is verified, checking for valid data types, variable declarations, and scope.
  4. Intermediate Code Generation: An abstract, machine-independent code is generated to optimize processing across platforms.
  5. Optimization: The intermediate code is refined to make the final output more efficient, reducing memory use and speeding up execution.
  6. Code Generation: The optimized intermediate code is translated into machine code specific to the target hardware.
  7. Code Linking and Loading: The machine code is linked with libraries and converted into an executable file.

  Compilers often provide error diagnostics to help developers fix issues in their code before the final executable is produced.

## Production App Architecture

### Continuous Integration & Continuous Deployment (CI/CD)

  **CI/CD (Continuous Integration and Continuous Deployment/Delivery)** is a practice in software development that automates the process of integrating code changes, testing them, and deploying them to production.

  Key Concepts:

  - Continuous Integration (CI):
    - Developers frequently merge code changes into a shared repository.
    - Automated tests and builds are triggered to ensure the code integrates smoothly with the existing codebase.
    - Benefits: Early detection of integration issues, improving code quality.
  - Continuous Deployment (CD):
    - Every change that passes the automated testing phase is automatically deployed to production.
    - Requires a high degree of confidence in the test coverage.
    - Benefits: Faster delivery of features and bug fixes to users.
  - Continuous Delivery (alternative CD):
    - Code changes are automatically prepared for release to production but require manual approval before deployment.
    - Balances automation with human oversight, making sure deployments are safe and controlled.

  Tools Commonly Used:

  - CI Tools: Jenkins, GitLab CI, Travis CI.
  - CD Tools: AWS CodePipeline, CircleCI, GitHub Actions.

  Key Benefits:

  - Reduces manual errors.
  - Ensures consistent software releases.
  - Improves collaboration and speeds up feedback loops.
  - Automates deployment processes.

### Load Balancer

  A **Load Balancer** is a system or device that distributes incoming network traffic across multiple servers to ensure no single server becomes overwhelmed. It helps improve the availability, reliability, and scalability of applications.

  Key Functions:

  1. Traffic Distribution: Distributes requests evenly across servers, preventing overload on any one server.
  2. Health Monitoring: Regularly checks the health of servers, ensuring traffic is only directed to those that are functioning correctly.
  3. Failover: If a server fails, the load balancer reroutes traffic to healthy servers, ensuring high availability.
  4. Scalability: Enables easy addition of new servers to handle increasing traffic.
  5. Session Persistence: Ensures that a user's session is maintained by routing subsequent requests to the same server.

  Types of Load Balancers:

  - Layer 4 (Transport Layer): Distributes traffic based on IP address and port (e.g., TCP/UDP).
  - Layer 7 (Application Layer): Distributes traffic based on application-level data (e.g., HTTP headers, cookies).

  Load Balancing Algorithms:

  - Round Robin: Distributes requests sequentially across servers.
  - Least Connections: Sends traffic to the server with the fewest active connections.
  - IP Hash: Routes requests based on the client’s IP address.

  Benefits:

  - Improved Performance: By distributing traffic, load balancers reduce response time and increase throughput.
  - High Availability: Ensures that services remain available even if some servers fail.
  - Flexibility: Supports scaling up or down depending on traffic load.

  Popular load balancers include NGINX, HAProxy, and cloud-based solutions like AWS Elastic Load Balancing (ELB).

### Storage

  In production app architecture, **storage** refers to how data is persistently managed and accessed. Effective storage design ensures that applications can handle large amounts of data efficiently, ensuring speed, security, and scalability.

  Key Types of Storage:

  1. Relational Databases (SQL):
  - Structured, schema-based.
  - Examples: MySQL, PostgreSQL.
  - Suitable for applications needing ACID transactions, complex querying, and data integrity.
  2. NoSQL Databases:
  - Flexible schemas, designed for scalability.
  - Examples: MongoDB, Cassandra.
  - Ideal for unstructured or semi-structured data like JSON, logs, or large-scale distributed applications.
  3. Blob/Object Storage:
  - Optimized for storing large amounts of unstructured data.
  - Examples: AWS S3, Google Cloud Storage.
  - Used for media files, backups, and big data storage.
  4. In-memory Storage:
  - Stores data in RAM for fast access.
  - Examples: Redis, Memcached.
  - Best for caching, session storage, or real-time data.
  5. Distributed Storage:
  - Scales across multiple servers or regions.
  - Examples: HDFS, Ceph.
  - Handles large datasets in data-intensive applications (e.g., analytics).

  Key Considerations:

  - Data Consistency: Ensuring that data remains accurate and reliable across the system.
  - Scalability: Ability to grow as the application and data increase.
  - Backup & Recovery: Mechanisms to prevent data loss in case of failure.
  - Latency: Minimizing response times for data retrieval.
  - Security: Implementing encryption, access control, and compliance with data privacy standards.

  In production, combining these storage types based on use cases ensures a robust and scalable architecture.

### Logging & Monitoring

  1. Logging:
  - Purpose: Captures detailed information about application events (errors, requests, database queries, etc.) to aid in troubleshooting, debugging, and tracking system behavior.
  - Components:
    - Log Collection: Logs are gathered from different parts of the app (frontend, backend, microservices) using libraries like `log4j`, `winston`, or `logrus`.
    - Log Storage: Logs are centralized in tools like ELK Stack (Elasticsearch, Logstash, Kibana), Fluentd, or Cloud-based solutions (AWS CloudWatch, GCP Stackdriver).
    - Log Rotation: To manage large log sizes, logs are rotated, compressed, or archived regularly.
  - Key Features: Time-stamped, structured logs (JSON format often preferred), with different log levels (INFO, WARN, ERROR, DEBUG).
    
  2. Monitoring:
  - Purpose: Continuously observes system performance and health metrics (CPU usage, memory, disk I/O, request latencies) to detect issues early and ensure system reliability.
  - Components:
    - Metrics Collection: Tools like Prometheus or Datadog gather system and application metrics in real-time.
    - Alerting: Alerts are triggered based on predefined thresholds (e.g., CPU usage > 80%) and sent via channels like Slack, email, or PagerDuty.
    - Visualization: Dashboards (Grafana, Cloud-based solutions) visualize the system’s performance to provide insight into app behavior.
  - Key Features: Monitors system uptime, database performance, response times, and supports anomaly detection.

  Integration: Logging and monitoring work together to provide observability in production environments, ensuring early detection of issues and quick troubleshooting.

### Staging Environment

  A **Staging Environment** in production app architecture is a replica of the production environment where final testing is conducted before code is deployed live. Its primary purpose is to simulate real-world conditions, allowing developers and testers to validate the application’s functionality, performance, and stability.

  Key characteristics include:

  - Isolation: Staging is separate from development and production environments to prevent interference with live systems.
  - Realistic Data: It uses production-like data or anonymized data to closely mimic the actual user experience.
  - Testing Ground: Enables testing for bugs, security vulnerabilities, integrations, and deployment processes.
  - Deployment Practice: New features and changes are deployed here first to ensure smooth transitions to production.

  It serves as the last checkpoint before live deployment, helping catch issues that might not appear in development.

## What is Good Design?

### Scalability

  **Scalability** in system design refers to the system's ability to handle increasing loads efficiently. As an app grows in users or data, its architecture needs to ensure performance remains high. There are two main types of scalability:

  1. Vertical Scalability (Scaling Up): Increasing the resources of a single server, like CPU or memory. It's simpler but has hardware limitations and can become expensive.

  2. Horizontal Scalability (Scaling Out): Adding more servers or nodes to distribute the load. It allows for greater flexibility and resilience but requires more complex coordination, like load balancing and data partitioning.

  Key Scalability Concepts:
  - Load Balancers: Distribute traffic across multiple servers, preventing any one server from becoming overloaded.
  - Microservices: Breaking applications into smaller, independent services that can be scaled individually.
  - Caching: Storing frequently accessed data in a cache (like Redis) reduces load on databases.
  - Sharding: Splitting databases across multiple servers to handle large datasets.
  - Auto-scaling: Automatically adding/removing servers based on traffic demand.

  Challenges:

  - State Management: Handling state across multiple servers requires mechanisms like distributed caches or stateless architectures.
  - Data Consistency: Ensuring data remains consistent when distributed across multiple databases or services.

  Scalability ensures that the system grows smoothly with demand while maintaining performance and cost efficiency.

### Maintainability

  **Maintainability** in system design refers to how easily a system can be modified, updated, or extended over time. A maintainable system ensures that developers can fix bugs, add new features, and improve performance with minimal disruption or risk to the existing system.

  Key Concepts for Maintainability:

  1. Modularity: Breaking the system into small, independent components or services (e.g., microservices). Each module can be maintained or updated without affecting the entire system.
  2. Separation of Concerns: Each component or service should focus on a single responsibility. This reduces complexity and makes the system easier to understand and modify.
  3. Readability & Documentation: Code should be well-organized, consistently structured, and documented. This helps new developers quickly understand the system and make changes without introducing bugs.
  4. Testability: A maintainable system is easy to test. Automated unit, integration, and end-to-end tests help catch issues early and ensure that changes do not break existing functionality.
  6. Version Control & Continuous Integration (CI): Using version control (e.g., Git) and CI pipelines allows teams to track changes, review code, and deploy updates safely.
  7. Decoupling: Reducing dependencies between components makes the system easier to update or replace individual parts without affecting others.

  Challenges:

  - Technical Debt: Accumulating quick fixes or poor design choices can hinder long-term maintainability.
  - Backward Compatibility: Ensuring new updates do not break older parts of the system is crucial in maintaining a stable, evolving system.

  Maintainability ensures that the system can evolve efficiently and reliably, allowing for easier updates and longer system lifespan.

### Efficiency

  **Efficiency** in system design refers to the optimization of resources—such as CPU, memory, storage, and network bandwidth—while maintaining performance, scalability, and reliability. A well-designed system should use minimal resources to achieve the required throughput and low-latency responses.

  Here are key aspects of efficiency in system design:

  1. Time Complexity: Efficient systems process tasks quickly, minimizing the time complexity of operations (e.g., using O(log n) or O(n) algorithms over O(n^2)).
  2. Space Complexity: Optimal memory usage helps reduce storage costs and ensures that the system can scale without running out of memory.
  3. Caching: Storing frequently accessed data in cache reduces the need to repeatedly fetch data from slower storage layers (e.g., databases), improving response times.
  4. Load Balancing: Efficient load distribution across servers ensures that no single server is overwhelmed, optimizing performance under high traffic.
  5. Asynchronous Processing: Offloading non-critical tasks to background jobs reduces the load on the system's core components, allowing faster user-facing operations.
  6. Concurrency: Designing systems to handle multiple tasks simultaneously (e.g., using multi-threading or event-driven models) increases throughput.
  7. Data Sharding and Partitioning: Splitting large datasets across multiple databases or servers allows for parallel processing, reducing query times.
  8. Network Efficiency: Minimizing the size of data transfers, compressing data, and reducing the number of round trips between client and server improves latency.

  Efficiency is a balance between resource utilization and system performance, key to creating scalable, reliable systems.

### Reliability

  **Reliability** in System Design refers to the ability of a system to function correctly and consistently over time, even in the presence of failures or unexpected conditions. Key aspects of designing for reliability include:

  1. Redundancy: Duplication of critical components (like servers, databases, and services) to prevent single points of failure. This can involve active-active or active-passive setups.
  2. Fault Tolerance: The system’s ability to continue functioning in case of component failures. This is achieved through mechanisms like load balancing, failover, and replication.
  3. Data Consistency: Ensuring data remains accurate and consistent across distributed systems, often using replication techniques, consensus protocols (e.g., Paxos, Raft), and eventual consistency models in some cases.
  4. Monitoring and Alerts: Continuous tracking of system health, resource usage, and performance to detect issues early and alert operators before they affect users.
  5. Graceful Degradation: When parts of the system fail, the system should degrade in a controlled way, providing limited functionality instead of failing completely.
  6. Backups and Disaster Recovery: Regular data backups and clear disaster recovery plans ensure that the system can recover from catastrophic failures or data loss.

  By addressing these areas, a reliable system can maintain high availability, minimize downtime, and ensure consistent user experiences despite unforeseen issues.

## Data Management

### Moving Data

  In system design, **moving data** refers to the process of transferring information between different components, services, or databases in a distributed system. Here's a concise overview:

  1. Data Flow: Data can flow between client and server, across microservices, or between databases. Common protocols include HTTP/HTTPS (for APIs), gRPC, and WebSockets for real-time communication.
  2. Data Formats: Typically, data is serialized for transfer, using formats like JSON, XML, or Protocol Buffers. The choice depends on factors like readability, performance, and compatibility.
  3. Data Storage and Replication: Moving data from one database to another may involve replication. This can be:
    - Synchronous: Data is written to all replicas at once, ensuring consistency but increasing latency.
    - Asynchronous: Data is written to the primary database first and propagated to replicas later, improving performance at the cost of eventual consistency.
  4. Data Streaming: Systems like Apache Kafka, RabbitMQ, or AWS Kinesis enable real-time data movement in event-driven architectures, allowing continuous flow and processing of data streams.
  5. Batch Processing: For large datasets, batch processing tools (e.g., Apache Hadoop, AWS Batch) are used to move and process data at scheduled intervals, ideal for bulk data transfers.
  6. Data Transformation: When moving data, you often need to convert it to a format usable by the receiving system (ETL – Extract, Transform, Load).
  7. Load Balancing: Data movement across services can be optimized using load balancers to distribute requests and manage data flow effectively.
  8. Latency and Bandwidth: It's crucial to optimize data movement for low latency and efficient bandwidth usage, especially in high-traffic systems.

  This is central to maintaining performance, reliability, and scalability in a distributed system.

### Storing Data

  In system design, storing data involves choosing where and how to persist data to meet system requirements like scalability, consistency, and fault tolerance. Here’s a short overview:

  1. Database Types:
  - Relational Databases (SQL): Store structured data in tables with predefined schemas. They support strong ACID properties (Atomicity, Consistency, Isolation, Durability). E.g., MySQL, PostgreSQL.
  - NoSQL Databases: Handle unstructured, flexible data, ideal for high-volume, distributed systems. They trade ACID for scalability. Types include:
    - Key-Value Stores: E.g., Redis, DynamoDB.
    - Document Stores: E.g., MongoDB, Couchbase.
    - Columnar Stores: E.g., Cassandra, HBase.
    - Graph Databases: E.g., Neo4j.
  2. Consistency Models:
  - Strong Consistency: Ensures that all users see the same data simultaneously. Good for systems needing accuracy.
  - Eventual Consistency: In distributed systems, replicas may temporarily diverge but converge over time. It favors availability over immediate consistency.
  3. Scaling:
  - Vertical Scaling: Adding more resources (CPU, RAM) to a single server.
  - Horizontal Scaling: Distributing data across multiple servers or shards to handle larger volumes. Often used with NoSQL.
  4. Caching:
  - In-memory Caches (like Redis or Memcached) store frequently accessed data to reduce load on databases and improve performance.
  5. Data Replication:
  - Master-Slave Replication: One primary server (master) handles writes; replicas (slaves) sync data for read scaling.
  - Multi-Master Replication: Multiple nodes can handle writes, useful for high-availability systems.
  6. Backup & Recovery:
  - Regular backups are essential for preventing data loss, and recovery strategies must be in place to handle failures.

  This high-level summary highlights essential concepts for designing a robust and scalable data storage system.

### Transforming Data

  In system design, **transforming data** refers to the process of converting data from one format, structure, or schema to another to facilitate processing, storage, or retrieval in distributed systems.

  Key Concepts:

  1. Normalization & Denormalization:
  - Normalization: Breaking data into smaller, logically organized tables to reduce redundancy and improve consistency.
  - Denormalization: Combining tables to optimize read performance, common in NoSQL databases for fast querying.
  2. ETL (Extract, Transform, Load):
  - Extract: Retrieving raw data from various sources.
  - Transform: Converting data into the required format, applying business logic or rules (e.g., aggregation, filtering).
  - Load: Storing the transformed data in a target system (like a database or data warehouse).
  3. Data Aggregation:
  - Combining multiple data records into a summarized format (e.g., counting, averaging) to improve performance for analytics.
  4. Encoding/Decoding:
  - Data may be transformed into compressed or encrypted formats for transmission or storage, requiring decoding upon retrieval.
  5. Serialization/Deserialization:
  - Serialization: Converting data into a format suitable for storage or transfer (e.g., JSON, XML).
  - Deserialization: Reversing this process to retrieve the original data structure.
  6. Schema Evolution:
  - Handling changes in the structure of data (schemas) over time, ensuring backward compatibility in distributed systems.

  Efficient data transformation improves scalability and performance in system design by optimizing how systems handle, store, and retrieve data across different components.

### CAP Theorem

  The **CAP Theorem** in system design, proposed by Eric Brewer, states that a distributed system can only guarantee two out of three properties simultaneously:

  1. Consistency (C): Every read receives the most recent write, ensuring all nodes in the system reflect the same data at the same time.
  2. Availability (A): Every request (read or write) receives a response, even if some nodes are down, ensuring the system is operational.
  3. Partition Tolerance (P): The system continues to function even if there is a network partition (a communication breakdown between nodes).

  Key Insight:

  In the presence of a network partition (which is inevitable in distributed systems), designers must choose between:
  - Consistency: Ensuring all nodes have the same data (but some requests might fail).
  - Availability: Keeping the system operational (but allowing some nodes to have outdated data).

  Examples:
  - CP Systems: Prioritize Consistency and Partition Tolerance (e.g., HBase).
  - AP Systems: Prioritize Availability and Partition Tolerance (e.g., Cassandra).
  - CA Systems: Only achievable when there are no network partitions, typically in non-distributed systems.

  The CAP theorem guides trade-offs in designing distributed systems based on the system’s requirements for consistency, availability, and tolerance to network failures.


