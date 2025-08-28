# Control Structures in Java

## The `if` Statement

The **`if` statement** is the most basic decision-making control structure in Java.
It allows a program to **evaluate a condition** (a boolean expression) and execute a block of code **only if the condition is true**.
If the condition evaluates to `false`, the code inside the block is skipped.

```java
if (condition) {
    // statements to execute if condition is true
}
```

* **condition**: must be a boolean expression (`true` or `false`).
* Curly braces `{}` are optional if only one statement is present, but generally used for clarity.

```java
int number = 10;

if (number > 0) {
    System.out.println("The number is positive.");
}

// Ouput: 
// The number is positive.
```
## Variations of `if`

1. **Simple if**
   Executes statements only if the condition is true.

2. **if-else**
   Provides an alternative block if the condition is false.

```java
if (number % 2 == 0) {
    System.out.println("Even");
} else {
    System.out.println("Odd");
}
```

3. **Nested if**
   An `if` statement inside another `if`. Useful for multiple checks.

```java
if (number > 0) {
    if (number < 100) {
        System.out.println("Positive and less than 100");
    }
}
```

4. **if-else-if ladder**
   Used when multiple conditions need to be tested sequentially.

```java
if (marks >= 90) {
    System.out.println("Grade A");
} else if (marks >= 75) {
    System.out.println("Grade B");
} else {
    System.out.println("Grade C");
}
```
Alright, here’s the clean note on **`if-else`** in Java, same structured flow for your vault:

## The `if-else` Statement

The **`if-else` statement** is a fundamental decision-making construct in Java.
It allows the program to choose between two alternative paths:

* If the **condition is true**, the `if` block executes.
* If the **condition is false**, the `else` block executes.

This ensures that one of the two possible branches always runs.

```java
if (condition) {
    // statements if condition is true
} else {
    // statements if condition is false
}
```

```java
// example : 
int age = 18;

if (age >= 18) {
    System.out.println("You are eligible to vote.");
} else {
    System.out.println("You are not eligible to vote.");
}

// output : 
// You are eligible to vote.
```

* Ensures **binary decision-making** (one of two paths is chosen).
* The `else` part is optional; if omitted, the program simply skips when the condition is false.
* Both blocks may contain a single statement or multiple statements enclosed in `{}`.

## The `while` Loop

The **`while` loop** is an *entry-controlled loop* in Java.
It repeatedly executes a block of statements **as long as the given condition is true**.
Because the condition is evaluated *before* entering the loop, it is possible that the loop body may never execute if the condition is false at the start.

```java
while (condition) {
    // statements to be executed
}
```

```java
int i = 1;

while (i <= 5) {
    System.out.println("Count: " + i);
    i++;
}

// Count: 1
// Count: 2
// Count: 3
// Count: 4
// Count: 5
```

* **Entry-controlled:** The condition is checked before execution.
* Executes **zero or more times**, depending on the condition.
* Typically used when the **number of iterations is not fixed** in advance.
* Requires careful update of loop variables to avoid infinite loops.

## The `for` Loop

The **`for` loop** is a *count-controlled loop* in Java.
It is used when the **number of iterations is known in advance**.
Unlike `while`, the `for` loop neatly combines loop initialization, condition-checking, and update in a single line, making the code more concise and readable.

```java
for (initialization; condition; update) {
    // statements to be executed
}
```

* **Initialization:** Sets the starting value(s) of loop control variable(s).
* **Condition:** Checked before each iteration; loop runs only if true.
* **Update:** Changes the control variable(s) after each iteration.

```java
for (int i = 1; i <= 5; i++) {
    System.out.println("Iteration: " + i);
}

// Output: 
// Iteration: 1
// Iteration: 2
// Iteration: 3
// Iteration: 4
// Iteration: 5
```

## The For-Each Loop (Enhanced For Loop)

It is a simplified form of the `for` loop, designed for **traversing arrays and collections** without explicitly using an index.
This makes the code more readable and reduces errors like *off-by-one mistakes*.

```java
for (type variable : arrayOrCollection) {
    // statements using variable
}
```

* **type** → the data type of elements in the array or collection.
* **variable** → a temporary variable that stores each element during iteration.
* **arrayOrCollection** → the data structure being traversed.

