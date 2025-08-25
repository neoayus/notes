# Introduction to Java

Java is a **high-level, object-oriented, platform-independent programming language** developed by *James Gosling* and his team at Sun Microsystems in **1995** (now owned by Oracle). It was designed with the philosophy of *“Write Once, Run Anywhere” (WORA)*, meaning compiled Java code can run on any device or operating system that has a Java Virtual Machine (JVM).

Java combines the power of **object-oriented principles** with the **portability of platform independence**, making it one of the most widely used languages in software development.

---

## Features of Java

* **Simple** → Syntax is easy to learn (similar to C/C++ but without complexities like pointers).
* **Object-Oriented** → Based on classes, objects, and principles like inheritance, encapsulation, and polymorphism.
* **Platform-Independent** → Compiled Java code runs on any system via JVM.
* **Secure** → Provides features like bytecode verification, exception handling, and no use of explicit pointers.
* **Robust** → Strong memory management, garbage collection, and exception handling.
* **Multithreaded** → Supports execution of multiple threads simultaneously.
* **Distributed** → Supports networking and remote method invocation (RMI).
* **High Performance** → Uses *Just-In-Time (JIT) compiler* for faster execution.

---

## Java Program Structure

A basic Java program consists of **class declaration**, **main method**, and **statements**.

```java
class HelloWorld {
    public static void main(String[] args) {
        System.out.println("Hello, World!");
    }
}
```

### Explanation:

* `class HelloWorld` → Class declaration (same as the program name)
* `public static void main(String[] args)` → Entry point of execution.
* `System.out.println(...)` → Statement to print output to the console.

---
## Java Execution Process

1. **Write Code** → Java source code is written in `.java` files.
2. **Compile** → Compiler (`javac`) converts source code into **bytecode** (`.class` files).
3. **Run** → JVM interprets bytecode and executes it on the underlying machine.

**Flow:**
`Source Code (.java)` → `Compiler (javac)` → `Bytecode (.class)` → `JVM` → Output

---

## Applications of Java

* **Desktop Applications** → IDEs like Eclipse, IntelliJ.
* **Web Applications** → Server-side development using Java Servlets, JSP, Spring.
* **Mobile Applications** → Android apps are largely built using Java.
* **Enterprise Systems** → Banking, insurance, ERP systems.
* **Scientific Applications** → Simulation, big data, and research tools.

---
## Advantages of Java

* Platform independence (WORA).
* Rich standard library (Java API).
* Strong community support.
* Easy to learn and widely used in academia and industry.
* Scalable from small applications to large enterprise systems.

--- 
# Structure of a Java Program

A Java program is a **collection of classes and objects** that interact with
each other. Every Java program follows a certain format consisting of **class declarations, methods, and statements**. The **`main()` method** acts as the entry point of the program.

---

## General Structure

```java
// 1. Package statement (optional)
package mypackage;

// 2. Import statements (optional)
import java.util.Scanner;

// 3. Class declaration
public class Example {

    // 4. Variables / fields
    int number;

    // 5. Methods
    void display() {
        System.out.println("Number: " + number);
    }

    // 6. main() method → entry point of program
    public static void main(String[] args) {
        Example obj = new Example(); // object creation
        obj.number = 10;             // assigning value
        obj.display();               // method call
    }
}
```

---

## Components of a Java Program

1. **Package Statement (optional)**

   * Defines a group of related classes and interfaces.
   * Example: `package studentdata;`

2. **Import Statement (optional)**

   * Used to access predefined Java classes (like Scanner, Arrays, etc.).
   * Example: `import java.util.Scanner;`

3. **Class Declaration**

   * Every program must have at least one class.
   * Syntax: `class ClassName { ... }`

4. **Fields (Variables)**

   * Represent the state or data of a class.
   * Example: `int age; String name;`

5. **Methods**

   * Define behavior or functionality of a class.
   * Example: `void study() { ... }`

6. **main() Method**

   * Starting point of execution.
   * Syntax:
#### Key Points About `main()` Method

* `public` → Accessible from anywhere.
* `static` → Can run without creating an object.
* `void` → Does not return any value.
* `String[] args` → Stores command-line arguments.

---
# Creating, Compilation, and Running Java Programs

Java programs follow a systematic process: **writing source code → compiling → generating bytecode → executing through JVM (Java Virtual Machine).**
This ensures **platform independence** (WORA: *Write Once, Run Anywhere*).

---
## Steps to Create, Compile, and Run a Java Program

### 1. Creating a Java Program

* Java code is written in a **text editor** (e.g., Notepad, VS Code, IntelliJ).
* File must be saved with the **`.java` extension**, and the filename should match the public class name.

```java
// HelloWorld.java
class HelloWorld {
    public static void main(String[] args) {
        System.out.println("Hello, World!");
    }
}
```

---

### 2. Compilation (Using Java Compiler: `javac`)

* The Java compiler translates source code (`.java`) into **bytecode** (`.class`).
* Bytecode is platform-independent and can run on any machine with JVM.

