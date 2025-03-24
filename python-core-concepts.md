# Python Concepts

## Python Basics
- Interpreted, dynamically typed, and garbage-collected language.
- Uses indentation for block definition instead of `{}`.
- File extension: `.py`.

```markdown
## 1. Variables & Data Types
- **Variables**: Store data (no explicit declaration).
  ```python
  name = "Alice"
  age = 30
  ```
- **Basic Types**:
  - `int`: `42`
  - `float`: `3.14`
  - `str`: `"Hello"`
  - `bool`: `True/False`
  - `NoneType`: `None`

## 2. Operators
- **Arithmetic**: `+`, `-`, `*`, `/`, `//` (floor), `**` (power)
- **Comparison**: `==`, `!=`, `>`, `<`, `>=`, `<=`
- **Logical**: `and`, `or`, `not`

## 3. Control Flow
- **Conditionals**:
  ```python
  if x > 0:
      print("Positive")
  elif x == 0:
      print("Zero")
  else:
      print("Negative")
  ```
- **Loops**:
  - `for`: Iterate over sequences.
    ```python
    for i in range(5):  # 0 to 4
        print(i)
    ```
  - `while`: Repeat while condition is true.
    ```python
    while count < 5:
        print(count)
        count += 1
    ```

## 4. Functions
- **Define & Call**:
  ```python
  def greet(name):
      return f"Hello, {name}!"
  print(greet("Bob"))  # Output: Hello, Bob!
  ```
- **Parameters**:
  - Defaults: `def func(a, b=10):`
  - Keyword args: `func(b=5, a=2)`

## 5. Data Structures
- **Lists**: Mutable sequences.
  ```python
  fruits = ["apple", "banana"]
  fruits.append("cherry")
  ```
- **Tuples**: Immutable sequences.
  ```python
  point = (3, 4)
  ```
- **Dictionaries**: Key-value pairs.
  ```python
  person = {"name": "Alice", "age": 30}
  ```
- **Sets**: Unique elements.
  ```python
  unique_nums = {1, 2, 3}
  ```
- **List Comprehensions**:
  ```python
  squares = [x**2 for x in range(10)]
  ```

## 6. File Handling
- **Read/Write Files**:
  ```python
  with open("file.txt", "r") as f:
      content = f.read()
  with open("new.txt", "w") as f:
      f.write("Hello World")
  ```

## 7. Error Handling
- **Try-Except Blocks**:
  ```python
  try:
      result = 10 / 0
  except ZeroDivisionError:
      print("Cannot divide by zero!")
  ```

## 8. Modules & Packages
- **Import Modules**:
  ```python
  import math
  print(math.sqrt(16))  # 4.0
  ```
- **Create a Module**: Save code in `mymodule.py` and import with `import mymodule`.

## 9. Object-Oriented Programming (OOP)
- **Classes & Objects**:
  ```python
  class Dog:
      def __init__(self, name):
          self.name = name
      def bark(self):
          print("Woof!")
  my_dog = Dog("Buddy")
  my_dog.bark()
  ```
- **Inheritance**:
  ```python
  class Labrador(Dog):
      def __init__(self, name, color):
          super().__init__(name)
          self.color = color
  ```

## 10. Built-in Functions & Libraries
- **Key Functions**:
  - `len()`, `type()`, `input()`, `print()`
- **Common Libraries**:
  - `math`: Math operations
  - `datetime`: Date/time handling
  - `os`: OS interactions

## 11. Virtual Environments
- **Create & Activate**:
  ```bash
  python -m venv myenv
  source myenv/bin/activate  # Linux/macOS
  myenv\Scripts\activate.bat  # Windows
  ```

## 12. PIP (Package Installer)
- **Install Packages**:
  ```bash
  pip install requests numpy pandas
  ```

## 13. Code Style (PEP 8)
- **Guidelines**:
  - Indent with 4 spaces.
  - Use snake_case for variables/functions.
  - Capitalize ClassNames.

---
