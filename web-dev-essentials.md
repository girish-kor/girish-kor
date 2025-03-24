# HTML, CSS & JAVASCRIPT ESSENTIAL NOTES

## HTML FUNDAMENTALS

### Basic HTML Document Structure
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document Title</title>
    <link rel="stylesheet" href="styles.css">
    <script src="script.js" defer></script>
</head>
<body>
    <!-- Content goes here -->
</body>
</html>
```

### Essential HTML Elements

#### Text Elements
```html
<h1>Heading Level 1</h1>
<h2>Heading Level 2</h2>
<!-- h3, h4, h5, h6 also available -->

<p>Paragraph text</p>

<strong>Bold text</strong>
<em>Italic text</em>
<span>Inline container</span>
<br> <!-- Line break -->
<hr> <!-- Horizontal rule -->
```

#### Lists
```html
<!-- Unordered List -->
<ul>
    <li>Item 1</li>
    <li>Item 2</li>
</ul>

<!-- Ordered List -->
<ol>
    <li>First item</li>
    <li>Second item</li>
</ol>

<!-- Description List -->
<dl>
    <dt>Term</dt>
    <dd>Description</dd>
</dl>
```

#### Links and Images
```html
<!-- Links -->
<a href="https://example.com">Link Text</a>
<a href="page.html">Internal Link</a>
<a href="#section-id">Jump to Section</a>
<a href="mailto:email@example.com">Email Link</a>

<!-- Images -->
<img src="image.jpg" alt="Description of image">
```

#### Tables
```html
<table>
    <thead>
        <tr>
            <th>Header 1</th>
            <th>Header 2</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Row 1, Cell 1</td>
            <td>Row 1, Cell 2</td>
        </tr>
        <tr>
            <td>Row 2, Cell 1</td>
            <td>Row 2, Cell 2</td>
        </tr>
    </tbody>
</table>
```

#### Forms
```html
<form action="/submit" method="post">
    <!-- Text input -->
    <label for="name">Name:</label>
    <input type="text" id="name" name="name" required>
    
    <!-- Email input -->
    <label for="email">Email:</label>
    <input type="email" id="email" name="email">
    
    <!-- Password input -->
    <label for="password">Password:</label>
    <input type="password" id="password" name="password">
    
    <!-- Radio buttons -->
    <input type="radio" id="option1" name="option" value="1">
    <label for="option1">Option 1</label>
    
    <input type="radio" id="option2" name="option" value="2">
    <label for="option2">Option 2</label>
    
    <!-- Checkboxes -->
    <input type="checkbox" id="check1" name="check1">
    <label for="check1">Check this</label>
    
    <!-- Select dropdown -->
    <label for="select">Choose an option:</label>
    <select id="select" name="select">
        <option value="1">Option 1</option>
        <option value="2">Option 2</option>
    </select>
    
    <!-- Textarea -->
    <label for="message">Message:</label>
    <textarea id="message" name="message" rows="4" cols="50"></textarea>
    
    <!-- Submit button -->
    <button type="submit">Submit</button>
</form>
```

#### Semantic HTML Elements
```html
<header>Site or section header</header>
<nav>Navigation menu</nav>
<main>Main content</main>
<article>Self-contained content</article>
<section>Thematic grouping</section>
<aside>Sidebar content</aside>
<footer>Site or section footer</footer>
```

#### Containers
```html
<div>Generic block container</div>
<span>Generic inline container</span>
```

## CSS FUNDAMENTALS

### Linking CSS
```html
<!-- External CSS -->
<link rel="stylesheet" href="styles.css">

<!-- Internal CSS -->
<style>
    p { color: blue; }
</style>

<!-- Inline CSS -->
<p style="color: red;">This is red text</p>
```

### Selectors
```css
/* Element selector */
p { color: blue; }

/* Class selector */
.my-class { font-size: 16px; }

/* ID selector */
#my-id { font-weight: bold; }

/* Attribute selector */
input[type="text"] { border: 1px solid gray; }

/* Descendant selector */
div p { margin-left: 20px; }

/* Child selector */
ul > li { list-style-type: square; }

/* Pseudo-class */
a:hover { text-decoration: underline; }

