# Distributed Chat System with Load Balancing & Fault Tolerance

## Overview

This project implements a distributed chat system designed to simulate real-world scalable communication infrastructure. It features multiple chat servers, a custom load balancer, and fault-tolerant mechanisms to ensure reliability and availability.

The system enables seamless communication between clients while efficiently distributing load and handling server failures gracefully.

---

## Key Features

### Distributed Architecture

- Multiple chat servers operating concurrently
- Each server manages a subset of chat rooms
- Clients dynamically connect to available servers

### Load Balancing

- Custom round-robin load balancer
- Even distribution of client connections
- Prevents server overload and improves scalability

### Fault Tolerance

- Heartbeat-based failure detection using gossip protocol
- Automatic failure recovery and reconnection
- Maintains system consistency during server crashes

### Leader Election & Coordination

- Leader election during initialization
- Leader maintains global state consistency
- Non-leader servers request approval for critical operations

### Concurrency Handling

- Multi-threaded server design
- Handles multiple clients simultaneously
- Efficient message broadcasting within chat rooms

---

## System Architecture

The system consists of three main components:

### 1. Chat Clients

- Connect to one server at a time
- Create, delete, join, and leave chat rooms
- Send and receive messages
- View available rooms and active users

### 2. Chat Servers

- Accept multiple TCP client connections
- Manage locally created chat rooms
- Handle client redirection across servers
- Synchronize system state

### 3. Load Balancer

- Distributes client requests across servers
- Uses round-robin scheduling
- Ensures balanced resource utilization

---

## Technologies Used

- Java (JDK 1.8)
- TCP Sockets
- Multithreading
- Maven (3.6.3)

Concepts:

- Distributed Systems
- Gossip Protocol
- Leader Election
- Consensus Mechanisms

---

## Build & Run Instructions

### Prerequisites

- Java 1.8
- Maven 3.6.3

### Build Commands

To build the project from source, navigate to the project root and run:

```bash
mvn clean install
mvn clean compile assembly:single
```

This will generate an executable fat JAR in the `target/` directory containing all dependencies.

### Running the System

You can run the system using the pre-compiled JAR files in the `executables/` directory or the JAR you just built.

**To run the Server (which acts as part of the distributed system):**

```bash
java -jar executables/server.jar
```

_Alternatively, from your Maven build:_

```bash
java -cp target/Distributed-Chat-System-1.0-SNAPSHOT-jar-with-dependencies.jar server.Main
```

**To run the Client:**

```bash
java -jar executables/client.jar
```

_(Open multiple terminal windows running the client to simulate multiple chat users talking to each other across the distributed system)._
