# Data Structures in Python

## Lists
- **Definition:** Mutable, ordered collection of items (can be different types).
- **Creation:**  
  ```python
  fruits = ["apple", "banana", "orange"]
  ```
- **Access:**  
  ```python
  fruits[0]  # "apple"
  fruits[2]  # "orange"
  ```
- **Modification:**  
  ```python
  fruits[1] = "grape"
  fruits.append("kiwi")
  fruits.remove("apple")
  ```
- **Operations:**  
  - Concatenation: `combined = fruits + fruits2`
  - Length: `len(fruits)`
  - Slicing: `fruits[1:3]`
  - Iteration:  
    ```python
    for fruit in fruits:
        print(fruit)
    ```
- **Nested Lists:**  
  ```python
  grades = [["Bob", 82], ["Alice", 90]]
  grades[0][1] = 83
  ```

## Tuples
- **Definition:** Immutable, ordered collection of items.
- **Creation:**  
  ```python
  fruits = ("apple", "banana", "orange")
  ```
- **Access:**  
  ```python
  fruits[0]  # "apple"
  ```
- **Immutability:** Cannot modify elements after creation.
- **Operations:**  
  - Concatenation: `combined = fruits + fruits2`
  - Length: `len(fruits)`
  - Slicing: `fruits[1:3]`
- **Use Cases:** Grouping related data, dictionary keys.

## Dictionaries
- **Definition:** Unordered collection of key-value pairs.
- **Creation:**  
  ```python
  student = {"name": "Alice", "age": 20, "major": "CS"}
  ```
- **Access:**  
  ```python
  student["name"]  # "Alice"
  ```
- **Modification:**  
  ```python
  student["age"] = 21
  student["city"] = "London"
  ```
- **Operations:**  
  - Length: `len(student)`
  - Iteration:  
    ```python
    for key in student:
        print(key, student[key])
    ```
  - Deletion: `del student["age"]`
- **Example:**  
  ```python
  drinks = {"White Russian": 8, "Old Fashioned": 12}
  drinks["White Russian"] = 9
  print(drinks.get("White Russian"))
  ```

## Strings (as Data Structures)
- **Definition:** Immutable sequence of characters.
- **Creation:**  
  ```python
  my_string = "Hello, World!"
  ```
- **Access:**  
  ```python
  my_string[0]  # 'H'
  ```
- **Operations:**  
  - Concatenation: `'Hello' + ' World'`
  - Length: `len(my_string)`
  - Slicing: `my_string[7:12]`
  - Methods: `.upper()`, `.lower()`, `.strip()`, `.split()`, `.replace()`
  - Formatting:  
    - `%` operator: `"My name is %s" % name`
    - `.format()`: `"My name is {}".format(name)`
    - f-strings: `f"My name is {name}"`
  - Membership: `"A" in "Apple"` (case sensitive)
  - Joining/Splitting:  
    ```python
    sentence = "192.168.138.1"
    parts = sentence.split('.')
    joined = '.'.join(parts)
    ```
  - Stripping whitespace: `"   hello   ".strip()`

---