**Command:**

```bash
javac HelloWorld.java
```

* If successful, it creates: `HelloWorld.class`

---

### 3. Running the Program (Using Java Interpreter: `java`)

* The Java interpreter (JVM) executes the **bytecode**.
* The Just-In-Time (JIT) compiler inside JVM converts bytecode into machine code for execution.

**Command:**

```bash
java HelloWorld
```

**Output:**

```
Hello, World!
```

⚠️ Note: While running, we do **not** include `.class` or `.java` extension. Only the class name is used.

**Diagram:**
`Program.java → (javac) → Program.class (bytecode) → (java interpreter/JVM) → Output`

---
## Role of Interpreter (JVM)

* Reads and executes bytecode instructions.
* Provides **platform independence** (same `.class` runs on Windows, Linux, Mac).
* Performs memory management via **Garbage Collection**.
* Ensures program **security** by verifying bytecode.

# Constants, Literals, Keywords, Variables, Identifiers, and Data Types

## 1. Constants

A **constant** is a value that cannot be changed during program execution. In Java, constants are declared using the `final` keyword.

```java
final double PI = 3.14159;
```

* Once assigned, the value of `PI` cannot be modified.
* Constants improve **readability** and **maintainability**.

---

## 2. Literals

**Literals** in java is a fixed constant value directly written in the source code. 
When he compiler counters a literal, it creates the appropriate value in memory without further computation. 
### Types of Literals:

#### **Integer Literals** → `10`, `-45`
Used for whole numbers (no fractional part). 
+ default type : int 
+ can also be stored in long if suffixed with L or 1.
```java
int a = 10;      // decimal literal
int b = 0x1A;    // hexadecimal (prefix 0x)
int c = 012;     // octal (prefix 0)
int d = 0b1010;  // binary (prefix 0b, Java 7+)
long e = 1000L;  // long literal
```

#### **Floating-point Literals** → `3.14`, `2.5e3`
Used for decimal numbers (fractional part). 
+ Default type : double 
+ for float, add suffix F or f. 
```java 
double x = 12.34;   // double literal
float y = 12.34F;   // float literal
```
#### **Character Literals** → `'A'`, `'\n'`
A single character enclosed in single quotes 
+ internally stored as Unicode values. 
+ Can also be expressed using escape sequence 
```java 
char c1 = 'A';  // simple character 
char c2 = '\n'; // newline escape
char c3 = '\u0041' // unicode respresentation of 'A' 
```
#### **String Literals** → `"Hello Java"`
A sequence of characters enclosed in double quotes. 
+ Strings in Java are objects of class String. 
+ They are immutable. 

```java
 Sring s = "Hellow, World !"
```
#### **Boolean Literals** → `true`, `false`
Only two possible values : true and false. 
+ Used in conditional expressions and logical operations. 
```java
boolean flag = true ; 
```

#### **Null Literal** → `null`
+ Null represents the absence of any object reference. 
+ Can only be assigned to reference types, not primitive types. 

---
## 3. Keywords

**Keywords** are reserved words in Java that have predefined meanings and cannot be used as identifiers.

Examples:
`class`, `public`, `static`, `void`, `int`, `if`, `else`, `while`, `return`, `final`

⚠️ Java has around **50+ keywords** (e.g., `abstract`, `extends`, `implements`, `super`, `this`, `try`, `catch`).

---

## 4. Variables

A **variable** is a named memory location that stores a value, which can change during program execution.

### Syntax:

```java
dataType variableName = value;
```

### Example:

```java
int number = 25;    // integer variable
double salary = 55000.50; // floating-point variable
```

### Types of Variables in Java:

* **Local Variables** → Declared inside methods, exist only within that block.
* **Instance Variables** → Declared inside a class but outside methods, specific to each object.
* **Static Variables** → Declared with `static` keyword, shared among all objects of a class.

---

## 5. Identifiers

**Identifiers** are the names used for variables, classes, methods, and objects.

### Rules for Identifiers:

* Must begin with a **letter, `$`, or `_`.**
* Cannot start with a digit.
* Cannot use Java **keywords**.
* Case-sensitive.
* Should be meaningful.

**Valid Identifiers:** `studentName`, `_count`, `sum1`
**Invalid Identifiers:** `1value`, `class`, `student-name`

---

## 6. Data Types

Java is a **strongly typed language**, meaning every variable must be declared with a data type.

### Categories of Data Types:

#### (a) Primitive Data Types

* **Numeric**

  * Integer → `byte`, `short`, `int`, `long`
  * Floating → `float`, `double`
* **Non-numeric**

  * Character → `char`
  * Boolean → `boolean`

#### (b) Non-Primitive Data Types

* **Strings**, **Arrays**, **Classes**, **Interfaces**

### Example:

```java
int age = 20;          // integer
float marks = 85.6f;   // floating-point
boolean isPass = true; // boolean
char grade = 'A';      // character
String name = "Riya";  // non-primitive (class type)
```