### Example: Array Traversal

```java
int[] numbers = {10, 20, 30, 40};

for (int num : numbers) {
    System.out.println(num);
}

// Output 
// 10
// 20
// 30
// 40
```

* Eliminates need for **explicit indexing**.
* Works with both **arrays** and **objects implementing `Iterable`** (e.g., `ArrayList`, `HashSet`).
* Cannot be used for modifying array/collection size during traversal.
* **Read-only** with respect to collection structure (cannot add or remove elements inside it directly).

# Arrays in Java

An **array** in Java is a **collection of elements of the same data type**, stored in contiguous memory locations. Arrays are objects in Java and are used to store **fixed-size sequential data**.
## Array Declaration

Declaring an array means informing the compiler about the **type of elements** and the **array reference variable**.
Two common forms of declaration:

```java
// Style 1 (preferred)
int[] numbers;

// Style 2 (also valid, but less common)
int numbers[];
```
## Array Creation (Memory Allocation)

After declaration, memory must be allocated using the `new` keyword:

```java
numbers = new int[5]; // creates an array of size 5
```
* By default, arrays are filled with **default values**:

## Array Initialization

Initialization means assigning actual values.
It can be done in several ways:

### 1. Static Initialization (at the time of declaration)

```java
int[] numbers = {10, 20, 30, 40, 50};
```

### 2. Dynamic Initialization (assigning later)

```java
int[] numbers = new int[3];
numbers[0] = 100;
numbers[1] = 200;
numbers[2] = 300;
```

### 3. Partial Initialization (rest filled with defaults)

```java
int[] marks = new int[5];
marks[0] = 90;
marks[1] = 85;
// remaining indices will hold 0
```

## Example: Printing an Array

```java
class ArrayDemo {
    public static void main(String[] args) {
        int[] arr = {1, 2, 3, 4, 5};

        for (int i = 0; i < arr.length; i++) {
            System.out.println(arr[i]);
        }
    }
}
```

# Methods in Java

A **method** in Java is a block of code designed to perform a specific task. It promotes **modularity, reusability, and readability** of programs. Methods allow programmers to break large programs into smaller, manageable parts.
## Purpose and Benefits of Methods

* **Modularity** – Code is divided into independent units.
* **Reusability** – A method can be called multiple times without rewriting the same logic.
* **Maintainability** – Easier to debug and update.
* **Readability** – Code structure becomes clear and logical.
* **Abstraction** – The user of a method need not know its internal details.
## General Syntax

```java
returnType methodName(parameterList) {
    // body of method
    return value; // if returnType is not void
}
```

```java
// example 
int add(int a, int b) {
    return a + b;
}
```

## Types of Methods

1. **Predefined (Library) Methods**

   * Already available in Java libraries.
   * Example:

```java
     String s = "hello";
     System.out.println(s.length()); // length() is a predefined method
     ```

2. **User-defined Methods**

   * Created by the programmer for specific tasks.
   
```java
     void greet() {
         System.out.println("Hello, World!");
     }
     ```

# Passing Parameters to Methods in Java

In Java, **parameters** allow values to be passed into a method when it is called. This enables methods to operate on different inputs without rewriting the logic.

```java
returnType methodName(parameterType1 param1, parameterType2 param2, ...) {
    // body
}
```

```java
// example: 
int add(int a, int b) {
    return a + b;
}
```

Here, `a` and `b` are parameters, also called **formal parameters**. When the method is called, values provided are called **arguments**.

## Types of Parameters in Java

### 1. Formal Parameters

* Declared in the method definition.
* Receive values when the method is called.

### 2. Actual Parameters (Arguments)

* Values or variables passed during the method call.
* Example:

  ```java
  int result = add(10, 20);   // 10 and 20 are actual parameters
  ```


## Parameter Passing Mechanism in Java

Java uses **Call by Value** only.

* A copy of the variable’s value is passed to the method.
* Changes made inside the method do not affect the original variable.

```java
class Demo {
    void changeValue(int x) {
        x = x + 10;
        System.out.println("Inside method: " + x);
    }

    public static void main(String[] args) {
        int a = 5;
        Demo d = new Demo();
        d.changeValue(a);
        System.out.println("Outside method: " + a);
    }
}
// output : 
// Inside method: 15  
// Outside method: 5  
```

