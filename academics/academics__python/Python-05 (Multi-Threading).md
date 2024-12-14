# **Multithreading, Networks, and Client/Server Programming**

---

### **Multithreading**

Multithreading is a concurrent execution model in which a program is divided into multiple threads that run independently yet share the same memory space. It allows for efficient utilization of system resources, especially in tasks like I/O-bound and computationally intensive operations.

---

### **Threads and Processes**

- **Processes**: A process is an independent program in execution with its own memory space. Multiple processes run in isolation from one another.
    - **Example**: Running multiple Python scripts at the same time.
- **Threads**: A thread is a lightweight, smaller unit of a process that shares the process's memory and resources.
    - **Example**: A web browser where one thread manages user interactions, another fetches data, and another renders graphics.

#### **Key Differences**:

| Feature       | Process                           | Thread                              |
| ------------- | --------------------------------- | ----------------------------------- |
| Memory Space  | Separate for each process         | Shared among threads of the process |
| Communication | Inter-process communication (IPC) | Easier as threads share memory      |
| Overhead      | High overhead (more resources)    | Low overhead                        |

---

### **Threads in Python**

Python provides a built-in `threading` module to create and manage threads.

#### **Creating Threads**:

```python
import threading

def print_numbers():
    for i in range(5):
        print(f"Number: {i}")

# Creating a thread
thread = threading.Thread(target=print_numbers)
thread.start()  # Start the thread
thread.join()  # Wait for the thread to finish
```

- **`target`**: The function to be executed in the thread.
- **`start()`**: Begins the thread's execution.
- **`join()`**: Ensures the main program waits for the thread to finish.

---

### **Sleeping Threads**

The `time.sleep()` function is used to pause a thread's execution for a specified duration.

#### **Example**:

```python
import threading
import time

def print_with_delay():
    for i in range(5):
        print(f"Task {i}")
        time.sleep(1)  # Pause for 1 second

thread = threading.Thread(target=print_with_delay)
thread.start()
```

In this example, the thread pauses for 1 second between each task.

---

### **Producer, Consumer, and Synchronization**

In multithreading, **producers** and **consumers** are a common pattern where:

- **Producers**: Generate data or resources.
- **Consumers**: Use or process the generated data.

#### **The Problem**:

Producers and consumers need to work together efficiently without overwriting or losing data. Synchronization ensures safe sharing of resources between threads.

---

### **Synchronization**

Synchronization is achieved using **locks**, which prevent multiple threads from accessing a shared resource simultaneously.

#### **Using Locks**:

```python
import threading

buffer = []
lock = threading.Lock()

def producer():
    with lock:  # Acquire the lock
        buffer.append("Item")
        print("Produced an item")

def consumer():
    with lock:  # Acquire the lock
        if buffer:
            buffer.pop()
            print("Consumed an item")

thread1 = threading.Thread(target=producer)
thread2 = threading.Thread(target=consumer)

thread1.start()
thread2.start()
thread1.join()
thread2.join()
```

---

#### **Producer-Consumer Problem (With Queue)**:

Using a `queue.Queue` simplifies the producer-consumer implementation.

```python
import threading
import queue
import time

buffer = queue.Queue(maxsize=5)

def producer():
    while True:
        buffer.put("Item")
        print("Produced an item")
        time.sleep(1)

def consumer():
    while True:
        item = buffer.get()
        print("Consumed an item")
        time.sleep(2)

producer_thread = threading.Thread(target=producer)
consumer_thread = threading.Thread(target=consumer)

producer_thread.start()
consumer_thread.start()
```

In this example:

- The producer adds items to the queue.
- The consumer removes items from the queue.
- The queue ensures thread-safe access.

---

### **Key Concepts in Multithreading**

1. **Concurrency**: The ability to run multiple tasks seemingly at the same time.
2. **Parallelism**: True simultaneous execution on multi-core processors.
3. **Race Conditions**: Occur when threads access shared resources without synchronization, leading to unpredictable results.
4. **Deadlock**: A situation where two or more threads are blocked forever, waiting for each other to release resources.
# **Networks and Client/Server Programming**

---

## **Networks**

A computer network is a group of interconnected devices that communicate and share resources. Networks form the backbone of modern computing, enabling applications like web browsing, email, and file sharing.

### **Basic Definitions**

1. **Clients and Servers**:
    
    - **Client**: A device or program that requests services or resources.
        - Example: A web browser.
    - **Server**: A device or program that provides services or resources in response to client requests.
        - Example: A web server hosting a website.
