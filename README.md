# System-Design-Notes
  This repository contains notes and example code based on what I learned from the FreeCodeCamp [System Design Course](https://www.youtube.com/watch?v=F2FmTdLtb_4). It covers essential system design concepts, architectural patterns, scalability techniques, and practical design examples.

## Table of Contents
  1. [Computer Architecture](#computer-architecture)
  - [Bits and Bytes](#bits-and-bytes)

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

