# Functions in Python

## What is a Function?
- A reusable block of code that performs a specific task.
- Helps organize code into logical, modular units for readability and reusability.

## Defining a Function
- Use the `def` keyword, function name, parentheses (with optional parameters), and a colon.
- Example:
  ```python
  def greet():
      print("Hello, World!")
  ```

## Calling a Function
- Execute by using its name followed by parentheses.
  ```python
  greet()
  ```

## Function Parameters
- Functions can accept parameters to customize behavior.
  ```python
  def greet(name):
      print("Hello, " + name + "!")
  greet("Alice")
  ```

## Return Statement
- Use `return` to send a value back from a function.
  ```python
  def add_numbers(a, b):
      return a + b
  result = add_numbers(3, 4)  # result is 7
  ```

## Why Use Functions?
- Encapsulate reusable code.
- Improve structure, efficiency, and maintainability.
- Can take inputs, perform computations, and produce outputs.

## Example Functions
```python
def who_am_i(name, age):
    print(f"My name is {name} and I am {age} years old")
who_am_i("Heath", 35)

def add_one_hundred(num):
    print(num + 100)
add_one_hundred(100)

def add(x, y):
    print(x + y)
add(7, 7)

def multiply(x, y):
    return x * y
result1 = multiply(7, 7)
result2 = multiply(8, 8)
print(result1 + result2)

def square_root(x):
    print(x ** 0.5)
square_root(64)

def nl():  # new line
    print('\\n')
nl()
