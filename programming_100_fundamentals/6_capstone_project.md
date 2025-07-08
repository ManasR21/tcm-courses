# Capstone Project: Python Port Scanner (Explained)

```python
import sys
import socket
from datetime import datetime
import threading
```
**Explanation:**  
- `sys` lets you handle command-line arguments and exit the program.
- `socket` is used for network communication.
- `datetime` helps print the current date and time.
- `threading` allows the program to scan many ports at once, making it much faster.

---

## Function to Scan a Single Port

```python
def scan_port(target, port):
    try:
        s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
        s.settimeout(1)
        result = s.connect_ex((target, port)) # error indicator - if 0, port is open
        if result == 0:
            print(f"Port {port} is open")
        s.close()
    except socket.error as e:
        print(f"Socket error on port {port}: {e}")
    except Exception as e:
        print(f"Unexpected error on port {port}: {e}")
```
**Explanation:**  
- This function tries to connect to a specific port on the target computer.
- If the connection is successful (`result == 0`), it prints that the port is open.
- If there’s an error, it prints an error message.
- The socket is always closed after checking.

---

## Main Function: Handles User Input and Starts the Scan

```python
def main():
    if len(sys.argv) == 2:
        target = sys.argv[1]
    else:
        print("Invalid number of arguments.")
        print("Usage: python.exe scanner.py <target>")
        sys.exit(1)
```
**Explanation:**  
- Checks if the user provided a target (like an IP address or website) as a command-line argument.
- If not, it prints how to use the program and exits.

---

### Resolving the Target and Printing a Banner

```python
    try:
        target_ip = socket.gethostbyname(target)
    except socket.gaierror:
        print(f"Error: Unable to resolve hostname {target}")
        sys.exit(1)

    print("-" * 50)
    print(f"Scanning target {target_ip}")
    print(f"Time started: {datetime.now()}")
    print("-" * 50)
```
**Explanation:**  
- Converts the target name (like "example.com") to an IP address.
- Prints a banner showing what is being scanned and when the scan started.

---

### Scanning All Ports with Threads

```python
    try:
        threads = []
        for port in range(1, 65536):
            thread = threading.Thread(target=scan_port, args=(target_ip, port))
            threads.append(thread)
            thread.start()

        for thread in threads:
            thread.join()
```
**Explanation:**  
- Creates a thread for each port (from 1 to 65535) to scan them all at the same time.
- Starts each thread, which runs the `scan_port` function.
- Waits for all threads to finish before moving on.

---

### Handling Interruptions and Errors

```python
    except KeyboardInterrupt:
        print("\nExiting program.")
        sys.exit(0)

    except socket.error as e:
        print(f"Socket error: {e}")
        sys.exit(1)

    print("\nScan completed!")
```
**Explanation:**  
- If you press Ctrl+C, the program exits gracefully.
- If there’s a socket error, it prints the error and exits.
- Prints a message when the scan is done.

---

## Running the Program

```python
if __name__ == "__main__":
    main()
```
**Explanation:**  
- This makes sure the `main()` function runs only if you start this file directly (not if you import it in another script).

---

## How to Use

- Run the program from the command line, providing a target:
  ```
  python scanner.py example.com
  ```
- Replace `example.com` with the IP address or website you want to scan.

---

**Summary:**  
This port scanner uses Python’s networking and threading features to quickly check which ports are open on a target computer. It’s a practical example of using functions, error handling, command-line arguments, and multithreading in a real-world project.
