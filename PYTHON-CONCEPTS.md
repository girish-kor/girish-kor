# Python Concepts (Essential 20%)

## 1. Python Basics
- Interpreted, dynamically typed, and garbage-collected language.
- Uses indentation for block definition instead of `{}`.
- File extension: `.py`.

## 2. Variables & Data Types
```python
x = 10          # Integer
y = 3.14        # Float
name = "Python" # String
is_active = True # Boolean
data = None     # NoneType
```

## 3. Control Flow (If-Else, Loops)
```python
# Conditional statements
if x > 5:
    print("Large")
elif x == 5:
    print("Equal")
else:
    print("Small")

# Loops
for i in range(5):  # 0 to 4
    print(i)

while x > 0:
    x -= 1
```

## 4. Functions
```python
def greet(name):
    return f"Hello, {name}!"

print(greet("Alice"))
```

## 5. Lists & Tuples
```python
# List (mutable)
numbers = [1, 2, 3]
numbers.append(4)

# Tuple (immutable)
point = (10, 20)
```

## 6. Dictionaries & Sets
```python
# Dictionary (key-value pair)
person = {"name": "Alice", "age": 25}
print(person["name"])

# Set (unique values)
unique_numbers = {1, 2, 3, 2}
```

## 7. List Comprehensions
```python
squares = [x**2 for x in range(5)]
```

## 8. Exception Handling
```python
try:
    result = 10 / 0
except ZeroDivisionError:
    print("Cannot divide by zero!")
finally:
    print("Cleanup")
```

## 9. Classes & Objects (OOP)
```python
class Car:
    def __init__(self, brand):
        self.brand = brand

    def drive(self):
        print(f"Driving {self.brand}")

car = Car("Toyota")
car.drive()
```

## 10. Modules & Imports
```python
import math
print(math.sqrt(16))

from random import randint
print(randint(1, 10))
```

## 11. File Handling
```python
# Writing to a file
with open("test.txt", "w") as file:
    file.write("Hello, World!")

# Reading a file
with open("test.txt", "r") as file:
    content = file.read()
```

## 12. Lambda Functions
```python
add = lambda x, y: x + y
print(add(3, 4))
```

## 13. Map, Filter, Reduce
```python
numbers = [1, 2, 3, 4]

# Map
squared = list(map(lambda x: x**2, numbers))

# Filter
evens = list(filter(lambda x: x % 2 == 0, numbers))

# Reduce
from functools import reduce
sum_all = reduce(lambda x, y: x + y, numbers)
```

## 14. Decorators
```python
def decorator(func):
    def wrapper():
        print("Before function")
        func()
        print("After function")
    return wrapper

@decorator
def say_hello():
    print("Hello!")

say_hello()
```

## 15. Generators & Iterators
```python
def count_up():
    n = 0
    while True:
        yield n
        n += 1

counter = count_up()
print(next(counter))
print(next(counter))
```

## 16. List & Dictionary Unpacking
```python
# List unpacking
a, b, *rest = [1, 2, 3, 4]

# Dictionary unpacking
data = {"name": "Alice", "age": 25}
print(**data)  # name=Alice age=25
```

## 17. Working with JSON
```python
import json

data = {"name": "Alice", "age": 25}
json_str = json.dumps(data)  # Convert to JSON string
json_data = json.loads(json_str)  # Convert back to Python dictionary
```

## 18. Virtual Environments & Package Management
```sh
# Create virtual environment
python -m venv venv

# Activate (Windows)
venv\Scripts\activate

# Activate (Mac/Linux)
source venv/bin/activate

# Install package
pip install requests
```

## 19. Multithreading & Multiprocessing
```python
import threading

def print_numbers():
    for i in range(5):
        print(i)

thread = threading.Thread(target=print_numbers)
thread.start()
thread.join()
```

## 20. Async & Await (Concurrency)
```python
import asyncio

async def fetch_data():
    print("Fetching...")
    await asyncio.sleep(2)
    print("Done")

asyncio.run(fetch_data())
```