/* Pseudo-element */
p::first-line { font-weight: bold; }
```

### Box Model
```css
div {
    width: 300px;
    height: 200px;
    padding: 20px;
    border: 2px solid black;
    margin: 30px;
    /* Total width: 300 + 20*2 + 2*2 + 30*2 = 404px */
    
    /* Alternative: Keep defined width including padding/border */
    box-sizing: border-box;
}
```

### Typography
```css
body {
    font-family: 'Arial', sans-serif;
    font-size: 16px;
    font-weight: normal; /* or bold, 400, 700, etc. */
    line-height: 1.5;
    color: #333;
    text-align: left; /* or center, right, justify */
    text-decoration: none; /* or underline, line-through */
    text-transform: none; /* or uppercase, lowercase, capitalize */
    letter-spacing: normal;
    word-spacing: normal;
}
```

### Colors and Backgrounds
```css
div {
    /* Colors */
    color: #0066cc; /* Hexadecimal */
    color: rgb(0, 102, 204); /* RGB */
    color: rgba(0, 102, 204, 0.5); /* RGBA with opacity */
    color: hsl(210, 100%, 40%); /* HSL */
    
    /* Backgrounds */
    background-color: #f5f5f5;
    background-image: url('image.jpg');
    background-repeat: no-repeat;
    background-position: center;
    background-size: cover;
    
    /* Shorthand */
    background: #f5f5f5 url('image.jpg') no-repeat center/cover;
}
```

### Layout: Display Property
```css
/* Block elements (take full width, start on new line) */
div { display: block; }

/* Inline elements (only take necessary width, don't break flow) */
span { display: inline; }

/* Inline-block (inline but can have width/height) */
.inline-block { display: inline-block; }

/* Hidden elements */
.hidden { display: none; }

/* Flex container */
.container { display: flex; }

/* Grid container */
.grid { display: grid; }
```

### Flexbox
```css
.container {
    display: flex;
    flex-direction: row; /* or column, row-reverse, column-reverse */
    flex-wrap: wrap; /* or nowrap, wrap-reverse */
    justify-content: space-between; /* or flex-start, flex-end, center, space-around, space-evenly */
    align-items: center; /* or flex-start, flex-end, stretch, baseline */
    gap: 20px; /* spacing between items */
}

.item {
    flex: 1; /* or specific flex-grow, flex-shrink, flex-basis values */
    align-self: center; /* override align-items for specific item */
    order: 1; /* change order of specific items */
}
```

### Grid Layout
```css
.grid-container {
    display: grid;
    grid-template-columns: 1fr 2fr 1fr; /* three columns */
    grid-template-rows: 100px auto 100px; /* three rows */
    gap: 20px; /* spacing between grid cells */
    
    /* Named areas */
    grid-template-areas:
        "header header header"
        "sidebar main main"
        "footer footer footer";
}

.header { grid-area: header; }
.sidebar { grid-area: sidebar; }
.main { grid-area: main; }
.footer { grid-area: footer; }

/* Positioning items manually */
.item {
    grid-column: 1 / 3; /* start at line 1, end at line 3 */
    grid-row: 2 / 3; /* start at line 2, end at line 3 */
}
```

### Position
```css
/* Static (default) */
.static { position: static; }

/* Relative (positioned relative to normal position) */
.relative {
    position: relative;
    top: 10px;
    left: 20px;
}

/* Absolute (positioned relative to nearest positioned ancestor) */
.absolute {
    position: absolute;
    top: 40px;
    right: 0;
}

/* Fixed (positioned relative to viewport) */
.fixed {
    position: fixed;
    bottom: 0;
    left: 0;
    width: 100%;
}

/* Sticky (acts like relative until scrolled to threshold) */
.sticky {
    position: sticky;
    top: 0;
}
```

### Responsive Design
```css
/* Media queries */
@media (max-width: 768px) {
    /* Styles for screens 768px wide or less */
    .container {
        flex-direction: column;
    }
}

/* Fluid layout */
.container {
    width: 100%;
    max-width: 1200px;
    margin: 0 auto;
}

/* Responsive images */
img {
    max-width: 100%;
    height: auto;
}

/* Responsive typography */
html {
    font-size: 16px;
}

@media (max-width: 768px) {
    html {
        font-size: 14px;
    }
}

h1 { font-size: 2rem; } /* relative to root font size */
```

### Transitions and Animations
```css
/* Transitions */
.button {
    background-color: blue;
    color: white;
    transition: background-color 0.3s ease, transform 0.2s ease;
}

