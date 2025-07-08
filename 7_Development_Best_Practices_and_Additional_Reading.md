# Development Best Practices & Additional Reading

## Pseudocode

**What is Pseudocode?**  
- Pseudocode is a way to describe algorithms using plain language and logical steps, not real code.
- It helps you plan, communicate, and understand the logic before writing actual code.

**Why Use Pseudocode?**
- Simplifies complex logic.
- Helps communicate ideas with others.
- Useful for early planning and teaching.
- Makes debugging and translating to code easier.

**Example: Linear Search in Pseudocode**
```
Procedure LinearSearch(arr, target)
    For each element in arr
        If element equals target
            Return "Found at index"
    End For
    Return "Not Found"
End Procedure
```
**Python Translation:**
```python
def linear_search(arr, target):
    for i, element in enumerate(arr):
        if element == target:
            return f"Found at index {i}"
    return "Not Found"
```

---

## High Level vs Low Level Programming

**High-Level Programming Languages:**
- Closer to human language, easier to read and write.
- Examples: Python, Java, JavaScript.
- Handle many details for you (memory management, complex operations).
- Good for rapid development and productivity.

**Low-Level Programming Languages:**
- Closer to machine language, harder for humans to read.
- Examples: Assembly, C.
- Give you more control over hardware and memory.
- Used for system programming, embedded systems, performance-critical code.

| Feature         | High-Level         | Low-Level         |
|-----------------|-------------------|-------------------|
| Readability     | Easy              | Hard              |
| Abstraction     | High              | Low               |
| Control         | Less              | More              |
| Speed           | Slower (usually)  | Faster (usually)  |
| Examples        | Python, Java      | C, Assembly       |

---

## Variable Best Practices

- **Use Descriptive Names:**  
  ```python
  age = 25         # Good
  a = 25           # Bad
  ```
- **Follow Naming Conventions:**  
  - Use lowercase_with_underscores for variables in Python.
- **Avoid Magic Numbers:**  
  - Use named constants instead of unexplained numbers.
  ```python
  MAX_USERS = 100
  ```
- **Initialize Variables:**  
  - Always assign a value before using a variable.
- **Keep Scope Small:**  
  - Define variables in the smallest scope needed (inside functions if possible).

---

## Statically Typed Variables

**Statically Typed Languages:**
- You must declare the type of a variable when you create it.
- The type cannot change later.
- Example (in Java):
  ```java
  int age = 25;
  age = "twenty-five"; // Error!
  ```
- **Benefits:**  
  - Catches type errors before running the program.
  - Can improve performance and reliability.

**Dynamically Typed Languages (like Python):**
- You do not declare types; variables can change type.
  ```python
  age = 25
  age = "twenty-five"  # Allowed
  ```

---

## Debugging Basics

- **What is Debugging?**  
  - The process of finding and fixing errors (bugs) in your code.

- **Common Debugging Techniques:**
  - **Print Statements:**  
    Print variable values to see what your code is doing.
    ```python
    print("x =", x)
    ```
  - **Use a Debugger:**  
    Step through code line by line, inspect variables, set breakpoints.
    - Python: Use `pdb` or an IDE’s debugger.
  - **Read Error Messages:**  
    Carefully read and understand error messages—they often tell you what’s wrong.
  - **Check Edge Cases:**  
    Test your code with unusual or extreme inputs.

---

## Setting Up a Reproducible Environment

- **Why?**  
  - Ensures your code runs the same way on any computer.
  - Makes it easier to share your project and collaborate.

- **How?**
  - **Use Virtual Environments:**  
    Isolate your project’s dependencies.
    ```bash
    python -m venv venv
    source venv/bin/activate  # On Windows: venv\Scripts\activate
    ```
  - **requirements.txt:**  
    List all packages your project needs.
    ```bash
    pip freeze > requirements.txt
    ```
    Others can install them with:
    ```bash
    pip install -r requirements.txt
    ```
  - **Document Your Setup:**  
    Write a README file with setup instructions.

---

## Writing Reusable and Testable Code

**What is Testable Code?**  
- Code that is easy to test in isolation, without relying on user input, print statements, or external systems.

**Non-Testable Example:**
```python
def atm_withdrawal():
    balance = int(input("Enter your current balance: "))
    amount = int(input("Enter the amount to withdraw: "))
    if amount > balance:
        print("Insufficient funds")
    elif amount <= 0:
        print("Invalid amount")
    else:
        balance -= amount
        print(f"Transaction successful. Your new balance is: {balance}")
```
*Problems:*
- Hard to test (relies on input/print).
- No clear inputs/outputs.

**Testable Version:**
```python
def atm_withdrawal(balance, amount):
    if amount > balance:
        return "Insufficient funds", balance
    elif amount <= 0:
        return "Invalid amount", balance
    else:
        balance -= amount
        return "Transaction successful", balance
```
*Improvements:*
- Takes clear inputs, returns clear outputs.
- No side effects (no input/print).

**How to Test:**
```python
import unittest

class TestATMWithdrawal(unittest.TestCase):
    def test_insufficient_funds(self):
        message, new_balance = atm_withdrawal(100, 150)
        self.assertEqual(message, "Insufficient funds")
        self.assertEqual(new_balance, 100)

    def test_invalid_amount(self):
        message, new_balance = atm_withdrawal(100, -20)
        self.assertEqual(message, "Invalid amount")
        self.assertEqual(new_balance, 100)

    def test_successful_transaction(self):
        message, new_balance = atm_withdrawal(100, 50)
        self.assertEqual(message, "Transaction successful")
        self.assertEqual(new_balance, 50)

if __name__ == "__main__":
    unittest.main()
```

---

## Key Principles for Writing Testable Code

- **Avoid Side Effects:** Don’t use input(), print(), or access files/databases inside your logic functions.
- **Clear Inputs and Outputs:** Functions should take parameters and return results.
- **Small, Focused Functions:** Each function should do one thing.
- **Dependency Injection:** Pass dependencies (like database connections) as parameters.
- **Write Tests in Parallel:** Write tests as you write your code.

---

## How Importing Works in Python

- You can import functions from one file (module) into another.
- Example:
  - In `test_atm.py`:  
    ```python
    from atm import atm_withdrawal
    ```
  - This lets you test the function defined in `atm.py` without rewriting it.

---

**Summary:**  
- Use pseudocode to plan and communicate logic.
- Write code that is easy to test by making it modular, focused, and free of side effects.
- Use Python’s import system and testing frameworks to organize and verify your code.
- Understand the difference between high-level and low-level programming, follow variable best practices, know about static vs dynamic typing, debug effectively, and set up reproducible environments for reliable development.




