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

# Introduction to OOP

Object-Oriented Programming (OOP) is a programming paradigm based on the concept of **objects**, which combine **data** (fields, attributes) and **behavior** (methods, functions) into a single modular unit. Unlike procedural programming, which focuses on step-by-step instructions, OOP models real-world entities and their interactions, making programs more **modular, reusable, and maintainable**.

## Key Concepts of OOP

### 1. Class and Object

* **Class**: A blueprint or template for creating objects. It defines attributes (variables) and methods (functions).
* **Object**: An instance of a class that holds actual values and can perform actions defined by the class.

```java
class Student {
    String name;
    int age;

    void display() {
        System.out.println(name + " is " + age + " years old.");
    }
}

public class Main {
    public static void main(String[] args) {
        Student s1 = new Student();  // object creation
        s1.name = "Aman";
        s1.age = 20;
        s1.display();
    }
}
```

### 2. Encapsulation

Encapsulation means **wrapping data and methods together** into a single unit (class). It restricts direct access to data and ensures controlled interaction through methods (getters and setters).
This promotes **data security and modular design**.

### 3. Inheritance

Inheritance allows a class to acquire properties and behaviors of another class.

* Promotes **code reusability**.
* Helps in building a **hierarchical structure**.

```java
class Vehicle {
    void run() {
        System.out.println("Vehicle is running");
    }
}

class Car extends Vehicle {
    void run() {
        System.out.println("Car is running");
    }
}
```

### 4. Polymorphism

Polymorphism means "many forms." It allows the same method or operation to behave differently depending on context.

* **Compile-time (Method Overloading)**: Same method name but different parameter list.
* **Runtime (Method Overriding)**: Subclass provides a specific implementation of a method already defined in parent class.

### 5. Abstraction

Abstraction hides the **implementation details** and exposes only the essential features of an object.

* Achieved using **abstract classes** or **interfaces**.
* Encourages **flexibility and scalability** in large systems.

---

## Advantages of OOP

* **Modularity**: Programs are divided into classes and objects.
* **Reusability**: Code can be reused through inheritance.
* **Maintainability**: Encapsulation makes modifications easier.
* **Flexibility**: Polymorphism allows dynamic method handling.
* **Security**: Encapsulation and abstraction protect data.

---

# Encapsulation

Encapsulation is one of the **fundamental principles of Object-Oriented Programming (OOP)**. It refers to the practice of **binding data (variables) and methods (functions) that operate on that data into a single unit (class)**. At the same time, it **restricts direct access** to the internal state of objects, ensuring that interaction takes place only through well-defined methods.

In simple words, encapsulation means **“data hiding and controlled access”**.

## Features of Encapsulation

* **Data Hiding**: Internal details of a class are hidden from outside. Only necessary information is exposed.
* **Controlled Access**: Fields are usually declared `private`, and access is provided through `public` methods (getters and setters).
* **Security**: Prevents unauthorized modification of sensitive data.
* **Modularity**: Each class encapsulates its own data and operations, making the system organized.

## Example in Java

```java
class BankAccount {
    // private data members
    private String accountHolder;
    private double balance;

    // constructor
    public BankAccount(String accountHolder, double balance) {
        this.accountHolder = accountHolder;
        this.balance = balance;
    }

    // getter
    public double getBalance() {
        return balance;
    }

    // setter with condition
    public void deposit(double amount) {
        if (amount > 0) {
            balance += amount;
        }
    }

    public void withdraw(double amount) {
        if (amount > 0 && amount <= balance) {
            balance -= amount;
        }
    }
}

public class Main {
    public static void main(String[] args) {
        BankAccount acc = new BankAccount("Aman", 1000);
        acc.deposit(500);
        acc.withdraw(200);
        System.out.println("Balance: " + acc.getBalance());
    }
}
```

## Benefits of Encapsulation

* **Improved Security**: Sensitive data cannot be accessed directly.
* **Maintainability**: Internal implementation can change without affecting external code.
* **Flexibility**: Validation logic can be added in setters.
* **Reusability**: Classes become modular and reusable in other programs.

## Real-World Analogy

A **capsule** in medicine contains powder inside but exposes only the outer shell. Similarly, in programming, the data is hidden inside the class, and only necessary interfaces are exposed.

---
# Abstraction

Abstraction is a core principle of **Object-Oriented Programming (OOP)** that focuses on **hiding implementation details** and showing only the **essential features** of an object. It allows programmers to work with high-level concepts without worrying about the low-level complexities.

In simple terms, **abstraction answers “what an object does” rather than “how it does it.”**

## Features of Abstraction

* **Hides implementation details** and exposes only necessary functionality.
* Achieved in Java using:

  * **Abstract Classes** → Can contain both abstract (unimplemented) and concrete (implemented) methods.
  * **Interfaces** → Define a contract of methods that a class must implement.
* Encourages **modular and flexible system design**.
* Helps in managing **large, complex codebases** by separating definition from implementation.

### Using Abstract Class

```java
abstract class Vehicle {
    abstract void start();  // abstract method (no body)
    
    void fuel() {          // concrete method
        System.out.println("Vehicle needs fuel.");
    }
}

class Car extends Vehicle {
    void start() {
        System.out.println("Car starts with a key.");
    }
}
```

### Using Interface

```java
interface Payment {
    void pay(double amount);
}

class CreditCardPayment implements Payment {
    public void pay(double amount) {
        System.out.println("Paid " + amount + " using Credit Card.");
    }
}
```

## Real-World Analogy

* **ATM Machine**: Users only see the interface (insert card, enter PIN, withdraw cash) but do not see the internal mechanisms of transaction processing.
* **Car Driving**: A driver uses the steering, brakes, and accelerator without knowing the internal working of the engine.