2. **IP Addresses**:
    
    - An **IP address** is a unique identifier assigned to a device on a network.
    - **IPv4**: 32-bit address (e.g., `192.168.1.1`).
    - **IPv6**: 128-bit address for larger address space (e.g., `2001:0db8:85a3:0000:0000:8a2e:0370:7334`).
3. **Ports**:
    
    - A **port** is a logical communication endpoint associated with an IP address.
    - Each port is identified by a number (0–65535).
    - Common port numbers:
        - **80**: HTTP
        - **443**: HTTPS
        - **22**: SSH
        - **25**: SMTP
4. **Sockets**:
    
    - A **socket** is an endpoint for communication between two machines.
    - It combines an IP address and a port number.
    - Python provides the `socket` module for working with sockets.

---

## **Client/Server Programming**

Client/Server programming involves creating software where one program (client) requests services from another program (server).

---

### **Day/Time Client Script**

This script connects to a server and retrieves the current date and time.

#### **Client Script**:

```python
import socket

def day_time_client():
    host = "127.0.0.1"  # Localhost
    port = 12345        # Port number of the server

    # Create a socket object
    client_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

    try:
        # Connect to the server
        client_socket.connect((host, port))
        print("Connected to the server.")

        # Receive the date and time from the server
        data = client_socket.recv(1024).decode()
        print("Server response:", data)

    except ConnectionError:
        print("Error: Unable to connect to the server.")
    
    finally:
        # Close the socket
        client_socket.close()

# Run the client script
day_time_client()
```

---

### **Day/Time Server Script**

This script listens for client connections and sends the current date and time to connected clients.

#### **Server Script**:

```python
import socket
from datetime import datetime

def day_time_server():
    host = "127.0.0.1"  # Localhost
    port = 12345        # Port number

    # Create a socket object
    server_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

    try:
        # Bind the socket to the host and port
        server_socket.bind((host, port))
        print("Server started. Waiting for clients...")

        # Listen for incoming connections
        server_socket.listen(5)

        while True:
            # Accept a client connection
            client_socket, address = server_socket.accept()
            print(f"Connected to {address}")

            # Send the current date and time to the client
            current_time = datetime.now().strftime("%Y-%m-%d %H:%M:%S")
            client_socket.send(current_time.encode())

            # Close the client socket
            client_socket.close()

    except KeyboardInterrupt:
        print("\nServer shutting down.")

    finally:
        # Close the server socket
        server_socket.close()

# Run the server script
day_time_server()
```

---

### **Two-Way Chat Script**

A simple chat application that allows two-way communication between a client and server.

#### **Server Script**:

```python
import socket

def chat_server():
    host = "127.0.0.1"
    port = 12345

    server_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
    server_socket.bind((host, port))
    server_socket.listen(1)

    print("Chat server started. Waiting for client...")
    conn, addr = server_socket.accept()
    print(f"Client connected: {addr}")

    while True:
        # Receive message from client
        message = conn.recv(1024).decode()
        if message.lower() == "bye":
            print("Client disconnected.")
            break
        print(f"Client: {message}")

        # Send reply to client
        reply = input("You: ")
        conn.send(reply.encode())
        if reply.lower() == "bye":
            print("Ending chat.")
            break

    conn.close()
    server_socket.close()

chat_server()
```

#### **Client Script**:

```python
import socket

def chat_client():
    host = "127.0.0.1"
    port = 12345

    client_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
    client_socket.connect((host, port))
    print("Connected to server. Type 'bye' to exit.")

    while True:
        # Send message to server
        message = input("You: ")
        client_socket.send(message.encode())
        if message.lower() == "bye":
            print("Ending chat.")
            break

        # Receive reply from server
        reply = client_socket.recv(1024).decode()
        if reply.lower() == "bye":
            print("Server ended chat.")
            break
        print(f"Server: {reply}")

    client_socket.close()

chat_client()
```

---

### **Key Points for Client/Server Programming**

1. **IP Address**: Identifies the device on the network.
2. **Port Number**: Identifies the application on the device.
3. **Socket**: The communication endpoint combining IP and port.
4. **Server Workflow**:
    - Bind the socket to an address.
    - Listen for incoming connections.
    - Accept connections and handle requests.
5. **Client Workflow**:
    - Connect to the server.
    - Send and receive data.

