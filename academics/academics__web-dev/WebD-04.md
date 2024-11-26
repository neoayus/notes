# **PHP Basics - Comprehensive Notes for Exam Preparation**

PHP (Hypertext Preprocessor) is a widely-used server-side scripting language designed for web development. It is known for its simplicity, efficiency, and ability to integrate with HTML and databases like MySQL. Below are the essential topics of **PHP Basics** that you need to understand for your exam preparation:

---

### **1. Introduction and Basic Syntax of PHP**

- PHP is a **server-side scripting language** used for creating dynamic web pages.
- It is embedded in HTML and typically used to handle forms, sessions, databases, and more.

**Basic Syntax**:

- PHP code is written within **`<?php ... ?>`** tags.
- PHP files generally have a **`.php`** extension.

```php
<?php
  echo "Hello, World!";
?>
```

- **Statements** in PHP end with a semicolon (`;`).
- PHP is **loosely typed**, meaning you don’t need to specify variable types explicitly.

---

### **Control Statements in PHP**

PHP supports several control structures to control the flow of execution in a program.
#### **Conditional Statements**:

- **`if`**: Executes the block of code if the condition is true.
    
    ```php
    if ($age > 18) {
      echo "You are an adult.";
    }
    ```
    
- **`else`**: Executes if the condition in the `if` statement is false.
    
    ```php
    if ($age > 18) {
      echo "Adult";
    } else {
      echo "Not an adult";
    }
    ```
    
- **`elseif`**: Checks multiple conditions.
    
    ```php
    if ($age > 18) {
      echo "Adult";
    } elseif ($age == 18) {
      echo "Just an adult!";
    } else {
      echo "Not an adult";
    }
    ```
    

#### **Switch-Case**:

- Used to compare a variable against multiple values.
    
    ```php
    switch ($day) {
      case "Monday":
        echo "Start of the week!";
        break;
      case "Friday":
        echo "End of the week!";
        break;
      default:
        echo "Midweek!";
    }
    ```
    

---

### **3. Output Statements in PHP**

PHP provides several functions for outputting data:

#### **`echo`**:

- **`echo`** is used to output one or more strings.
    
    ```php
    echo "Hello, world!";
    ```
    

#### **`print`**:

- **`print`** is similar to **`echo`** but it can only output one string and returns 1.
    
    ```php
    print "Hello, World!";
    ```
    

#### **`printf`**:

- **`printf`** formats the output before displaying it.
    
    ```php
    printf("The number is %d", 10);
    ```
    

---

### **4. String Methods in PHP**

PHP provides various functions to work with strings.

#### **Common String Functions**:

- **`strlen()`**: Returns the length of a string.
    
    ```php
    echo strlen("Hello");  // Outputs 5
    ```
    
- **`strpos()`**: Finds the position of the first occurrence of a substring.
    
    ```php
    echo strpos("Hello, World!", "World");  // Outputs 7
    ```
    
- **`substr()`**: Extracts a portion of a string.
    
    ```php
    echo substr("Hello, World!", 0, 5);  // Outputs Hello
    ```
    
- **`str_replace()`**: Replaces occurrences of a substring with another.
    
    ```php
    echo str_replace("World", "PHP", "Hello, World!");  // Outputs Hello, PHP!
    ```
    
- **`strtoupper()`**: Converts a string to uppercase.
    
    ```php
    echo strtoupper("hello");  // Outputs HELLO
    ```
    
- **`strtolower()`**: Converts a string to lowercase.
    
    ```php
    echo strtolower("HELLO");  // Outputs hello
    ```
    

---

### **5. Arrays in PHP**

Arrays in PHP can be **indexed** (numeric) or **associative** (key-value pairs).

#### **Creating Arrays**:

- **Indexed Array**: Uses numeric indexes.
    
    ```php
    $fruits = array("Apple", "Banana", "Orange");
    ```
    
- **Associative Array**: Uses named keys.
    
    ```php
    $person = array("name" => "John", "age" => 25);
    ```
    

#### **Accessing Array Elements**:

- **Indexed Array**:
    
    ```php
    echo $fruits[0];  // Outputs Apple
    ```
    
- **Associative Array**:
    
    ```php
    echo $person["name"];  // Outputs John
    ```
    

#### **Array Methods**:

- **`count()`**: Returns the number of elements in an array.
    
    ```php
    echo count($fruits);  // Outputs 3
    ```
    
- **`array_push()`**: Adds one or more elements to the end of an array.
    
    ```php
    array_push($fruits, "Grapes");
    ```
    
- **`array_pop()`**: Removes the last element from an array.
    
    ```php
    array_pop($fruits);
    ```
    
- **`in_array()`**: Checks if a value exists in an array.
    
    ```php
    if (in_array("Apple", $fruits)) {
      echo "Apple is in the list!";
    }
    ```
    

#### **Sequential Access**:

- PHP provides the **`foreach`** loop to iterate through arrays.
    
    ```php
    foreach ($fruits as $fruit) {
      echo $fruit . " ";
    }
    ```
    

#### **Sorting Arrays**:

- **`sort()`**: Sorts an indexed array in ascending order.
    
    ```php
    sort($fruits);
    ```
    
- **`asort()`**: Sorts an associative array according to the value.
    
    ```php
    asort($person);
    ```
    
- **`ksort()`**: Sorts an associative array according to the key.
    
    ```php
    ksort($person);
    ```
    

---

### **6. Functions in PHP**

Functions in PHP allow you to encapsulate code into reusable blocks.

#### **Creating a Function**:

- **Syntax**:
    
    ```php
    function functionName() {
      // Code
    }
    ```
    
- **Example**:
    
    ```php
    function greet($name) {
      echo "Hello, " . $name;
    }
    
    greet("John");  // Outputs Hello, John
    ```
    

#### **Returning Values**:

- Functions can return values using the **`return`** keyword.
    
    ```php
    function add($a, $b) {
      return $a + $b;
    }
    
    echo add(5, 3);  // Outputs 8
    ```
    

#### **Variable Scope**:

- **Global Scope**: Variables declared outside functions.
- **Local Scope**: Variables declared inside functions.

You can use the **`global`** keyword to access global variables inside functions.

```php
$x = 10;

function test() {
  global $x;
  echo $x;
}

test();  // Outputs 10
```

---

### **7. Pattern Matching in PHP**

Pattern matching in PHP can be achieved using regular expressions (regex).

#### **Using `preg_match()`**:

- This function searches a string for a pattern and returns a boolean value (true or false).
    
    ```php
    $pattern = "/php/";
    if (preg_match($pattern, "PHP is a popular language")) {
      echo "Match found!";
    }
    ```
    

#### **Using `preg_replace()`**:

- Replaces a pattern in a string with a specified replacement.
    
    ```php
    $pattern = "/world/i";
    $string = "Hello World!";
    echo preg_replace($pattern, "PHP", $string);  // Outputs Hello PHP!
    ```


	---
----
----
# UNIT 04 ENDS HERE ! 
# \>GO TO [UNIT 05](WebD-05.md) 
