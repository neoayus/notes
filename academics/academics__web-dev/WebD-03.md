# Introduction to JS 
## JavaScript

JavaScript is a versatile programming language that is primarily used for creating interactive and dynamic content on web pages. As a core technology of the web, alongside HTML and CSS.

## Basic Syntax and Structure

```javascript
// Displaying a message
console.log("Hello, World!");

// Declaring a variable
let number = 10;

// Conditional statement
if (number > 5) {
   console.log("The number is greater than 5");
} else {
   console.log("The number is 5 or less");
}

// Function definition
function greet(name) {
   return "Hello, " + name;
}

// Calling the function
console.log(greet("Alice"));
```

In this example, the `console.log` function is used to print messages to the browser's console. Variables like `number` store data, and `if-else` statements make decisions based on conditions. Functions like `greet` encapsulate code that can be reused with different inputs.

##  JavaScript Syntax 
### Variables

Variables in JavaScript are used to store data values. You can declare a variable using the `let`, `const`, or `var` keywords.

- **`let`**: Declares a block-scoped variable, meaning it is only accessible within the block where it is defined.
  ```javascript
  let name = "Alice";
  ```

- **`const`**: Declares a block-scoped constant, which cannot be reassigned after its initial assignment.
  ```javascript
  const pi = 3.14;
  ```

- **`var`**: Declares a function-scoped variable. It was commonly used before `let` and `const` were introduced, but is now less preferred due to its broader scope.
  ```javascript
  var age = 25;
  ```

### Data Types

- **Number**: Represents both integers and floating-point numbers.
  ```javascript
  let temperature = 30;      // Integer
  let price = 19.99;         // Floating-point number
  ```

- **String**: Represents text and is enclosed in quotes (`"` or `'`).
  ```javascript
  let greeting = "Hello, world!";
  ```

- **Boolean**: Represents logical values, either `true` or `false`.
  ```javascript
  let isAvailable = true;
  ```

- **Array**: Represents a list of values, which can be of any data type.
  ```javascript
  let colors = ["red", "green", "blue"];
  ```

- **Object**: Represents a collection of key-value pairs.
  ```javascript
  let person = {
      firstName: "John",
      lastName: "Doe",
      age: 30
  };
  ```

- **Null**: Represents an intentional absence of any object value.
  ```javascript
  let emptyValue = null;
  ```

- **Undefined**: Represents an uninitialized variable or the absence of a value.
  ```javascript
  let notDefined;
  ```

### Operators

- **Comparison Operators**: Used to compare two values.
  ```javascript
  let isEqual = (10 == "10");      // true, because == does type conversion
  let isStrictEqual = (10 === 10); // true, because === checks both value and type
  ```

### Functions

Functions are blocks of code designed to perform a particular task. They can take input in the form of parameters and return a result.

- **Function Declaration**:
  ```javascript
  function add(a, b) {
      return a + b;
  }
  let sum = add(5, 10);  // sum will be 15
  ```

- **Arrow Functions**:
  Arrow functions are a more concise way to write functions, introduced in ES6.
  ```javascript
  const multiply = (a, b) => a * b;
  let product = multiply(5, 10);  // product will be 50
  ```


Here’s a detailed explanation of **Screen Output in JavaScript** written in a modularized paragraph style:

---

## Screen Output in JavaScript

There are different ways you can display or render information on a web page or the browser console.
JavaScript provides several methods to output data, each suited for specific scenarios such as debugging, user interaction, or updating web page content dynamically.

### Using `console.log()`

The `console.log()` method is widely used for outputting messages to the browser’s console. This is particularly useful for debugging purposes, as it allows developers to check the values of variables or the flow of execution in their code.

```javascript
let greeting = "Hello, World!";
console.log(greeting);  // Outputs: Hello, World! in the console
```

### Using `document.write()`

The `document.write()` method writes content directly to the HTML document. This method is often used for testing purposes, but it's generally discouraged for production use as it can overwrite the entire document if called after the page has fully loaded.

```javascript
document.write("This is written directly to the HTML document.");
```

While `document.write()` can be handy for simple scripts, it’s not commonly used in modern web development due to its limitations and the potential to disrupt the page’s content.

### Using `alert()`

The `alert()` method displays a pop-up dialog box with the specified message. This method is often used for debugging or to show important information to the user that requires their attention. 
However, the use of `alert()` **can be intrusive** as it blocks user interaction until the dialog is dismissed.