## Special Case: Objects as Parameters

When an **object** is passed, the reference (memory address) is copied.

* Changes to the object’s fields affect the original object.

```java
class Student {
    String name;
}

class Test {
    void update(Student s) {
        s.name = "Updated Name";
    }

    public static void main(String[] args) {
        Student st = new Student();
        st.name = "Original";
        
        Test t = new Test();
        t.update(st);
        
        System.out.println(st.name); // prints "Updated Name"
    }
}
```

# Sorting and Searching Applications

Sorting and searching are two fundamental operations in computer science. They form the backbone of efficient data processing and are widely used in real-world applications such as databases, search engines, and file management systems.

## Sorting

Sorting is the process of arranging elements in a particular order, typically **ascending** or **descending**.
### Common Sorting Techniques in Java

1. **Bubble Sort** – compares adjacent elements and swaps them until the list is sorted.
2. **Selection Sort** – repeatedly selects the smallest (or largest) element and places it in the correct position.
3. **Insertion Sort** – builds the sorted portion step by step by inserting elements in the correct position.
4. **Merge Sort** – a divide-and-conquer algorithm that splits, sorts, and merges arrays.
5. **Quick Sort** – selects a pivot and partitions elements around it, then recursively sorts sub-arrays.
6. **Built-in Sort** – Java provides `Arrays.sort()` and `Collections.sort()` for optimized sorting.

```java
import java.util.Arrays;
class SortExample {
    public static void main(String[] args) {
        int[] arr = {5, 2, 8, 1, 9};
        Arrays.sort(arr);  // ascending order
        System.out.println(Arrays.toString(arr));
    }
}
```

## Searching

Searching is the process of finding the location of a specific element in a collection.

### Common Searching Techniques in Java

1. **Linear Search**

   * Checks elements one by one.
   * Simple but inefficient for large data.
   * Time complexity: O(n).

[]()2. **Binary Search**

   * Works on **sorted arrays**.
   * Divides the array repeatedly to locate the element.
   * Time complexity: O(log n).

### Example: Binary Search

```java
import java.util.Arrays;
class SearchExample {
    public static void main(String[] args) {
        int[] arr = {1, 3, 5, 7, 9, 11};
        int index = Arrays.binarySearch(arr, 7);
        System.out.println("Element found at index: " + index);
    }
}
```


# Strings

A **String** in Java is a sequence of characters. Unlike primitive data types, `String` is a **class** in the `java.lang` package. Strings are widely used to store and manipulate text.

## Ways to Initialize Strings

### 1. **Using String Literal**

* The simplest way.
* Stored in the **String Constant Pool** (SCP).
* Saves memory by reusing existing objects.

```java
class StringLiteral {
    public static void main(String[] args) {
        String s1 = "Hello";   // String literal
        String s2 = "Hello";   // Reuses the same object from SCP
        System.out.println(s1 == s2);  // true (same reference)
    }
}
```

### 2. **Using `new` Keyword**

* Creates a new `String` object in the **heap memory**, even if the same value exists in the SCP.

```java
class StringNew {
    public static void main(String[] args) {
        String s1 = new String("Hello");  
        String s2 = new String("Hello");  
        System.out.println(s1 == s2);  // false (different objects)
    }
}
```


# String Manipulation

**String manipulation** refers to the process of modifying, analyzing, or extracting information from strings. Since Java strings are **immutable**, every manipulation operation that seems to “change” a string actually creates a **new string object**.

## Common String Manipulation Operations

### 1. **Concatenation**

Joining two or more strings into one.

* Using `+` operator
* Using `concat()` method

```java
String s1 = "Hello";
String s2 = "World";
String s3 = s1 + " " + s2;          // Hello World
String s4 = s1.concat(" ").concat(s2);  // Hello World
```

### 2. **Case Conversion**

```java
String str = "Java Programming";
System.out.println(str.toUpperCase()); // JAVA PROGRAMMING
System.out.println(str.toLowerCase()); // java programming
```

### 3. **Substring Extraction**

```java
String str = "Programming";
System.out.println(str.substring(0, 6)); // Progra
System.out.println(str.substring(3));    // gramming
```
### 4. **Character Access**

