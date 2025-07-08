# Control Structures in Python

## Boolean Expressions & Relational Operators
- **Boolean expressions:** Evaluate to `True` or `False`. Used in conditionals and logic.
- **Relational operators:**
  - `==` (equal to)
  - `!=` (not equal to)
  - `>` (greater than)
  - `<` (less than)
  - `>=` (greater than or equal to)
  - `<=` (less than or equal to)
- **Logical operators:**
  - `and` (both conditions true)
  - `or` (at least one condition true)
  - `not` (negates the condition)
- **Example:**
  ```python
  x = 5
  y = 10
  print(x == y)        # False
  print(x < y and y > 0)  # True
  print(not (x == y))  # True
  ```

## Conditional Statements
- **if statement:** Executes code if condition is true.
  ```python
  if x > 0:
      print("x is positive")
  ```
- **if-else statement:** Adds an alternative if condition is false.
  ```python
  if x > 0:
      print("x is positive")
  else:
      print("x is not positive")
  ```
- **if-elif-else statement:** Checks multiple conditions.
  ```python
  if x > 0:
      print("x is positive")
  elif x < 0:
      print("x is negative")
  else:
      print("x is zero")
  ```
- **Example functions:**
  ```python
  def drink(money):
      if money >= 2:
          return "You've got yourself a drink!"
      else:
          return "No drink for you!"
  print(drink(3))
  print(drink(1))
  ```

## Loops
- **for loop:** Iterates over a sequence (list, string, range, etc.).
  ```python
  fruits = ["apple", "banana", "orange"]
  for fruit in fruits:
      print(fruit)
  ```
- **while loop:** Repeats as long as a condition is true.
  ```python
  count = 0
  while count < 5:
      print(count)
      count += 1
  ```
- **break:** Exit the loop early.
- **continue:** Skip to the next iteration.

- **Examples:**
  ```python
  vegetables = ["cucumber", "spinach", "cabbage"]
  for veggie in vegetables:
      print(veggie)

  for i in range(5):
      print(i)

  word = "Python"
  for letter in word:
      print(letter)

  i = 1
  while i < 10:
      print(i)
      i += 1
  ```

## Simple Calculator Example
```python
x = float(input("Give me a number: "))
o = input("Give me an operator: ")
y = float(input("Give me yet another number: "))

if o == "+":
    print(x + y)
elif o == "-":
    print(x - y)
elif o == "/":
    print(x / y)
elif o == "*":
    print(x * y)
elif o == "**" or o == "^":
    print(x ** y)
else:
    print("Unknown operator.")
```
    