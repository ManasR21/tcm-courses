# Basic Programming Concepts (Python)

## Strings
- **Definition:** Sequence of characters in single or double quotes. Immutable.
- **Creation:** `my_string = 'Hello'` or `my_string = "Hello"`
- **Indexing:** `my_string[0]` → first character.
- **Concatenation:** `'Hello' + ' World'` → `'Hello World'`
- **Length:** `len(my_string)`
- **Slicing:** `my_string[7:12]` → substring.
- **Methods:** `.upper()`, `.lower()`, `.strip()`, `.split()`, `.replace()`, etc.
- **Formatting:**  
  - `%` operator: `"My name is %s" % name`
  - `.format()`: `"My name is {}".format(name)`
  - f-strings: `f"My name is {name}"`

## Math Module & Operators
- **Import:** `import math`
- **Functions:**  
  - `math.sqrt(x)`, `math.pow(x, y)`, `math.exp(x)`, `math.log(x)`, `math.log10(x)`
  - Trigonometry: `math.sin(x)`, `math.cos(x)`, `math.tan(x)`
  - Conversion: `math.degrees(x)`, `math.radians(x)`
- **Operators:**  
  - Addition: `+`
  - Subtraction: `-`
  - Multiplication: `*`
  - Division: `/`
  - Integer Division: `//`
  - Modulo: `%`
  - Exponentiation: `**`

## Variables & Methods
- **Variables:** Named storage for data. Dynamically typed.
  - Example:  
    ```python
    x = 10
    name = "John"
    is_true = True
    ```
- **Usage:**  
  - Arithmetic: `y = x + 5`
  - String: `print("Hello, " + name)`
  - Boolean:  
    ```python
    if is_true:
        print("The condition is true")
    ```
- **Methods (Functions):**
  - Built-in: `len(numbers)`
  - User-defined:  
    ```python
    def greet(name):
        print("Hello, " + name)
    greet("Alice")
    ```

## String & Variable Methods
- `quote.upper()`, `quote.lower()`, `quote.title()`, `len(quote)`
- String concatenation: `"My name is "+name+" and I am "+str(age)+" years old."`
- Increment: `age += 1`

## User Input
- **Input:**  
  ```python
  name = input("Enter your name: ")
  print("Hello, " + name + "!")
  ```
- **Type Conversion:**  
  ```python
  age = int(input("Enter your age: "))
  print("You will be " + str(age + 1) + " next year.")
  ```
- **Example:**  
  ```python
  x = float(input("Give me a number: "))
  y = float(input("Give me another number: "))
  print(x + y)
  ```