```javascript
alert("This is an alert message!");
```


### using `window.prompt()`

the `window.prompt()` method displays a dialog box that prompts the user for input. it returns the input value if the user clicks "ok" or `null` if the user clicks "cancel". the prompt dialog is useful for simple input tasks.

```javascript
let username = prompt("please enter your name:");
console.log("hello, " + username);
```

### Using `window.confirm()`

The `window.confirm()` method displays a dialog box with a specified message, along with "OK" and "Cancel" buttons. It returns `true` if the user clicks "OK" and `false` if the user clicks "Cancel". This is typically used for confirming user actions.

```javascript
let result = confirm("Are you sure you want to delete this?");
if (result) {
    console.log("Item deleted.");
} else {
    console.log("Action canceled.");
}
```

Here’s a detailed explanation of **String Methods in JavaScript** written in a modularized paragraph style:

---

## String Methods in JavaScript

String methods in JavaScript are built-in functions that allow you to manipulate and interact with strings in various ways. These methods enable you to perform tasks like searching within a string, modifying its content, and extracting specific parts. Understanding these methods is essential for effectively handling text data in your JavaScript programs.

### `length`

The `length` property returns the number of characters in a string, including spaces and punctuation. This is often used to determine the size of a string or to loop through each character.

```javascript
let message = "Hello, World!";
console.log(message.length);  // Outputs: 13
```

### `charAt()`

The `charAt()` method returns the character at a specified index in a string. The index is zero-based, meaning the first character has an index of 0.

```javascript
let message = "Hello, World!";
console.log(message.charAt(0));  // Outputs: H
```

### `indexOf()` and `lastIndexOf()`

The `indexOf()` method returns the index of the first occurrence of a specified substring within the string. If the substring is not found, it returns `-1`. The `lastIndexOf()` method works similarly, but it searches from the end of the string.

```javascript
let message = "Hello, World!";
console.log(message.indexOf("World"));     // Outputs: 7
console.log(message.lastIndexOf("o"));     // Outputs: 8
```

### `slice()`, `substring()`, and `substr()`

These methods are used to extract parts of a string:

- **`slice(start, end)`**: Extracts a section of a string and returns it as a new string, based on the start and end indices.
  ```javascript
  let message = "Hello, World!";
  console.log(message.slice(0, 5));  // Outputs: Hello
  ```

- **`substring(start, end)`**: Similar to `slice()`, but does not accept negative indices.
  ```javascript
  let message = "Hello, World!";
  console.log(message.substring(7, 12));  // Outputs: World
  ```

- **`substr(start, length)`**: Extracts a substring starting from a specified index and continuing for a given number of characters.
  ```javascript
  let message = "Hello, World!";
  console.log(message.substr(7, 5));  // Outputs: World
  ```

### `replace()`

The `replace()` method searches for a specified value in a string and replaces it with another value. The first parameter can be a substring or a regular expression, and the second parameter is the replacement string.

```javascript
let message = "Hello, World!";
let newMessage = message.replace("World", "JavaScript");
console.log(newMessage);  // Outputs: Hello, JavaScript!
```

### `toUpperCase()` and `toLowerCase()`

These methods are used to convert a string to all uppercase or lowercase letters, respectively.

- **`toUpperCase()`**: Converts all characters in the string to uppercase.
  ```javascript
  let message = "Hello, World!";
  console.log(message.toUpperCase());  // Outputs: HELLO, WORLD!
  ```

- **`toLowerCase()`**: Converts all characters in the string to lowercase.
  ```javascript
  let message = "Hello, World!";
  console.log(message.toLowerCase());  // Outputs: hello, world!
  ```

### `concat()`

The `concat()` method combines two or more strings and returns a new string.

```javascript
let firstName = "John";
let lastName = "Doe";
let fullName = firstName.concat(" ", lastName);
console.log(fullName);  // Outputs: John Doe
```

### `trim()`

The `trim()` method removes whitespace from both ends of a string. This is useful when dealing with user input, where extra spaces can cause issues.

```javascript
let message = "   Hello, World!   ";
console.log(message.trim());  // Outputs: Hello, World!
```

### `split()`

The `split()` method splits a string into an array of substrings based on a specified delimiter. This is particularly useful for parsing CSV data or breaking up a sentence into words.

```javascript
let message = "Hello, World!";
let words = message.split(" ");
console.log(words);  // Outputs: ["Hello,", "World!"]
```

