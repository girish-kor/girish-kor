# CORE JAVA ESSENTIAL NOTES

## 1. Java Fundamentals

### Basic Structure
- Java is platform-independent ("write once, run anywhere")
- All code is written inside classes
- File name must match public class name with `.java` extension
- Source code is compiled to bytecode (`.class` files)
- Bytecode runs on the Java Virtual Machine (JVM)

### Main Method
```java
public class HelloWorld {
    public static void main(String[] args) {
        System.out.println("Hello, World!");
    }
}
```

### Data Types
- **Primitive Types**:
  - `byte` (8-bit), `short` (16-bit), `int` (32-bit), `long` (64-bit)
  - `float` (32-bit), `double` (64-bit)
  - `char` (16-bit Unicode character)
  - `boolean` (true/false)
- **Reference Types**:
  - Classes, Interfaces, Arrays, Enums

### Variables
```java
// Declaration and initialization
int number = 10;
String text = "Hello";
final double PI = 3.14159; // Constants (final)

// Type inference (Java 10+)
var message = "Hello"; // Inferred as String
```

### Operators
- Arithmetic: `+`, `-`, `*`, `/`, `%`
- Assignment: `=`, `+=`, `-=`, `*=`, `/=`
- Comparison: `==`, `!=`, `>`, `<`, `>=`, `<=`
- Logical: `&&`, `||`, `!`
- Increment/Decrement: `++`, `--`

## 2. Control Flow

### Conditional Statements
```java
// If-else statement
if (condition) {
    // code block
} else if (anotherCondition) {
    // code block
} else {
    // code block
}

// Switch statement
switch (variable) {
    case value1:
        // code block
        break;
    case value2:
        // code block
        break;
    default:
        // code block
}

// Ternary operator
String result = (condition) ? "True" : "False";

// Enhanced switch (Java 14+)
switch (day) {
    case MONDAY, FRIDAY -> System.out.println("Weekday");
    case SATURDAY, SUNDAY -> System.out.println("Weekend");
    default -> System.out.println("Midweek");
}
```

### Loops
```java
// For loop
for (int i = 0; i < 5; i++) {
    // code block
}

// Enhanced for loop (for-each)
for (String item : collection) {
    // code block
}

// While loop
while (condition) {
    // code block
}

// Do-while loop
do {
    // code block
} while (condition);
```

## 3. Object-Oriented Programming

### Classes and Objects
```java
// Class definition
public class Person {
    // Instance variables (fields)
    private String name;
    private int age;
    
    // Constructor
    public Person(String name, int age) {
        this.name = name;
        this.age = age;
    }
    
    // Methods
    public String getName() {
        return name;
    }
    
    public void setName(String name) {
        this.name = name;
    }
    
    public int getAge() {
        return age;
    }
    
    public void setAge(int age) {
        this.age = age;
    }
}

// Creating objects
Person person1 = new Person("John", 30);
```

### Inheritance
```java
// Parent class
public class Animal {
    protected String name;
    
    public Animal(String name) {
        this.name = name;
    }
    
    public void eat() {
        System.out.println(name + " is eating");
    }
}

// Child class
public class Dog extends Animal {
    private String breed;
    
    public Dog(String name, String breed) {
        super(name); // Call parent constructor
        this.breed = breed;
    }
    
    public void bark() {
        System.out.println(name + " is barking");
    }
    
    // Method overriding
    @Override
    public void eat() {
        System.out.println(name + " the dog is eating");
    }
}
```

### Polymorphism
```java
Animal animal1 = new Animal("Generic Animal");
Animal animal2 = new Dog("Rex", "German Shepherd"); // Upcasting

animal1.eat(); // Calls Animal's eat method
animal2.eat(); // Calls Dog's eat method (runtime polymorphism)
```

### Abstraction
```java
// Abstract class
public abstract class Shape {
    abstract double area(); // Abstract method
    
    public void display() { // Concrete method
        System.out.println("Area: " + area());
    }
}

// Concrete implementation
public class Circle extends Shape {
    private double radius;
    
    public Circle(double radius) {
        this.radius = radius;
    }
    
    @Override
    double area() {
        return Math.PI * radius * radius;
    }
}
```

### Interfaces
```java
// Interface definition
public interface Drawable {
    void draw(); // Abstract method
    
    default void display() { // Default method (Java 8+)
        System.out.println("Displaying the drawable");
    }
    
    static void info() { // Static method (Java 8+)
        System.out.println("This is a drawable interface");
    }
}

// Implementation
public class Rectangle implements Drawable {
    @Override
    public void draw() {
        System.out.println("Drawing a rectangle");
    }
}
```

### Encapsulation
```java
public class BankAccount {
    private double balance; // Private field
    
    public double getBalance() {
        return balance;
    }
    
    public void deposit(double amount) {
        if (amount > 0) {
            balance += amount;
        }
    }
    
    public boolean withdraw(double amount) {
        if (amount > 0 && balance >= amount) {
            balance -= amount;
            return true;
        }
        return false;
    }
}
```

