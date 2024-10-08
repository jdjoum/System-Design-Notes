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