.button:hover {
    background-color: darkblue;
    transform: scale(1.05);
}

/* Animations */
@keyframes slide-in {
    0% {
        transform: translateX(-100%);
        opacity: 0;
    }
    100% {
        transform: translateX(0);
        opacity: 1;
    }
}

.animated-element {
    animation: slide-in 1s ease-out forwards;
}
```

## JAVASCRIPT FUNDAMENTALS

### Including JavaScript
```html
<!-- External JavaScript -->
<script src="script.js"></script>

<!-- Inline JavaScript -->
<script>
    console.log("Hello, World!");
</script>

<!-- Modern approach: defer loading until HTML is parsed -->
<script src="script.js" defer></script>
```

### Variables and Data Types
```javascript
// Variables
let name = "John"; // Block-scoped, can be reassigned
const age = 30; // Block-scoped, cannot be reassigned
var legacy = "old"; // Function-scoped, avoid using

// Data Types
// Primitives
let string = "Text";
let number = 42;
let decimal = 3.14;
let boolean = true;
let nullValue = null;
let undefinedValue;
let symbol = Symbol("unique");
let bigInt = 9007199254740991n;

// Reference Types
let array = [1, 2, 3, "four"];
let object = { name: "John", age: 30 };
let func = function() { return "Hello"; };
let date = new Date();
let regex = /pattern/;
```

### Operators
```javascript
// Arithmetic operators
let sum = 5 + 5;
let difference = 10 - 5;
let product = 5 * 5;
let quotient = 10 / 2;
let remainder = 10 % 3;
let exponent = 2 ** 3; // 2^3 = 8

// Assignment operators
let x = 10;
x += 5; // x = x + 5
x -= 3; // x = x - 3
x *= 2; // x = x * 2
x /= 4; // x = x / 4

// Comparison operators
let isEqual = 5 == "5"; // true (loose equality)
let isStrictEqual = 5 === "5"; // false (strict equality)
let isNotEqual = 5 != "6"; // true
let isStrictNotEqual = 5 !== "5"; // true
let isGreater = 10 > 5; // true
let isLess = 5 < 10; // true
let isGreaterOrEqual = 10 >= 10; // true
let isLessOrEqual = 5 <= 5; // true

// Logical operators
let and = true && false; // false
let or = true || false; // true
let not = !true; // false

// Ternary operator
let status = age >= 18 ? "adult" : "minor";
```

### Control Flow
```javascript
// Conditional statements
if (age >= 18) {
    console.log("Adult");
} else if (age >= 13) {
    console.log("Teenager");
} else {
    console.log("Child");
}

// Switch statement
switch (day) {
    case "Monday":
        console.log("Start of work week");
        break;
    case "Friday":
        console.log("End of work week");
        break;
    case "Saturday":
    case "Sunday":
        console.log("Weekend");
        break;
    default:
        console.log("Midweek");
}

// Loops
// For loop
for (let i = 0; i < 5; i++) {
    console.log(i);
}

// For...of loop (arrays)
for (const item of array) {
    console.log(item);
}

// For...in loop (objects)
for (const key in object) {
    console.log(key + ": " + object[key]);
}

// While loop
let i = 0;
while (i < 5) {
    console.log(i);
    i++;
}

// Do...while loop
let j = 0;
do {
    console.log(j);
    j++;
} while (j < 5);
```

### Functions
```javascript
// Function declaration
function greet(name) {
    return "Hello, " + name + "!";
}

// Function expression
const greet = function(name) {
    return "Hello, " + name + "!";
};

// Arrow function
const greet = (name) => {
    return "Hello, " + name + "!";
};

// Simplified arrow function (implicit return)
const greet = name => "Hello, " + name + "!";

// Default parameters
function greet(name = "Guest") {
    return "Hello, " + name + "!";
}

// Rest parameters
function sum(...numbers) {
    return numbers.reduce((total, num) => total + num, 0);
}

// Immediately Invoked Function Expression (IIFE)
(function() {
    console.log("This runs immediately");
})();
```

### Arrays
```javascript
// Creating arrays
let fruits = ["apple", "banana", "orange"];
let numbers = new Array(1, 2, 3);