Here’s a detailed explanation of **Arrays in JavaScript** written in a modularized paragraph style:

---

## Arrays

Arrays in JavaScript are used to store multiple values in a single variable, making it easier to manage and manipulate collections of data. 

### Declaring and Initializing Arrays

An array can be declared using square brackets `[]` or the `Array` constructor. The elements within an array are indexed, starting from `0`.

```javascript
let fruits = ["Apple", "Banana", "Cherry"];
let numbers = new Array(1, 2, 3, 4, 5);
```

In the examples above, the `fruits` array contains three strings, while the `numbers` array contains five numbers.

### Array Methods for Searching and Sorting

- **`indexOf()`**: The `indexOf()` method returns the first index at which a given element can be found in the array, or `-1` if it is not present.

  ```javascript
  let index = fruits.indexOf("Cherry");  // Outputs: 2
  ```

- **`includes()`**: The `includes()` method determines whether an array contains a specified element, returning `true` or `false`.

  ```javascript
  let hasBanana = fruits.includes("Banana");  // Outputs: false (after modification)
  ```

- **`sort()`**: The `sort()` method sorts the elements of an array in place and returns the sorted array. The default sort order is ascending, built upon converting the elements into strings.

  ```javascript
  fruits.sort();  // Sorts the array alphabetically
  ```

- **`reverse()`**: The `reverse()` method reverses the order of the elements in an array.

  ```javascript
  fruits.reverse();  // Reverses the array
  ```

# Event handling and DOM 

### **Document Object Model (DOM)**

The **Document Object Model (DOM)** is a programming interface for web documents. It represents the structure of a web page as a tree of objects, enabling programs to access, manipulate, and update the content, structure, and style of a document dynamically.

---

### **1. What is the DOM?**

- **Tree Representation**: The DOM represents an HTML or XML document as a tree-like structure where each node represents a part of the document (elements, attributes, text, etc.).
- **Platform-Independent**: It is a standard defined by the **W3C (World Wide Web Consortium)**, ensuring that it works across different browsers and platforms.
- **Interactive Web Pages**: Using the DOM, JavaScript can make web pages dynamic by modifying their elements, styles, and behaviors.

---

### **2. DOM Tree Structure**

The DOM organizes an HTML document into a **hierarchical tree** of nodes:

- **Document Node**: The root of the tree.
- **Element Nodes**: Represent HTML tags (e.g., `<div>`, `<p>`, `<a>`).
- **Text Nodes**: Contain the text inside an element.
- **Attribute Nodes**: Represent attributes of HTML elements (e.g., `class="example"`).

#### **Example:**

HTML:

```html
<!DOCTYPE html>
<html>
  <head>
    <title>Example</title>
  </head>
  <body>
    <h1>Hello World</h1>
    <p>This is a paragraph.</p>
  </body>
</html>
```

DOM Tree:

```
Document
├── html
    ├── head
    │   └── title ("Example")
    └── body
        ├── h1 ("Hello World")
        └── p ("This is a paragraph.")
```

---

### **3. Accessing the DOM**

JavaScript interacts with the DOM using the global `document` object. Some common methods include:

#### **Selecting Elements:**

- **By ID**:
    
    ```javascript
    let element = document.getElementById("id");
    ```
    
- **By Class Name**:
    
    ```javascript
    let elements = document.getElementsByClassName("class-name");
    ```
    
- **By Tag Name**:
    
    ```javascript
    let elements = document.getElementsByTagName("tag-name");
    ```
    
- **Using Query Selectors**:
    
    ```javascript
    let element = document.querySelector(".class-name");  // First matching element
    let elements = document.querySelectorAll(".class-name");  // All matching elements
    ```
    

---

### **4. Manipulating the DOM**

#### **Modifying Content**:

- **Change Inner HTML**:
    
    ```javascript
    let element = document.getElementById("myDiv");
    element.innerHTML = "<p>New Content</p>";
    ```
    
- **Change Text Content**:
    
    ```javascript
    element.textContent = "New Text";
    ```
    

#### **Changing Attributes**:

- **Set an Attribute**:
    
    ```javascript
    element.setAttribute("class", "new-class");
    ```
    
- **Get an Attribute**:
    
    ```javascript
    let value = element.getAttribute("id");
    ```
    
- **Remove an Attribute**:
    
    ```javascript
    element.removeAttribute("class");
    ```
    