```java
String str = "Hello";
char c = str.charAt(1);  // 'e'
```

### 5. **Length of String**

```java
String str = "OpenAI";
System.out.println(str.length());  // 6
```

### 6. **Searching Within Strings**

* `indexOf()` → gives first occurrence index.
* `lastIndexOf()` → gives last occurrence index.
* `contains()` → checks presence of a substring.

```java
String str = "Java is powerful";
System.out.println(str.indexOf("is"));   // 5
System.out.println(str.contains("power"));// true
```

### 7. **Replacing Characters or Substrings**

```java
String str = "Java is hard";
String replaced = str.replace("hard", "easy");
System.out.println(replaced); // Java is easy
```

### 8. **Trimming White Spaces**

```java
String str = "   spaced out   ";
System.out.println(str.trim()); // "spaced out"
```

### 9. **Splitting and Joining**

```java
String str = "apple,banana,grape";
String[] fruits = str.split(",");
for(String f : fruits) {
    System.out.println(f);
}
```

### 10. **Comparison**

* `equals()` → checks content.
* `equalsIgnoreCase()` → ignores case.
* `compareTo()` → lexicographical comparison.

```java
String a = "Java";
String b = "java";
System.out.println(a.equals(b));          // false
System.out.println(a.equalsIgnoreCase(b));// true
System.out.println(a.compareTo(b));       // -32
```

# StringBuffer Class

* `StringBuffer` is a **mutable sequence of characters** in Java.
* Unlike `String` (immutable), a `StringBuffer` object can be **modified without creating a new object**.
* It is **synchronized** → thread-safe (can be safely used in multithreaded environments).

## Declaration and Initialization

```java
StringBuffer sb1 = new StringBuffer();               // empty buffer, default capacity = 16
StringBuffer sb2 = new StringBuffer("Hello");        // initialized with string
StringBuffer sb3 = new StringBuffer(50);             // capacity of 50 characters
```

## Important Methods of StringBuffer

### 1. **append()**

Adds text at the end of buffer.

```java
StringBuffer sb = new StringBuffer("Java");
sb.append(" Programming");
System.out.println(sb); // Java Programming
```

### 2. **insert()**

Inserts text at a specific position.

```java
StringBuffer sb = new StringBuffer("Java");
sb.insert(4, " Language");
System.out.println(sb); // Java Language
```

### 3. **replace()**

Replaces characters from start index to end index (exclusive).

```java
StringBuffer sb = new StringBuffer("Hello World");
sb.replace(6, 11, "Java");
System.out.println(sb); // Hello Java
```

### 4. **delete()**

Deletes a portion of characters.

```java
StringBuffer sb = new StringBuffer("Programming");
sb.delete(3, 6);
System.out.println(sb); // Proramming
```

### 5. **reverse()**

Reverses the character sequence.

```java
StringBuffer sb = new StringBuffer("Hello");
System.out.println(sb.reverse()); // olleH
```

### 6. **capacity() and ensureCapacity()**

* `capacity()` → returns buffer capacity.
* `ensureCapacity(n)` → ensures capacity is at least `n`.

```java
StringBuffer sb = new StringBuffer();
System.out.println(sb.capacity()); // 16 (default)
sb.ensureCapacity(50);
System.out.println(sb.capacity()); // ≥50
```

### 7. **charAt(), setCharAt()**

```java
StringBuffer sb = new StringBuffer("Java");
System.out.println(sb.charAt(2)); // v
sb.setCharAt(2, 'X');
System.out.println(sb); // JaXa
```

### 8. **length(), setLength()**

```java
StringBuffer sb = new StringBuffer("Hello");
System.out.println(sb.length()); // 5
sb.setLength(3);
System.out.println(sb); // Hel
```

## Difference Between **String**, **StringBuffer**, and **StringBuilder**

| Feature       | String          | StringBuffer         | StringBuilder |
| ------------- | --------------- | -------------------- | ------------- |
| Mutability    | Immutable       | Mutable              | Mutable       |
| Thread Safety | Yes (Immutable) | Yes (Synchronized)   | No            |
| Performance   | Slower          | Slower (thread-safe) | Faster        |