// Accessing elements
let firstFruit = fruits[0]; // "apple"

// Common array methods
fruits.push("grape"); // Add to end
fruits.pop(); // Remove from end
fruits.unshift("mango"); // Add to beginning
fruits.shift(); // Remove from beginning
fruits.splice(1, 2, "pear", "kiwi"); // Remove elements and insert new ones
let sliced = fruits.slice(1, 3); // Return portion without modifying original

// Iterating arrays
fruits.forEach((fruit, index) => {
    console.log(index + ": " + fruit);
});

// Transforming arrays
let uppercaseFruits = fruits.map(fruit => fruit.toUpperCase());
let longFruits = fruits.filter(fruit => fruit.length > 5);
let allLong = fruits.every(fruit => fruit.length > 3);
let someLong = fruits.some(fruit => fruit.length > 6);
let foundFruit = fruits.find(fruit => fruit.startsWith("a"));
let fruitString = fruits.join(", ");
let total = numbers.reduce((sum, num) => sum + num, 0);
```

### Objects
```javascript
// Creating objects
let person = {
    firstName: "John",
    lastName: "Doe",
    age: 30,
    // Method
    fullName: function() {
        return this.firstName + " " + this.lastName;
    }
};

// Shorthand method definition
let person = {
    firstName: "John",
    lastName: "Doe",
    fullName() {
        return this.firstName + " " + this.lastName;
    }
};

// Accessing properties
let name = person.firstName; // Dot notation
let age = person["age"]; // Bracket notation

// Adding/modifying properties
person.email = "john@example.com"; 
person["phone"] = "555-1234";

// Removing properties
delete person.age;

// Object methods
let keys = Object.keys(person); // Array of keys
let values = Object.values(person); // Array of values
let entries = Object.entries(person); // Array of [key, value] pairs
let hasProp = Object.hasOwnProperty("firstName"); // true

// Object destructuring
let { firstName, lastName } = person;
```

### DOM Manipulation
```javascript
// Selecting elements
let element = document.getElementById("myId");
let elements = document.getElementsByClassName("myClass");
let tags = document.getElementsByTagName("div");
let queryElement = document.querySelector(".myClass"); // First match
let queryElements = document.querySelectorAll("div.item"); // All matches

// Modifying content
element.textContent = "New text"; // Just text
element.innerHTML = "<strong>Bold text</strong>"; // HTML content

// Modifying attributes
element.setAttribute("id", "newId");
let value = element.getAttribute("class");
element.removeAttribute("style");

// Classes
element.classList.add("active");
element.classList.remove("hidden");
element.classList.toggle("highlight");
let hasClass = element.classList.contains("active");

// Styles
element.style.color = "blue";
element.style.fontSize = "16px";
element.style.display = "none";

// Creating elements
let newDiv = document.createElement("div");
newDiv.textContent = "New Div";
document.body.appendChild(newDiv); // Add to end of body

// Remove elements
element.remove(); // Remove element
parent.removeChild(child); // Remove child from parent

// Navigating the DOM
let parent = element.parentElement;
let children = element.children;
let firstChild = element.firstElementChild;
let nextSibling = element.nextElementSibling;
```

### Events
```javascript
// Adding event listeners
element.addEventListener("click", function(event) {
    console.log("Element clicked");
});

// Arrow function
element.addEventListener("mouseover", (event) => {
    element.style.color = "red";
});

// Named function
function handleClick(event) {
    console.log("Clicked:", event.target);
}
element.addEventListener("click", handleClick);

// Removing event listeners
element.removeEventListener("click", handleClick);

// Common events
// Mouse: click, dblclick, mousedown, mouseup, mouseover, mouseout, mousemove
// Keyboard: keydown, keyup, keypress
// Form: submit, change, input, focus, blur
// Window: load, resize, scroll, unload
// Document: DOMContentLoaded

// Event object properties
function handleEvent(event) {
    event.preventDefault(); // Prevent default action
    event.stopPropagation(); // Stop event bubbling
    
    console.log(event.target); // Element that triggered event
    console.log(event.currentTarget); // Element that listener is attached to
    console.log(event.type); // Type of event
    console.log(event.clientX, event.clientY); // Mouse coordinates
}

