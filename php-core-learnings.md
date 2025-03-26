# PHP Essentials: 20% Knowledge for 80% Understanding

## 1. Basic Syntax and Structure
```php
<?php
    // PHP code starts with <?php and ends with ?>
    echo "Hello World!"; // Basic output
    
    // Variable declaration
    $name = "Girish";
    $age = 25;
    
    // String concatenation
    $greeting = "Hello, " . $name;
    
    // Variable interpolation
    $message = "I am $age years old";
?>
```

## 2. Data Types
- Scalar Types:
  - `int`: Integer numbers
  - `float`: Floating-point numbers
  - `string`: Text data
  - `bool`: True/False values

- Compound Types:
  - `array`: Ordered map/list
  - `object`: Instance of a class

## 3. Control Structures
```php
// Conditional Statements
if ($age >= 18) {
    echo "Adult";
} elseif ($age >= 13) {
    echo "Teenager";
} else {
    echo "Child";
}

// Switch Statement
switch ($age) {
    case 18:
        echo "Just became an adult";
        break;
    case 25:
        echo "Mid-twenties";
        break;
    default:
        echo "Other age";
}

// Loops
// For Loop
for ($i = 0; $i < 10; $i++) {
    echo $i;
}

// While Loop
while ($condition) {
    // Code block
}

// Foreach Loop (for arrays)
$colors = ["red", "green", "blue"];
foreach ($colors as $color) {
    echo $color;
}
```

## 4. Functions
```php
// Function Definition
function greet($name = "Guest") {
    return "Hello, $name!";
}

// Anonymous Functions (Closures)
$multiply = function($a, $b) {
    return $a * $b;
};

// Arrow Functions (PHP 7.4+)
$add = fn($a, $b) => $a + $b;
```

## 5. Arrays
```php
// Indexed Array
$fruits = ["apple", "banana", "cherry"];

// Associative Array
$person = [
    "name" => "Girish",
    "age" => 25,
    "city" => "Mumbai"
];

// Multidimensional Array
$matrix = [
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9]
];

// Array Functions
$numbers = [1, 2, 3, 4, 5];
$squared = array_map(fn($n) => $n * $n, $numbers);
$sum = array_sum($numbers);
```

## 6. Object-Oriented Programming
```php
class Person {
    // Properties
    public $name;
    private $age;
    
    // Constructor
    public function __construct($name, $age) {
        $this->name = $name;
        $this->age = $age;
    }
    
    // Method
    public function introduce() {
        return "I'm {$this->name}, {$this->age} years old";
    }
}

// Object Creation
$girish = new Person("Girish", 25);
echo $girish->introduce();
```

## 7. Error Handling
```php
try {
    // Code that might throw an exception
    $result = 10 / 0; // Will cause an error
} catch (Exception $e) {
    echo "Error: " . $e->getMessage();
} finally {
    // Optional cleanup code
    echo "Operation completed";
}
```

## 8. Database Interaction (MySQLi)
```php
// Database Connection
$conn = new mysqli("localhost", "username", "password", "database");

// Check connection
if ($conn->connect_error) {
    die("Connection failed: " . $conn->connect_error);
}

// Prepared Statement
$stmt = $conn->prepare("INSERT INTO users (name, age) VALUES (?, ?)");
$stmt->bind_param("si", $name, $age);
$stmt->execute();
```

## 9. File Handling
```php
// Reading a file
$content = file_get_contents("example.txt");

// Writing to a file
file_put_contents("output.txt", "Hello World!");

// File operations
if (file_exists("example.txt")) {
    unlink("example.txt"); // Delete file
}
```

## 10. Key PHP Superglobals
- `$_GET`: Retrieve data from URL parameters
- `$_POST`: Retrieve data from form submissions
- `$_SESSION`: Store user session data
- `$_COOKIE`: Manage browser cookies
- `$_SERVER`: Server and execution environment info

## Essential Tips
1. Always use `===` for strict equality comparison
2. Use `trim()` to remove whitespace from inputs
3. Validate and sanitize all user inputs
4. Use prepared statements to prevent SQL injection
5. Enable error reporting during development