---

# Inheritance

Inheritance is a **fundamental concept of OOP** that allows a class (called the *child* or *subclass*) to **acquire properties and behaviors of another class** (called the *parent* or *superclass*).

It promotes **code reusability, modularity, and hierarchical relationships** between classes. Instead of rewriting code, a subclass can extend an existing class and either **reuse, override, or add new features**.

## Key Points

* **Superclass (Parent class):** The class whose properties and methods are inherited.
* **Subclass (Child class):** The class that inherits from another class.
* **`extends` keyword (Java):** Used to establish inheritance.
* **Code Reusability:** Shared features can be written once in the superclass.
* **Polymorphism Support:** Subclasses can override methods for different behavior.

## Example in Java

```java
// Parent class
class Vehicle {
    String brand = "Generic Vehicle";
    
    void run() {
        System.out.println("Vehicle is running...");
    }
}

// Child class
class Car extends Vehicle {
    String model = "Sedan";
    
    void honk() {
        System.out.println("Car is honking...");
    }
}

public class Main {
    public static void main(String[] args) {
        Car c = new Car();
        c.run();          // inherited from Vehicle
        c.honk();         // defined in Car
        System.out.println(c.brand + " " + c.model);
    }
}
```

## Types of Inheritance in Java

* **Single Inheritance** → One class inherits another.
* **Multilevel Inheritance** → A subclass becomes a superclass for another class.
* **Hierarchical Inheritance** → Multiple classes inherit from a single superclass.

⚠️ **Note**: Java does **not support multiple inheritance** with classes (to avoid ambiguity). Instead, multiple inheritance is achieved using **interfaces**.

## Real-World Analogy

* **Family hierarchy**: A child inherits characteristics from parents, but can also have unique traits.
* **Biological species**: Mammals inherit traits from Animals, but each mammal type (like Dog, Cat, Human) has its own specific behavior.

## Advantages of Inheritance

* **Code Reusability** → Common functionality is defined once.
* **Faster Development** → New classes can be created quickly by reusing existing ones.
* **Maintainability** → Changes in the superclass automatically reflect in subclasses.
* **Extensibility** → New features can be easily added to subclasses.

# Classes

A **class** in Java is a **blueprint or template** from which objects are created. It defines the **structure** (data members/fields) and **behavior** (methods/functions) of objects.

In Object-Oriented Programming (OOP), a class is the **fundamental building block** because it provides the mechanism to encapsulate **data** and **methods** together in a modular unit.

## Characteristics of a Class

* **Data Members (Fields):** Variables that hold the state of an object.
* **Methods (Functions):** Define the behavior or operations an object can perform.
* **Access Modifiers:** Control visibility (e.g., `public`, `private`, `protected`).
* **Constructors:** Special methods used to initialize objects.
* **Objects:** Instances created from a class.

```java
class Student {
    // data members (fields)
    String name;
    int age;

    // constructor
    Student(String n, int a) {
        name = n;
        age = a;
    }

    // method (behavior)
    void display() {
        System.out.println(name + " is " + age + " years old.");
    }
}

public class Main {
    public static void main(String[] args) {
        // creating objects
        Student s1 = new Student("Aman", 20);
        Student s2 = new Student("Riya", 19);

        // calling methods
        s1.display();
        s2.display();
    }
}
```

## Types of Classes in Java

* **Concrete Class** → A normal class with complete implementation.
* **Abstract Class** → A class that may contain abstract methods (unimplemented). Cannot be instantiated directly.
* **Final Class** → A class that cannot be inherited. Declared using `final`.
* **Inner Class** → A class defined within another class.

## Real-World Analogy

* Think of a **class as a house blueprint**. It defines how the house will look (rooms, doors, windows), but it is not a real house.
* **Objects** are the actual houses built using that blueprint.

## Advantages of Using Classes

* **Modularity**: Code is organized into logical units.
* **Reusability**: The same class can create multiple objects.
* **Encapsulation**: Data and methods are bundled together.
* **Abstraction Support**: Complex systems can be simplified.

# Objects

An **object** is a **real-world entity** or an **instance of a class**. While a class is only a blueprint, objects are the actual runtime entities that hold **data (state)** and perform **operations (behavior)** defined in the class.

Objects are the foundation of Object-Oriented Programming, as they model real-world things such as a *student, car, bank account,* or *employee*.

## Characteristics of an Object

* **Identity** → Each object is unique and has its own reference in memory.
* **State** → The data/values stored in its fields (variables).
* **Behavior** → The methods or functions that define what the object can do.

```java
class Student {
    String name;
    int age;

    // constructor
    Student(String n, int a) {
        name = n;
        age = a;
    }

    // method
    void display() {
        System.out.println(name + " is " + age + " years old.");
    }
}

public class Main {
    public static void main(String[] args) {
        // creating objects (instances of Student class)
        Student s1 = new Student("Aman", 20);
        Student s2 = new Student("Riya", 19);

        // using object methods
        s1.display();
        s2.display();
    }
}
```

## How Objects are Created in Java

1. **Using `new` keyword** (most common):

   ```java
   Student s = new Student("Rahul", 21);
   ```
2. **Using `newInstance()` method** (reflection).
3. **Using object cloning**.
4. **Using deserialization** (reading from a file or stream).

## Real-World Analogy

* **Class = Car design (blueprint)**
* **Object = Actual car built from that design**.
  Each car (object) may have different colors, speeds, or features, but they all follow the same blueprint (class).
  
## Advantages of Objects

* Represent **real-world entities** in programming.
* Enable **code reuse** (multiple objects from the same class).
* Provide **modularity** and make code **organized and maintainable**.
* Support **interaction** between different objects in large systems.