// Event delegation
document.getElementById("parent").addEventListener("click", function(event) {
    if (event.target.matches(".button")) {
        console.log("Button clicked");
    }
});
```

### Asynchronous JavaScript
```javascript
// Callbacks
function fetchData(callback) {
    setTimeout(() => {
        callback("Data received");
    }, 1000);
}

fetchData(function(data) {
    console.log(data);
});

// Promises
function fetchData() {
    return new Promise((resolve, reject) => {
        setTimeout(() => {
            if (Math.random() > 0.2) {
                resolve("Data received");
            } else {
                reject("Error fetching data");
            }
        }, 1000);
    });
}

fetchData()
    .then(data => console.log(data))
    .catch(error => console.error(error))
    .finally(() => console.log("Operation finished"));

// Chaining promises
fetchUser()
    .then(user => fetchUserPosts(user.id))
    .then(posts => console.log(posts))
    .catch(error => console.error(error));

// Async/Await
async function getData() {
    try {
        let user = await fetchUser();
        let posts = await fetchUserPosts(user.id);
        console.log(posts);
    } catch (error) {
        console.error(error);
    }
}

// Fetch API
fetch('https://api.example.com/data')
    .then(response => {
        if (!response.ok) {
            throw new Error('Network response was not ok');
        }
        return response.json();
    })
    .then(data => console.log(data))
    .catch(error => console.error('Fetch error:', error));

// With async/await
async function fetchData() {
    try {
        const response = await fetch('https://api.example.com/data');
        if (!response.ok) {
            throw new Error('Network response was not ok');
        }
        const data = await response.json();
        console.log(data);
    } catch (error) {
        console.error('Fetch error:', error);
    }
}
```

### ES6+ Features
```javascript
// Template literals
let greeting = `Hello, ${firstName}!`;
let multiline = `Line 1
Line 2
Line 3`;

// Destructuring
// Arrays
let [a, b, ...rest] = [1, 2, 3, 4, 5];
// Objects
let { firstName, lastName: surname, age = 25 } = person;

// Spread operator
let combined = [...array1, ...array2];
let objectCopy = { ...object1, ...object2 };

// Classes
class Person {
    constructor(name, age) {
        this.name = name;
        this.age = age;
    }
    
    greet() {
        return `Hello, I'm ${this.name}`;
    }
    
    static createAnonymous() {
        return new Person("Anonymous", 0);
    }
}

// Inheritance
class Employee extends Person {
    constructor(name, age, position) {
        super(name, age);
        this.position = position;
    }
    
    greet() {
        return `${super.greet()} and I work as a ${this.position}`;
    }
}

// Modules
// file: math.js
export function add(a, b) {
    return a + b;
}
export const PI = 3.14159;

// file: main.js
import { add, PI } from './math.js';
import * as math from './math.js';
import defaultExport from './module.js';

// Arrow functions and lexical 'this'
function Traditional() {
    this.value = 42;
    setTimeout(function() {
        console.log(this.value); // undefined
    }, 1000);
}

function ArrowFunction() {
    this.value = 42;
    setTimeout(() => {
        console.log(this.value); // 42
    }, 1000);
}
```

### Local Storage
```javascript
// Storing data
localStorage.setItem('username', 'john');
localStorage.setItem('preferences', JSON.stringify({
    theme: 'dark',
    fontSize: 16
}));

// Retrieving data
const username = localStorage.getItem('username');
const preferences = JSON.parse(localStorage.getItem('preferences'));

// Removing data
localStorage.removeItem('username');

// Clearing all data
localStorage.clear();
```

### Error Handling
```javascript
// Try/Catch
try {
    // Code that might throw an error
    let result = riskyFunction();
    console.log(result);
} catch (error) {
    console.error('An error occurred:', error.message);
} finally {
    // Always executes, regardless of error
    console.log('Cleanup code');
}

// Throwing custom errors
function divide(a, b) {
    if (b === 0) {
        throw new Error('Division by zero');
    }
    return a / b;
}

// Custom error types
class ValidationError extends Error {
    constructor(message) {
        super(message);
        this.name = 'ValidationError';
    }
}

// Using custom errors
try {
    if (!isValid) {
        throw new ValidationError('Invalid data');
    }
} catch (error) {
    if (error instanceof ValidationError) {
        console.error('Validation failed:', error.message);
    } else {
        console.error('Unknown error:', error);
    }
}
```
