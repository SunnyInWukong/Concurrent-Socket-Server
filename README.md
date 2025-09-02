# Concurrent Socket Server

## Overview
This project implements a **multi-threaded concurrent client-server system in Java**.  
The server listens on a port, accepts client requests, and spawns a **new thread for each request**, allowing multiple clients to be served simultaneously.  

This design highlights the performance improvements and scalability benefits of concurrency compared to the [Iterative Socket Server](https://github.com/SunniyInWukong/Iterative_Socket_Server).

---

## Features

### Server
- Listens on a specified port for incoming requests  
- Creates a **new thread per client request** (concurrent design)  
- Supports the following system queries:
  1. Current date and time  
  2. Uptime (time since last boot)  
  3. Current memory usage  
  4. Active network connections  
  5. Users currently logged in  
  6. Processes currently running  

### Client
- Sends a request to the server specifying which operation to perform  
- Receives and displays the server’s response  
- Can run multiple simultaneous requests, benefiting from concurrency  

---

## How It Works
- **Concurrent design:**  
  Each client request is processed on its own thread, allowing many clients to be served in parallel.  
- **Client-server communication:**  
  Implemented with Java sockets (`ServerSocket`, `Socket`).  
- **System commands:**  
  Server executes terminal commands (`netstat`, `who`, `ps -e`) via a helper method (`runCommand`) to collect live system info.  

---

## Testing & Analysis
The server was tested under increasing client loads, comparing performance with the Iterative Socket Server.  
Collected metrics:  
- **Total turnaround time** across different numbers of requests  
- **Average response time** per request  
- **Observed scalability improvements** due to concurrency  

Results showed that the concurrent model maintains faster average turnaround times as client load increases, while the iterative model slows significantly under heavy load.

---

## Lessons Learned
- Benefits and trade-offs of **multi-threaded server design**  
- Using Java’s **threading model** (`new Thread(() -> { ... }).start()`)  
- Measuring performance under varying loads  
- Handling simultaneous socket connections and shared resources  