## 4. Exception Handling

### Try-Catch-Finally
```java
try {
    // Code that might throw an exception
    int result = 10 / 0;
} catch (ArithmeticException e) {
    // Handle specific exception
    System.out.println("Cannot divide by zero");
} catch (Exception e) {
    // Handle other exceptions
    System.out.println("An error occurred: " + e.getMessage());
} finally {
    // Always executed, regardless of exceptions
    System.out.println("Finally block executed");
}
```

### Try-with-Resources (Java 7+)
```java
try (FileReader reader = new FileReader("file.txt");
     BufferedReader br = new BufferedReader(reader)) {
    // Resources are automatically closed
    String line = br.readLine();
    System.out.println(line);
} catch (IOException e) {
    System.out.println("Error reading file: " + e.getMessage());
}
```

### Throwing Exceptions
```java
public void checkAge(int age) throws IllegalArgumentException {
    if (age < 0) {
        throw new IllegalArgumentException("Age cannot be negative");
    }
}
```

### Custom Exceptions
```java
public class InsufficientFundsException extends Exception {
    public InsufficientFundsException(String message) {
        super(message);
    }
}
```

## 5. Collections Framework

### Collection Hierarchy
- **Collection** (interface)
  - **List**: Ordered collection (ArrayList, LinkedList)
  - **Set**: No duplicates (HashSet, TreeSet, LinkedHashSet)
  - **Queue**: FIFO structure (PriorityQueue, LinkedList)
- **Map** (interface): Key-value pairs (HashMap, TreeMap, LinkedHashMap)

### ArrayList
```java
// Creating
ArrayList<String> names = new ArrayList<>();

// Adding elements
names.add("Alice");
names.add("Bob");
names.add(1, "Charlie"); // Insert at index 1

// Accessing
String first = names.get(0);

// Modifying
names.set(0, "Alex");

// Removing
names.remove(2); // By index
names.remove("Bob"); // By value

// Iterating
for (String name : names) {
    System.out.println(name);
}

names.forEach(name -> System.out.println(name)); // Lambda (Java 8+)
```

### HashMap
```java
// Creating
HashMap<Integer, String> employees = new HashMap<>();

// Adding entries
employees.put(101, "John");
employees.put(102, "Mary");

// Accessing
String employee = employees.get(101);

// Checking
boolean containsKey = employees.containsKey(102);
boolean containsValue = employees.containsValue("Mary");

// Removing
employees.remove(101);

// Iterating
for (Map.Entry<Integer, String> entry : employees.entrySet()) {
    System.out.println(entry.getKey() + ": " + entry.getValue());
}

employees.forEach((id, name) -> 
    System.out.println(id + ": " + name)); // Lambda (Java 8+)
```

## 6. Generics

### Generic Classes
```java
// Generic class
public class Box<T> {
    private T content;
    
    public Box(T content) {
        this.content = content;
    }
    
    public T getContent() {
        return content;
    }
    
    public void setContent(T content) {
        this.content = content;
    }
}

// Usage
Box<Integer> intBox = new Box<>(10);
Box<String> stringBox = new Box<>("Hello");
```

### Generic Methods
```java
public <T> void printArray(T[] array) {
    for (T element : array) {
        System.out.println(element);
    }
}

// Usage
Integer[] intArray = {1, 2, 3};
String[] stringArray = {"a", "b", "c"};

printArray(intArray);
printArray(stringArray);
```

### Bounded Type Parameters
```java
// Upper bound
public <T extends Number> double sum(T[] array) {
    double sum = 0.0;
    for (T element : array) {
        sum += element.doubleValue();
    }
    return sum;
}

// Multiple bounds
public <T extends Comparable<T> & Serializable> void process(T data) {
    // code
}
```

## 7. Functional Programming (Java 8+)

### Lambda Expressions
```java
// Traditional anonymous class
Runnable runnable1 = new Runnable() {
    @Override
    public void run() {
        System.out.println("Running");
    }
};

// Lambda expression
Runnable runnable2 = () -> System.out.println("Running");

// With parameters
Comparator<String> comparator = (s1, s2) -> s1.length() - s2.length();

// With multiple statements
Consumer<String> consumer = s -> {
    s = s.toUpperCase();
    System.out.println(s);
};
```

### Functional Interfaces
```java
// Predicate - boolean test(T t)
Predicate<Integer> isPositive = num -> num > 0;
boolean result = isPositive.test(5); // true

// Function - R apply(T t)
Function<String, Integer> length = str -> str.length();
int len = length.apply("Hello"); // 5

// Consumer - void accept(T t)
Consumer<String> print = s -> System.out.println(s);
print.accept("Hello"); // Prints "Hello"

// Supplier - T get()
Supplier<Double> random = () -> Math.random();
double value = random.get();
```