#### **Changing Styles**:

- Modify styles using the `style` property.
    
    ```javascript
    element.style.color = "blue";
    element.style.fontSize = "20px";
    ```
    

---

### **5. Adding and Removing Elements**

#### **Creating Elements**:

- **Create a New Element**:
    
    ```javascript
    let newElement = document.createElement("div");
    ```
    
- **Add Content to the Element**:
    
    ```javascript
    newElement.textContent = "This is a new div.";
    ```
    

#### **Appending Elements**:

- **Append to the DOM**:
    
    ```javascript
    document.body.appendChild(newElement);
    ```
    

#### **Removing Elements**:

- **Remove an Element**:
    
    ```javascript
    let element = document.getElementById("myDiv");
    element.remove();
    ```
    

---

### **6. Event Handling in the DOM**

Events are actions that happen in the browser (e.g., clicking a button, loading a page). You can add event listeners to handle these actions.

#### **Adding an Event Listener**:

```javascript
let button = document.getElementById("myButton");
button.addEventListener("click", () => {
  alert("Button clicked!");
});
```

#### **Removing an Event Listener**:

```javascript
button.removeEventListener("click", myFunction);
```

## **Form Validation in JavaScript**

Form validation in JavaScript is crucial for ensuring that users input the correct type of data before submitting a form. It helps in improving user experience by providing immediate feedback and reducing errors on the server side.

---

### **1. Types of Form Validation:**

- **Client-Side Validation**: Performed on the user’s browser before data is submitted to the server. It helps in giving real-time feedback to the user.
- **Server-Side Validation**: Performed after the form data is sent to the server. It’s essential for security, as client-side validation can be bypassed.

JavaScript is commonly used for **client-side form validation**.


### **2. Common Validation Tasks**


- **Required Field Validation**: Ensures that the user has filled out a required field.
- **Email Format Validation**: Ensures that the email address is in the correct format (e.g., `example@domain.com`).
- **Password Validation**: Ensures that passwords meet certain criteria (e.g., minimum length, special characters).
- **Number Validation**: Ensures that the input is a number, and optionally, within a specific range.

---

### **3. Form Validation Techniques**

#### **Basic Structure of a Form in HTML:**

```html
<form id="myForm" onsubmit="return validateForm()">
  <label for="email">Email:</label>
  <input type="text" id="email" name="email">
  <span id="emailError" class="error"></span><br>

  <label for="password">Password:</label>
  <input type="password" id="password" name="password">
  <span id="passwordError" class="error"></span><br>

  <input type="submit" value="Submit">
</form>
```

#### **JavaScript Validation Function:**

- **Required Field Validation:**
    
    ```javascript
    function validateForm() {
      let email = document.getElementById("email").value;
      let password = document.getElementById("password").value;
      let emailError = document.getElementById("emailError");
      let passwordError = document.getElementById("passwordError");
      
      // Reset errors
      emailError.textContent = "";
      passwordError.textContent = "";
      
      // Validate email (required)
      if (email == "") {
        emailError.textContent = "Email is required!";
        return false;
      }
      
      // Validate password (required)
      if (password == "") {
        passwordError.textContent = "Password is required!";
        return false;
      }
      
      return true;
    }
    ```

### **4. Email Validation**

To check if the entered email is in the correct format, you can use a regular expression:

```javascript
function validateEmail() {
  let email = document.getElementById("email").value;
  let emailError = document.getElementById("emailError");
  let regex = /^[a-zA-Z0-9._-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,6}$/;

  // Clear previous error message
  emailError.textContent = "";

  // Check email format
  if (!regex.test(email)) {
    emailError.textContent = "Please enter a valid email address!";
    return false;
  }
  return true;
}
```

You can call `validateEmail()` inside your `validateForm()` function, just before the `return true`.
### **5. Password Validation**

For password validation, you can check if the password meets certain criteria, such as having a minimum length or including a mix of characters.

```javascript
function validatePassword() {
  let password = document.getElementById("password").value;
  let passwordError = document.getElementById("passwordError");

  // Clear previous error message
  passwordError.textContent = "";

  // Check if the password is at least 8 characters long
  if (password.length < 8) {
    passwordError.textContent = "Password must be at least 8 characters long!";
    return false;
  }

  return true;
}
```

---
----
----
# UNIT 03 ENDS HERE ! 
# \>GO TO [UNIT 04](WebD-04.md) 
