# Other Items in Python (Fundamental Concepts)

## Importing Modules

### What is a Module?
- A module is a file containing Python code (functions, variables, classes) that you can use in your own programs.
- Python comes with many built-in modules (like math, sys, socket), and you can also create your own.

### Why Import Modules?
- To avoid rewriting code that already exists.
- To organize your code into smaller, manageable pieces.
- To use powerful features provided by Python or others.

### How to Import Modules

- **Import the whole module:**  
  You get access to everything in the module, but you must use the module name each time.
  ```python
  import math
  print(math.sqrt(25))  # Use math. before sqrt
  ```

- **Import just what you need:**  
  You can import only specific functions or variables.
  ```python
  from math import sqrt
  print(sqrt(25))  # No need for math. prefix
  ```

- **Give a module a nickname (alias):**  
  Useful if the module name is long or you want to avoid conflicts.
  ```python
  import math as m
  print(m.sqrt(25))
  ```

- **Import everything (not recommended):**  
  This puts all functions/variables from the module into your program, which can cause confusion.
  ```python
  from math import *
  print(sqrt(25))
  ```

- **Other examples:**
  ```python
  import sys  # System-specific functions
  from datetime import datetime as dt  # Date and time, with alias
  print(sys.version)
  print(dt.now())
  ```

---

## Sockets (Networking Basics)

### What is a Socket?
- A socket is like a phone jack for your program: it lets your program talk to other computers over a network.
- Sockets are used for things like web browsing, chatting, and online games.

### Why Use Sockets?
- To send and receive data between computers.
- To build networked applications (like servers and clients).

### How to Use Sockets in Python

- **Import the socket module:**
  ```python
  import socket
  ```

- **Create a socket:**
  - For most uses, you’ll want an “IPv4” address and “TCP” connection:
    ```python
    s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
    ```

- **Common Socket Actions:**
  - **Connect to another computer:**  
    (Client side)
    ```python
    s.connect(('hostname', port_number))
    ```
  - **Bind to an address/port:**  
    (Server side)
    ```python
    s.bind(('hostname', port_number))
    ```
  - **Listen for connections:**  
    (Server side, TCP only)
    ```python
    s.listen(5)  # 5 = max number of waiting connections
    ```
  - **Accept a connection:**  
    (Server side)
    ```python
    client_socket, client_address = s.accept()
    ```
  - **Send and receive data:**
    ```python
    s.send(b"Hello")  # Send bytes
    data = s.recv(1024)  # Receive up to 1024 bytes
    ```

### Example: Simple TCP Server
```python
import socket
server_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
server_socket.bind(('localhost', 1234))
server_socket.listen(5)
while True:
    client_socket, client_address = server_socket.accept()
    data = client_socket.recv(1024)
    client_socket.send(b"Received: " + data)
    client_socket.close()
```

### Example: Simple TCP Client
```python
import socket
s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
s.connect(('127.0.0.1', 7777))
```

---

**In summary:**  
- Importing modules lets you use code written by others (or yourself) to make your programs more powerful and organized.
- Sockets let your programs communicate with other computers, which is the foundation of all networked applications.