### Stream API
```java
List<String> names = Arrays.asList("Alice", "Bob", "Charlie", "Dave");

// Filtering
List<String> longNames = names.stream()
                              .filter(name -> name.length() > 4)
                              .collect(Collectors.toList());

// Mapping
List<Integer> nameLengths = names.stream()
                                .map(String::length)
                                .collect(Collectors.toList());

// Sorting
List<String> sortedNames = names.stream()
                               .sorted()
                               .collect(Collectors.toList());

// Reduction
Optional<String> concatenated = names.stream()
                                   .reduce((a, b) -> a + ", " + b);

// Statistics
IntSummaryStatistics stats = names.stream()
                                .mapToInt(String::length)
                                .summaryStatistics();
double average = stats.getAverage();
int max = stats.getMax();
```

## 8. File I/O

### Reading Files
```java
// Java 7+ (try-with-resources)
try (BufferedReader reader = new BufferedReader(new FileReader("file.txt"))) {
    String line;
    while ((line = reader.readLine()) != null) {
        System.out.println(line);
    }
} catch (IOException e) {
    e.printStackTrace();
}

// Java 8+ (Files)
try {
    List<String> lines = Files.readAllLines(Paths.get("file.txt"));
    lines.forEach(System.out::println);
} catch (IOException e) {
    e.printStackTrace();
}

// Java 8+ (Stream)
try (Stream<String> stream = Files.lines(Paths.get("file.txt"))) {
    stream.forEach(System.out::println);
} catch (IOException e) {
    e.printStackTrace();
}
```

### Writing Files
```java
// Java 7+ (try-with-resources)
try (BufferedWriter writer = new BufferedWriter(new FileWriter("file.txt"))) {
    writer.write("Hello, World!");
    writer.newLine();
    writer.write("Another line");
} catch (IOException e) {
    e.printStackTrace();
}

// Java 8+ (Files)
try {
    List<String> lines = Arrays.asList("Line 1", "Line 2", "Line 3");
    Files.write(Paths.get("file.txt"), lines);
} catch (IOException e) {
    e.printStackTrace();
}
```

## 9. Multithreading

### Creating Threads
```java
// Extending Thread class
class MyThread extends Thread {
    @Override
    public void run() {
        System.out.println("Thread running: " + Thread.currentThread().getName());
    }
}
MyThread thread1 = new MyThread();
thread1.start();

// Implementing Runnable interface
class MyRunnable implements Runnable {
    @Override
    public void run() {
        System.out.println("Runnable running: " + Thread.currentThread().getName());
    }
}
Thread thread2 = new Thread(new MyRunnable());
thread2.start();

// Using lambda (Java 8+)
Thread thread3 = new Thread(() -> {
    System.out.println("Lambda running: " + Thread.currentThread().getName());
});
thread3.start();
```

### Thread Synchronization
```java
// Synchronized method
public synchronized void increment() {
    count++;
}

// Synchronized block
public void increment() {
    synchronized(this) {
        count++;
    }
}

// Lock objects
private final Object lock = new Object();
public void increment() {
    synchronized(lock) {
        count++;
    }
}
```

### Executor Framework
```java
// Single thread executor
ExecutorService executor = Executors.newSingleThreadExecutor();
executor.submit(() -> System.out.println("Task executed"));
executor.shutdown();

// Fixed thread pool
ExecutorService pool = Executors.newFixedThreadPool(5);
for (int i = 0; i < 10; i++) {
    final int taskId = i;
    pool.submit(() -> System.out.println("Task " + taskId + " executed"));
}
pool.shutdown();
```

### Future and CompletableFuture
```java
// Future
ExecutorService executor = Executors.newSingleThreadExecutor();
Future<Integer> future = executor.submit(() -> {
    Thread.sleep(1000);
    return 123;
});
try {
    Integer result = future.get(); // Blocks until completed
    System.out.println("Result: " + result);
} catch (Exception e) {
    e.printStackTrace();
}
executor.shutdown();

// CompletableFuture (Java 8+)
CompletableFuture<String> future = CompletableFuture.supplyAsync(() -> {
    try {
        Thread.sleep(1000);
    } catch (InterruptedException e) {
        throw new RuntimeException(e);
    }
    return "Result";
}).thenApply(s -> s + " processed");

future.thenAccept(System.out::println);
```

## 10. Java Memory Management

### Memory Areas
- **Stack**: Local variables, method calls
- **Heap**: Objects, instance variables
- **Method Area**: Class metadata, static variables
- **PC Registers**: Address of current instruction
- **Native Method Stack**: Native method information

### Garbage Collection
- Automatic memory management
- Objects without references are eligible for GC
- `System.gc()` suggests GC (not guaranteed)
- Finalize method called before object destruction

### References (Java 1.2+)
```java
// Strong reference
Object strong = new Object(); // Not eligible for GC while referenced

// Weak reference
WeakReference<Object> weak = new WeakReference<>(new Object());
// Eligible for GC when no strong references exist

// Soft reference
SoftReference<Object> soft = new SoftReference<>(new Object());
// May be collected when memory is low

// Phantom reference
ReferenceQueue<Object> queue = new ReferenceQueue<>();
PhantomReference<Object> phantom = new PhantomReference<>(new Object(), queue);
// Used to be notified when object is physically removed
```
