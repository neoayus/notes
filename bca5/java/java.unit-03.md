# Classes and Objects
## Class Variables

A **class variable** in Java is a variable that belongs to the class rather than to any specific instance (object) of that class. Such variables are declared using the keyword **`static`** inside a class but outside any method, constructor, or block.

They are also called **static variables** because they are allocated memory only once, at the time of class loading. All objects of the class share the same copy of a class variable.


## Characteristics of Class Variables

- **Shared among objects**: All instances of a class use the same variable.
- **Memory allocation**: Memory is allocated only once, at class loading time.
- **Access**: Can be accessed using the class name (e.g., `ClassName.variableName`) or through an object reference.
- **Lifetime**: Remains in memory for the entire duration of the program.
- **Storage location**: Stored in the _method area_ (part of JVM memory).

```java
class Example {
    static int count = 0;  // class variable

    void increment() {
        count++;
    }
}
```

### Example: Shared Nature of Class Variables

```java
class Student {
    String name;             // instance variable
    static String college = "ABC College";  // class variable

    Student(String n) {
        name = n;
    }

    void display() {
        System.out.println(name + " studies in " + college);
    }

    public static void main(String[] args) {
        Student s1 = new Student("Rahul");
        Student s2 = new Student("Priya");

        s1.display();
        s2.display();

        // Changing the class variable through one object
        s1.college = "XYZ University";

        s1.display();
        s2.display();  // change reflects for all objects
    }
}

// output 
// Rahul studies in ABC College
// Priya studies in ABC College
// Rahul studies in XYZ University
// Priya studies in XYZ University
```

## Types of Variables in Java

In Java, variables can be categorized into three main types depending on **where they are declared** and **how long they live**:

1. **Local Variables**
2. **Instance Variables**
3. **Class Variables (Static Variables)**

### 1. Local Variables

* Declared **inside methods, constructors, or blocks**.
* Created when the method is invoked and destroyed once it ends.
* Stored in the **stack memory**.
* **Must be initialized** before use (Java does not assign default values to local variables).

```java
class Example {
    void show() {
        int x = 10;  // local variable
        System.out.println("Local variable: " + x);
    }
}
```

### 2. Instance Variables

* Declared **inside a class but outside methods, constructors, or blocks**.
* Belong to **individual objects** (each object has its own copy).
* Stored in the **heap memory** as part of the object.
* JVM provides **default values** if not initialized (e.g., 0 for int, null for objects).
* Accessed through object references.

```java
class Student {
    String name;   // instance variable
    int age;       // instance variable

    void display() {
        System.out.println("Name: " + name + ", Age: " + age);
    }
}
```

### 3. Class Variables (Static Variables)

* Declared using the **`static`** keyword inside a class, but outside any method.
* Shared by all objects of the class (only one copy exists).
* Memory allocated **once at class loading time**.
* Can be accessed using **class name** directly.

```java
class Student {
    String name;               // instance variable
    static String college = "ABC College";  // class variable

    Student(String n) {
        name = n;
    }

    void display() {
        System.out.println(name + " studies at " + college);
    }
}
```

### Summary 

| Type of Variable   | Declared In                          | Memory Location | Lifetime                | Default Value       | Scope                          |
| ------------------ | ------------------------------------ | --------------- | ----------------------- | ------------------- | ------------------------------ |
| **Local**          | Inside method, constructor, or block | Stack           | During method execution | Must be initialized | Limited to block/method        |
| **Instance**       | Inside class, outside methods        | Heap            | Till object is alive    | Given by JVM        | Accessible through object      |
| **Class (Static)** | Inside class, with `static` keyword  | Method Area     | Entire program          | Given by JVM        | Accessible via class or object |

# Constructors in Java

A **constructor** in Java is a special method used to **initialize objects**.

* Its name must be the **same as the class name**.
* It **does not have a return type** (not even `void`).
* Called automatically when an object is created using `new`.

```java
class Student {
    String name;
    int age;

    // Constructor
    Student(String n, int a) {
        name = n;
        age = a;
    }

    void display() {
        System.out.println(name + " is " + age + " years old");
    }
}

class Main {
    public static void main(String[] args) {
        Student s1 = new Student("Amit", 20); // constructor invoked
        s1.display();
    }
}
```

## Types of Constructors

### 1. Default Constructor

* Provided by the compiler if no constructor is explicitly defined.
* Takes **no parameters**.
* Initializes variables with **default values**.

```java
class Car {
    String brand;
    int year;
    
    // No constructor defined -> compiler provides default constructor
    
    void show() {
        System.out.println("Brand: " + brand + ", Year: " + year);
    }
}

class Main {
    public static void main(String[] args) {
        Car c1 = new Car(); // default constructor invoked
        c1.show(); // brand=null, year=0
    }
}
```

### 2. No-Argument Constructor (Explicit)

* A constructor explicitly written with **no parameters**.
* Different from compiler’s default constructor because it can include **custom initialization**.

```java
class Book {
    String title;
    
    // No-argument constructor
    Book() {
        title = "Unknown";
    }
    
    void show() {
        System.out.println("Title: " + title);
    }
}

class Main {
    public static void main(String[] args) {
        Book b1 = new Book(); 
        b1.show(); // Title: Unknown
    }
}
```

### 3. Parameterized Constructor

* Accepts **arguments** to initialize object properties with specific values.

```java
class Employee {
    String name;
    int id;

    // Parameterized constructor
    Employee(String n, int i) {
        name = n;
        id = i;
    }

    void display() {
        System.out.println("Name: " + name + ", ID: " + id);
    }
}

class Main {
    public static void main(String[] args) {
        Employee e1 = new Employee("Riya", 101);
        Employee e2 = new Employee("Arjun", 102);
        e1.display();
        e2.display();
    }
}
```

### 4. Copy Constructor (User-Defined)

* Java does not have a built-in copy constructor like C++, but we can **create one manually** to copy values from one object to another.

```java
class Student {
    String name;
    int age;

    // Parameterized constructor
    Student(String n, int a) {
        name = n;
        age = a;
    }

    // Copy constructor
    Student(Student s) {
        name = s.name;
        age = s.age;
    }

    void display() {
        System.out.println(name + " - " + age);
    }
}

class Main {
    public static void main(String[] args) {
        Student s1 = new Student("Kiran", 21);
        Student s2 = new Student(s1); // copy constructor
        s1.display();
        s2.display();
    }
}
```

## Visibility Labels (Access Modifiers): `public`, `private`, `protected`

In Java, **access modifiers** (also called *visibility labels*) define the **scope of accessibility** of classes, methods, and variables.
They control **who can see or use** a particular member of a class.

---

### 1. `public`

* Accessible **from anywhere** in the program.
* Can be accessed by:

  * Same class
  * Same package
  * Subclasses
  * Different packages

```java
class Student {
    public String name = "Ravi";  // public variable
    
    public void showName() {      // public method
        System.out.println(name);
    }
}

class Main {
    public static void main(String[] args) {
        Student s1 = new Student();
        System.out.println(s1.name);  // Accessible
        s1.showName();                // Accessible
    }
}
```

### 2. `private`

* Accessible **only within the same class**.
* Not accessible from outside the class, even by subclasses.
* Usually used for **data hiding** (encapsulation).

```java
class Account {
    private double balance;  // private variable

    // public method to access private data
    public void setBalance(double amount) {
        balance = amount;
    }

    public double getBalance() {
        return balance;
    }
}

class Main {
    public static void main(String[] args) {
        Account acc = new Account();
        // System.out.println(acc.balance); // ❌ Error: balance is private
        acc.setBalance(1000);
        System.out.println(acc.getBalance()); // ✅ Access through method
    }
}
```

### 3. `protected`

* Accessible within:

  * Same class
  * Same package
  * Subclasses (even in different packages, through inheritance)
* More open than `private`, but less open than `public`.

**Example:**

```java
class Person {
    protected String name = "Amit";  // protected variable
}

class Student extends Person {
    public void showName() {
        System.out.println("Student Name: " + name);  // Accessible via inheritance
    }
}

class Main {
    public static void main(String[] args) {
        Student s1 = new Student();
        s1.showName(); // ✅ Accessible inside subclass
        // System.out.println(s1.name); // ❌ Error: name not accessible directly
    }
}
```


## **Super Class**

### 🔹 What is a Superclass?

* In **Java OOP**, a **superclass** is the **parent class** from which another class (called the **subclass**) inherits.
* It defines **common properties and behaviors** that can be shared by multiple subclasses.
* The keyword **`extends`** is used to inherit a superclass.

```java
// Superclass
class Animal {
    String name;

    public void eat() {
        System.out.println(name + " is eating.");
    }
}

// Subclass
class Dog extends Animal {
    public void bark() {
        System.out.println(name + " is barking.");
    }
}

class Main {
    public static void main(String[] args) {
        Dog d = new Dog();
        d.name = "Tommy";
        d.eat();   // inherited from Animal (Superclass)
        d.bark();  // defined in Dog (Subclass)
    }
}

/* Output! 
Tommy is eating.
Tommy is barking.
*/ 

```

###  Characteristics of a Superclass

1. **Code Reusability** → Common attributes & methods are defined once in the superclass.
2. **Inheritance** → Subclass acquires fields & methods of the superclass.
3. **Polymorphism** → A subclass can override superclass methods.
4. **Access Modifiers matter** →

   * `public` & `protected` members → accessible in subclass.
   * `private` members → **not accessible** directly in subclass.

###  Using `super` keyword with Superclass

The `super` keyword is used to:

1. **Access superclass constructor**
2. **Access superclass methods**
3. **Access superclass variables (if hidden by subclass variable)**

```java
class Animal {
    String name = "Animal";

    Animal() {
        System.out.println("Animal constructor called");
    }

    void sound() {
        System.out.println("Animal makes sound");
    }
}

class Dog extends Animal {
    String name = "Dog";

    Dog() {
        super(); // calls superclass constructor
        System.out.println("Dog constructor called");
    }

    void showName() {
        System.out.println("Superclass name: " + super.name); // Animal
        System.out.println("Subclass name: " + name);         // Dog
    }

    void sound() {
        super.sound(); // calls Animal’s sound()
        System.out.println("Dog barks");
    }
}

class Main {
    public static void main(String[] args) {
        Dog d = new Dog();
        d.showName();
        d.sound();
    }
}

/* Output: 
Animal constructor called
Dog constructor called
Superclass name: Animal
Subclass name: Dog
Animal makes sound
Dog barks
*/ 
```

## **Final Method**

* In Java, when a method is declared using the **`final`** keyword, it **cannot be overridden** by subclasses.
* Purpose: To **prevent modification of specific behavior** in subclasses.

### Syntax

```java
class Parent {
    final void display() {
        System.out.println("This is a final method.");
    }
}
```

###  Example: Final Method Usage

```java
class Parent {
    final void showMessage() {
        System.out.println("Message from Parent class");
    }
}

class Child extends Parent {
    // ❌ Error: Cannot override final method
    /*
    void showMessage() {
        System.out.println("Message from Child class");
    }
    */
}

class Main {
    public static void main(String[] args) {
        Child obj = new Child();
        obj.showMessage();  // Calls Parent’s method
    }
}

// Output 
// Message from Parent class
```

1. **Prevents Overriding** → Once a method is `final`, no subclass can override it.
2. **Inheritance Still Works** → Subclass can still *inherit* and *use* the method.
3. **Can be Overloaded** → Final methods can still be **overloaded** in the same class.

   ```java
   class Demo {
       final void display() {
           System.out.println("No arguments");
       }
       final void display(int x) {  // Overloading allowed
           System.out.println("With argument: " + x);
       }
   }
   ```
4. **Access Modifiers** → Final methods can have any access modifier (`public`, `protected`, etc.).
5. **Why use it?**

   * To maintain **consistent behavior** across all subclasses.
   * To enforce rules in framework/library design.


## Static Method

### What is a Static Method?

* A **static method** belongs to the **class** rather than to any specific object of the class.
* It can be called without creating an instance of the class.
* Declared using the `static` keyword.

```java
class ClassName {
    static returnType methodName(parameters) {
        // method body
    }
}
```

### Example: 
```java
class MathUtil {
    // Static method
    static int square(int n) {
        return n * n;
    }
}

class Main {
    public static void main(String[] args) {
        // Calling static method using class name
        int result = MathUtil.square(5);
        System.out.println("Square: " + result);
    }
}

// Output ! 
// Square: 25
```

### Key Characteristics of Static Methods

1. **No Object Required** → Can be invoked using the class name.
2. **Access Only Static Data** → Can directly access static variables and call other static methods.

   ```java
   class Demo {
       static int count = 0;

       static void increment() {
           count++;
           System.out.println(count);
       }
   }
   ```
3. **Cannot Access Non-Static Members Directly**

   * A static method cannot use instance variables or call non-static methods without creating an object.

   ```java
   class Example {
       int x = 10;

       static void print() {
           // System.out.println(x); ❌ Error: non-static variable cannot be referenced
       }
   }
   ```
4. **Inheritance**

   * Static methods can be inherited but **cannot be overridden** in the true sense.
   * If a subclass defines a static method with the same signature, it hides the parent method (method hiding).

## Abstract Class

* An **abstract class** in Java is a class that is declared using the keyword `abstract`.
* It can **contain both abstract methods and non-abstract methods**.
* **Abstract methods** are methods without a body (only declaration).
* Abstract classes **cannot be instantiated directly**; they must be subclassed.

### Syntax

```java
abstract class ClassName {
    // abstract method (no body)
    abstract void methodName();

    // non-abstract method (with body)
    void normalMethod() {
        System.out.println("This is a concrete method.");
    }
}
```

### Example: Abstract Class and Inheritance

```java
// Abstract class
abstract class Animal {
    // Abstract method (no implementation)
    abstract void sound();

    // Non-abstract method
    void sleep() {
        System.out.println("Sleeping...");
    }
}

// Subclass must implement abstract method
class Dog extends Animal {
    void sound() {
        System.out.println("Barks");
    }
}

class Main {
    public static void main(String[] args) {
        // Animal a = new Animal(); ❌ Not allowed (abstract class)
        Dog d = new Dog();
        d.sound();   // Calls overridden method
        d.sleep();   // Calls inherited concrete method
    }
}

// Output: 
// Barks
// Sleeping...
```

### Key Points

1. **Cannot Instantiate**

   * `new AbstractClass()` is not allowed.
2. **May Contain Constructors**

   * Abstract classes can have constructors, which are called when a subclass object is created.
   
3. **May Contain Static, Final, or Normal Methods**
   * Abstract classes can mix abstract and concrete (normal) methods.
   
4. **Subclass Responsibility**
   * If a subclass extends an abstract class, it must **provide implementations** for all abstract methods, unless the subclass is also abstract.
   
5. **Supports Partial Abstraction**
   * Unlike interfaces, abstract classes allow you to define **common code** (shared logic) along with abstract declarations.

# Inheritance in java  

Inheritance is one of the central features of object-oriented programming, and Java implements it in a clean, structured manner. At its core, inheritance allows a class (called a **subclass**) to acquire the properties and behaviors of another class (called a **superclass**). It enables **code reuse**, promotes **hierarchical classification**, and supports the implementation of **polymorphism**.


## **SUPERCLASS AND SUBCLASS**

#### **Super Class (Base Class / Parent Class)**

A **superclass** is the class whose members (fields, methods) are inherited by another class.  
It defines **general characteristics**.

```java
class Animal {
    void eat() {
        System.out.println("Animal eats food");
    }
}
```

### **Subclass (Derived Class / Child Class)**

The subclass extends the superclass and inherits its members. It may add more attributes or override existing behavior.

```java
class Dog extends Animal {
    void bark() {
        System.out.println("Dog barks");
    }
}
```

### **Role of `super` Keyword**

- Used to access superclass methods/variables.
- Used to call the superclass constructor as the _first_ statement in a subclass constructor.

```java
class A {
    A() { System.out.println("A constructor"); }
}

class B extends A {
    B() {
        super();
        System.out.println("B constructor");
    }
}
```

# **FINAL METHOD**

A `final` method is a method that **cannot be overridden** by subclasses.

### **Why final?**

- To **preserve critical behavior**.
- To **prevent accidental modification** in child classes.
- Often used in secure, sensitive, or core library code.
   
```java
class Vehicle {
    final void startEngine() {
        System.out.println("Engine starts safely");
    }
}

class Car extends Vehicle {
    // Error: cannot override final method
    // void startEngine() {}
}
```

### **Final Class**

A class declared as `final` cannot be extended:

```java
final class MathUtils { ... }
```

This is how Java ensures immutability for classes like `String`.

## **STATIC METHOD AND INHERITANCE**

### **Static methods are inherited but _not overridden_**.

If a subclass declares a static method with the same signature, it **hides** the method — not overrides it.

Reason:  
Static methods belong to the **class**, not to individual objects.

```java
class A {
    static void demo() { System.out.println("A"); }
}

class B extends A {
    static void demo() { System.out.println("B"); }
}

A.demo(); // prints A
B.demo(); // prints B
```

Static methods are **not polymorphic**. Method call is resolved at **compile time**, not runtime.

## **ABSTRACT CLASS**

An **abstract class** is a class that cannot be instantiated and may contain abstract (unimplemented) methods.

### **Purpose**

- Define a **common template** for all subclasses.
- Enforce that subclasses _must_ provide specific behavior.
   
```java
abstract class Shape {
    abstract void draw();
}

class Circle extends Shape {
    void draw() { System.out.println("Drawing circle"); }
}
```

### Characteristics:

- Can contain both abstract and concrete methods.
- Can have constructors.
- Used when some shared structure exists but behavior varies.
   
## **AGGREGATION AND COMPOSITION**

Both represent a **has-a** relationship, but differ in ownership and lifespan.

## **Aggregation (Weak Has-a Relation)**

- The child object _can exist independently_ of the parent.
- Referred to as a **"weak association"**.
   

Example:

- A `Student` has a `Department`.
- Even if the student object is destroyed, the department still exists.

```java
class Department { ... }

class Student {
    Department dept;   // aggregation
    Student(Department d) {
        this.dept = d;
    }
}
```

## **Composition (Strong Has-a Relation)**

- The child object **cannot exist without** the parent.
- Referred to as a **"strong association"**.
- Parent controls object creation and destruction.
   

Example:

- A `House` has `Rooms`.
- If the house is destroyed, its rooms do not exist independently.
   

```java
class House {
    private Room room = new Room();  // composition
}
```

### Exam Hint:

> “Aggregation is partial ownership; composition is complete ownership.”

## **MESSAGING**

In object-oriented programming, **messaging** refers to the process of objects communicating with one another by invoking methods.

### Basic Idea

An object requests another object to perform an operation by **sending a message** — that is, by calling a method.

```java
car.start();  // car receives a message to start
```

### Why messaging matters in inheritance

- Objects operate through well-defined interfaces (methods).
- Inheritance allows child classes to **respond differently** to the same message (polymorphism).
   
```java
Shape s = new Circle();
s.draw();   // message "draw" goes to Circle
```

This is fundamental for runtime polymorphism.

--- 
# Multithreading porgramming: 

Multithreading is a fundamental feature of Java that enables concurrent execution of multiple parts of a program. A **thread** represents an independent path of execution, and multithreading allows several such paths to run simultaneously, improving responsiveness, resource utilization, and program structure.

Java was designed from the beginning with built-in support for threads, making it one of the earliest languages to provide robust concurrency out of the box.

## Conecpt of Threads

A **thread** is the smallest unit of execution within a process.  
A Java program starts with a **main thread**, which the JVM automatically creates.

Each thread has:
- its own **stack**,
- program counter,
- local variables,
- but shares **heap memory** with other threads in the same process.
   

This shared-memory model enables communication but also creates synchronization challenges.

### **Advantages of Multithreading**

- Better CPU utilization (threads run when others wait).
- More responsive applications (e.g., GUI remains active while background tasks run).
- Simplifies division of complex tasks.
- Helps in concurrent I/O operations.
- Reduces waiting time.
   
## Creating Threads 

Java provides two fundamental ways to create a thread:

## **1) Extending the `Thread` class**

You create a new class that extends `Thread` and override the `run()` method, which defines the thread’s logic.

```java
class MyThread extends Thread {
    public void run() {
        System.out.println("Thread running");
    }
}

public class Demo {
    public static void main(String[] args) {
        MyThread t = new MyThread();
        t.start();   // creates a new thread, invokes run() asynchronously
    }
}
```

### **Key Idea**

`start()` → new thread is created  
`run()` → method containing the task

Calling `run()` directly **does not** start a new thread; it behaves like a normal method.

## **2) Implementing the `Runnable` Interface**

Preferred for large applications because Java does not support multiple inheritance of classes.

```java
class Task implements Runnable {
    public void run() {
        System.out.println("Runnable thread running");
    }
}

public class Demo {
    public static void main(String[] args) {
        Thread t = new Thread(new Task());
        t.start();
    }
}
```

### **Benefits**

- Avoids limitations of single inheritance.
- Allows task and thread management to be separated.
- Suitable for thread pooling.

## Thread life cycle 

Java defines a well-structured life cycle for threads:
### **1. New**
Thread object created but not started.

### **2. Runnable**
After calling `start()`, thread is ready to run. JVM decides scheduling.

### **3. Running**
Thread scheduler picks it for execution.

### **4. Blocked / Waiting / Timed Waiting**
Thread temporarily stops executing due to:

- `sleep(ms)`
- `wait()`
- I/O waiting
- waiting for lock
   

### **5. Terminated**

Thread completes execution or is stopped suddenly.

## Thread Methods 

### **`sleep()`**

Temporarily pauses execution.

```java
Thread.sleep(1000); // 1 second
```

### **`yield()`**

Hints scheduler to give other threads a chance.

### **`join()`**

Allows one thread to wait for the completion of another.

```java
t1.join(); // current thread waits for t1 to finish
```

### **`isAlive()`**

Checks if a thread has completed execution.

## Thread Priority 

Threads have priorities from 1 to 10:

- `MIN_PRIORITY` = 1
- `NORM_PRIORITY` = 5
- `MAX_PRIORITY` = 10
   

Higher priority threads get preference, but scheduling is **not guaranteed** since it depends on OS.

```java
t.setPriority(Thread.MAX_PRIORITY);
```

# **Thread Synchronization**

Because threads share memory, inconsistent data access may occur (**race conditions**).  
Java uses **synchronization** to ensure that only one thread accesses a critical section at a time.

## **synchronized method**

```java
synchronized void deposit(int amount) {
    balance += amount;
}
```

## **synchronized block**

More efficient when only a part needs locking.

```java
synchronized(obj) {
    // critical code
}
```

## **Why synchronization is important**

- Prevents data inconsistency
- Ensures atomic operations
- Controls concurrent access
- Avoids unpredictable results

## Thread Pooling 

Instead of creating a new thread every time, Java uses a pool of reusable threads.

Used in:
- servers
- web containers
- large applications
   

Example using Executor framework:

```java
ExecutorService service = Executors.newFixedThreadPool(5);
service.submit(new Task());
```

## Advantages of MultiThreadin

- Optimized CPU usage
- Faster execution of independent tasks
- Non-blocking UI
- Simpler program design for concurrent work
- Modular and manageable code

## Challenges of Multithreading 

- Synchronization overhead
- Risk of deadlocks
- Debugging becomes harder
- Context switching reduces performance at high thread counts

  --- 

# Thread classes

### thread class

This is the base class in Java used to create and manage threads. You can make your own thread by extending this class and overriding the `run()` method.

**Key points:**

- Inherit using `extends Thread`
- Write your task inside `run()`
- Start the thread with `start()` (never call `run()` directly)
   

```java
class MyThread extends Thread {
    public void run() {
        System.out.println("Thread running...");
    }
}

public class Main {
    public static void main(String[] args) {
        MyThread t = new MyThread();
        t.start();
    }
}
```

### runnable interface

Another way to create threads without extending Thread. You just implement `Runnable` and pass the object to a `Thread` class.

**Key points:**

- Use when your class already extends another class
- Implement `run()`
- Create a Thread object and pass the runnable
   

```java
class MyTask implements Runnable {
    public void run() {
        System.out.println("Task running...");
    }
}

public class Main {
    public static void main(String[] args) {
        Thread t = new Thread(new MyTask());
        t.start();
    }
}
```

### difference between thread and runnable

- **Thread class** → You extend Thread, simple but limited (since Java doesn’t allow multiple inheritance).
   
- **Runnable interface** → More flexible, preferred for real projects.



---
## Thread priority

Thread priority is used to tell the JVM how important a thread is. Higher-priority threads _may_ get more CPU time than lower-priority ones, but it’s **not guaranteed** because it depends on the OS scheduler.

### key points

- Priority is an integer value from **1 to 10**.
   
- Java provides 3 predefined constants:
    - `Thread.MIN_PRIORITY` → 1
    - `Thread.NORM_PRIORITY` → 5 (default)
    - `Thread.MAX_PRIORITY` → 10
   
- You set priority using `setPriority(int p)`.
   
- You get priority using `getPriority()`.
   

### example

```java
class MyThread extends Thread {
    public void run() {
        System.out.println("Thread running: " + getName());
    }
}

public class Main {
    public static void main(String[] args) {
        MyThread t1 = new MyThread();
        MyThread t2 = new MyThread();

        t1.setPriority(Thread.MAX_PRIORITY);  // highest
        t2.setPriority(Thread.MIN_PRIORITY);  // lowest

        t1.start();
        t2.start();
    }
}
```


---
## Communication between threads

Communication in multithreading refers to how threads **coordinate**, **share data**, and **notify each other** so work happens safely and in the correct order. Since multiple threads run independently, they need a controlled way to interact without corrupting data. Java provides a built-in monitor mechanism that lets threads communicate inside synchronized blocks or methods.

### why communication is needed

- To avoid inconsistent or incomplete data when multiple threads read/write the same resource.

- To let one thread wait until another finishes some task.

- To prevent busy-waiting (a thread running in a loop checking conditions repeatedly).

- To create producer–consumer systems, pipelines, background workers, etc.

### the classic communication tools

Inside any synchronized code, Java offers three key methods inherited from `Object`:

#### 1. `wait()`

- Makes the current thread **pause** and release the lock it holds.
   
- The thread will stay suspended until another thread calls `notify()` or `notifyAll()`.
   
- Used when a thread can’t continue until some condition becomes true.
   

#### 2. `notify()`

- Wakes up **one** thread that’s waiting on the same object’s monitor.
   
- Choosing which waiting thread wakes is JVM-dependent.
   

#### 3. `notifyAll()`

- Wakes **all** waiting threads; after that, they compete for the lock.
   
- Used when many threads may be waiting for a shared condition.
   

### how it works in practice

Two (or more) threads must use the **same shared object** as their communication lock.  
Example scenario: a producer puts data in a buffer; a consumer waits until the buffer has something to read.

### example

```java
class DataBox {
    int data;
    boolean hasData = false;

    synchronized void produce(int value) throws InterruptedException {
        while (hasData) {
            wait();            // wait until consumer consumes
        }
        data = value;
        hasData = true;
        System.out.println("Produced: " + value);
        notify();              // wake consumer
    }

    synchronized int consume() throws InterruptedException {
        while (!hasData) {
            wait();            // wait until producer produces
        }
        hasData = false;
        System.out.println("Consumed: " + data);
        notify();              // wake producer
        return data;
    }
}
```

--- 
# Synchronization

Synchronization in Java is the mechanism that ensures **orderly and safe access** to shared resources when multiple threads are running at the same time. Since threads execute independently, two or more of them can attempt to modify the same variable, file, object, or memory region simultaneously.

Without protection, this leads to race conditions, data inconsistency, or unpredictable behavior. Synchronization provides a controlled way to let only **one thread at a time** access critical sections of code.


At its core, Java uses the concept of a _monitor_, which is essentially a lock associated with every object. When a thread enters a synchronized block or method, it acquires the lock for that object. Until it exits, no other thread can enter any synchronized block tied to that same object. This exclusive access is what preserves data correctness.

### why synchronization matters

Whenever threads share mutable data, problems like corrupted values, incomplete reads, or overwriting can occur. 
For example, two threads adding money to the same bank account object could both read the same initial balance before either one writes back the updated value, breaking the logic. 

Synchronization prevents such overlaps by forcing the operations to occur sequentially, even in a multithreaded environment.

### Synchronized methods

A method can be declared `synchronized`, meaning the entire method becomes protected by the object’s lock. When an instance method is synchronized, the lock taken is the lock of that **particular object**. 

Only one thread can run any synchronized instance method of that object at a time. This approach is useful when the whole operation must remain atomic.

```java
synchronized void updateBalance(int amount) {
    balance += amount;
}
```

### Synchronized blocks

If whole-method locking is too broad, synchronized blocks give fine control. Only the specific part of the code that deals with shared data is protected. The lock object is specified manually, which also allows different locks for different sections of work.

```java
void deposit(int amount) {
    synchronized(this) {
        balance += amount;
    }
}
```

Using smaller synchronized blocks improves performance because threads spend less time holding the lock.

### class-level locking

Sometimes shared resources belong to the class itself rather than individual objects. In that case, synchronization must happen on the class object using a static synchronized method or a block that locks on the class literal.

```java
static synchronized void updateGlobalCount() {
    count++;
}
```

This ensures only one thread across the entire JVM touches that static resource at once.

### the concept of a critical section

A critical section is any section of code where the shared data is accessed or modified. Synchronization ensures that this block is executed atomically—meaning it completes as one uninterrupted action. Good thread-safe design tries to keep these sections as small as possible so the system stays efficient.

### interaction with thread communication

Synchronization also forms the foundation for `wait()`, `notify()`, and `notifyAll()`. These methods require the thread to already hold the object's monitor lock, which becomes possible only inside synchronized code. This is why inter-thread communication and synchronization go hand in hand.

### risks and misuses

While synchronization fixes data consistency issues, excessive or incorrect usage can lead to performance bottlenecks or deadlocks. Deadlock happens when two threads hold locks the other one needs, and both refuse to release them. Balanced locking strategies, consistent lock order, and short critical sections help avoid such pitfalls.


--- 
# Deadlock

Deadlock is one of the most serious problems in multithreaded programming. It happens when two or more threads get stuck forever because each one is waiting for the other to release a resource. No thread can move forward, no lock gets freed, and the program just freezes at that point. Java doesn’t automatically detect or fix deadlocks — preventing them is the programmer’s job.

At the heart of deadlock is the idea of **circular waiting**. Imagine Thread A holds Lock 1 and wants Lock 2. Thread B holds Lock 2 and wants Lock 1. Neither of them can continue because both are blocking each other. This situation never resolves, since both threads expect the other to give up first. That dependency cycle is what makes deadlock permanent.

### how deadlock forms

Deadlock usually arises when:

- More than one lock is involved.
   
- Threads acquire locks in different orders.
   
- A thread holds one lock while trying to acquire another.
   
- No one ever times out or releases their lock early.

Java uses intrinsic locks (monitors), and when a thread calls a synchronized block, it sits waiting if another thread already owns that lock. If two threads enter cross-locking patterns, the system can freeze.

### simple illustration

```java
class A {
    synchronized void methodA(B b) {
        System.out.println("Thread entered A.methodA");
        try { Thread.sleep(100); } catch(Exception e){}
        b.last();    // wants lock on B
    }
    synchronized void last() { }
}

class B {
    synchronized void methodB(A a) {
        System.out.println("Thread entered B.methodB");
        try { Thread.sleep(100); } catch(Exception e){}
        a.last();    // wants lock on A
    }
    synchronized void last() { }
}
```

If Thread 1 runs `a.methodA(b)` and Thread 2 runs `b.methodB(a)` at the same time, you get:

- Thread 1 owns lock A, wants lock B
- Thread 2 owns lock B, wants lock A  
   Neither continues. That’s deadlock.

### conditions for deadlock

Classically, deadlock requires four conditions (even if your exam doesn’t always name them, including them shows maturity in understanding):

1. **Mutual exclusion** — resources (locks) are exclusive; one thread at a time.
   
2. **Hold and wait** — threads hold at least one lock while requesting another.
   
3. **No preemption** — a lock can’t be forcibly taken; it’s released only voluntarily.
   
4. **Circular wait** — a closed chain of threads wait on each other’s locks.
   

If all four coexist, deadlock becomes possible.

### preventing or avoiding deadlock

Java doesn’t eliminate deadlocks automatically, but programmers avoid them using patterns like:

- Acquiring multiple locks in the **same global order**.
   
- Using **timeout-based** locking with `ReentrantLock.tryLock()` (in `java.util.concurrent.locks`).
   
- Reducing how long locks are held by shrinking synchronized sections.
   
- Avoiding nested locks where possible.
   
- Using immutable or thread-safe data structures.

--- 
## Packages

Packages in Java are basically the language’s way of organizing code into clean, manageable sections. Think of them as folders for classes, interfaces, enums, and sub-packages. Once a project grows big, throwing every class into one place becomes messy and confusing, so Java groups related functionality into packages. This helps with structure, reuse, name management, and access control.

At the language level, a package gives every class a **unique namespace**. Two classes with the same name can exist peacefully if they live in different packages. 

The JVM identifies classes by their fully qualified names — for example, `java.util.ArrayList` versus `java.awt.List`. The package prefix eliminates collisions and clarifies the class’s purpose within the system’s architecture.


### types of packages

Java supports two main categories:

#### built-in packages
These are the standard libraries provided by Java. They cover almost every common need: data structures (`java.util`), I/O (`java.io`), networking (`java.net`), GUI (`java.awt`/`javax.swing`), and much more. Using them avoids reinventing basic functionality.

#### user-defined packages
Developers can create their own packages using the `package` keyword at the top of a file. This keeps project modules separate: controllers in one package, utilities in another, services in another, etc. It brings clarity and separation of concern in large systems.

### Creating and using packages

A source file starts by declaring its package:

```java
package com.example.utils;

public class Helper {
    public static void greet() {
        System.out.println("Hello!");
    }
}
```

The file must be stored in a folder structure that matches the package path, so `com/example/utils/Helper.java`. When another class wants to use `Helper`, it imports the package:

```java
import com.example.utils.Helper;

public class Test {
    public static void main(String[] args) {
        Helper.greet();
    }
}
```

The `import` statement makes the class visible without writing the full path each time. If needed, Java allows wildcard imports:  
`import com.example.utils.*;`  
But good style uses specific imports to avoid ambiguity.

### package naming and conventions

To avoid accidental name conflicts across the world, Java recommends using the **reverse domain name** of the organization as the root — like `org.apache.tools`, `com.google.gson`, etc. User projects follow the same idea even if they aren’t organizations, just for consistency.

### role of packages in large software

In professional, multi-module systems, packages act as the boundaries between layers and departments of the codebase. Business logic, database access, networking utilities, and UI logic all live in separate packages. This makes code easier to navigate, test, maintain, and scale. Tools like Maven or Gradle build on top of this by mapping packages to project modules.


---
# Interfaces in java!

## **Introduction: What an Interface Really Is**

In Java, an **interface** is a **pure abstraction construct** — a contract that defines _what a class must do_, without specifying _how_ it does it.

It tells the world:

> “Any class that agrees to implement me must provide concrete definitions for the behaviors I list.”

Unlike classes, interfaces **cannot hold implementation (in classic Java)** — only **method signatures**, **constants**, and since Java 8, they can hold **default** and **static methods** with bodies.

Because of this, interfaces help Java deliver:

- **Total abstraction**
  
- **Loose coupling**
  
- **Multiple inheritance of type**
   
- **A clean separation between behavior specification and implementation**
   
## **Why Interfaces Exist**

Java originally forbade **multiple inheritance of classes** to avoid ambiguity problems (the “diamond problem”).  
But real-world systems _do_ need a single class to promise multiple kinds of behavior.

Interfaces solve that by letting a class **implement several behavioral contracts** safely.

Interfaces give you:

- A way to define **capabilities** (Runnable, Comparable, Serializable)
   
- A way to build **plug-and-play architectures**
   
- A way to enforce **common behavior** across unrelated classes
   
- A way to design **flexible APIs** that can evolve without breaking code
  
## ** Syntax and Structure of an Interface**

```java
interface InterfaceName {
    // abstract methods
    returnType methodName(parameters);

    // constants
    int VALUE = 10;
}
```

### Important rules:

1. All methods are **public and abstract** by default.
   
2. All variables are automatically:
   - **public**
   - **static**
   - **final**
   
3. Interfaces **cannot have constructors**, because they cannot be instantiated.
   
4. A class implements an interface using the **implements** keyword.
   
## **Implementing an Interface**

```java
interface Drawable {
    void draw();
}

class Circle implements Drawable {
    public void draw() {
        System.out.println("Drawing a circle");
    }
}
```

Notice two things:

- The implementing method must be **public**, because interface methods are public.
   
- The class must override _all_ abstract methods, or else the class must be marked **abstract**.
   
## **Difference Between Interface and Abstract Class**

| **Interface**                        | **Abstract Class**                        |
| ------------------------------------ | ----------------------------------------- |
| Only abstract methods (until Java 8) | Can have both abstract & concrete methods |
| Variables are public static final    | Can have normal variables                 |
| No constructors                      | Has constructors                          |
| Supports multiple inheritance        | Does not                                  |
| Used for total abstraction           | Used for partial abstraction              |


---
# Interface Inheritance 

Just like classes can inherit from other classes, **interfaces can inherit from other interfaces**.  
This is known as **interface inheritance**.

But unlike classes:

- Interfaces inherit **only abstract behavior**, not implementation.
- Interfaces can inherit from **multiple interfaces** (multiple inheritance).
- The child interface automatically includes **all the abstract methods** of its parent interfaces.
  

Interface inheritance exists to **build larger, richer, more meaningful contracts** by combining simpler ones.

## **Syntax of Interface Inheritance**

```java
interface A {
    void methodA();
}

interface B extends A {
    void methodB();
}
```

Here,

- `B` inherits `methodA()` from `A`.
- Any class implementing `B` must define **both** `methodA()` and `methodB()`.
   

## **Multiple Inheritance of Interfaces**

Unlike classes, interfaces support **multiple inheritance**.

```java
interface A { void a(); }
interface B { void b(); }

interface C extends A, B {
    void c();
}
```

Key points:

- `C` inherits methods from **A and B**.
- There is **no diamond problem**, because interfaces have **no conflicting implementation** (only declarations).
   
## **Why Interface Inheritance is Useful**

Interface inheritance supports:

1. **Behavior expansion**  
   Build big interfaces from smaller ones.
  
2. **Loose coupling**  
   Let classes depend on abstract contracts, not concrete classes.
   
3. **Plug-and-play architecture**  
   Swap implementations easily.
   
4. **Large-scale API design**  
   Java’s own frameworks (Collections, IO, Networking) depend heavily on interface inheritance.
   
## **Real Java Example (Collections Framework)**

Java’s Collection API is the **best real-world use** of interface inheritance:

```
Iterable
   └── Collection
         ├── List
         ├── Set
         └── Queue
```

Each interface expands behavior logically:

- `Iterable` → ability to iterate
- `Collection` → ability to store elements
- `List` → maintains order
- `Set` → removes duplicates

## **Interface Inheritance vs. Class Inheritance**

| Feature                          | Interface Inheritance             | Class Inheritance          |
| -------------------------------- | --------------------------------- | -------------------------- |
| Language keyword                 | `extends`                         | `extends`                  |
| Support for multiple inheritance | **Yes**                           | No                         |
| Inherits implementation?         | No (unless using default methods) | Yes                        |
| Method conflicts                 | Rare                              | Possible (diamond problem) |
| Designed for                     | Behavior specification            | Code reuse + structure     |

--- 
# **`instanceof` Operator 

`instanceof` is a Java keyword used to check whether an object belongs to a particular class **or** implements a specific interface.

It returns **true/false** (boolean).

## **Why It’s Used**

- To avoid **ClassCastException**
   
- To confirm an object’s type before performing type-specific operations
   
- Used in **polymorphism**, **downcasting**, and object checks in inheritance chains
   

---
## **Syntax**

```java
objectReference instanceof ClassName
```

---

## ** Key Points**

- Works with:
    
    - Classes
    - Abstract classes
    - Interfaces
    - Subclasses (polymorphic objects)
     
- If the left side is **null**, result is always **false**
  
- JVM checks the whole inheritance chain for compatibility
  

## **Example 1: Simple Class Check**

```java
String s = "Hello";
System.out.println(s instanceof String);  // true
```

## **Example 2: Inheritance**

```java
class Animal {}
class Dog extends Animal {}

Animal a = new Dog();

System.out.println(a instanceof Dog);    // true
System.out.println(a instanceof Animal); // true
```

## **Example 3: With Interface**

```java
interface Shape {}
class Circle implements Shape {}

Shape sh = new Circle();
System.out.println(sh instanceof Circle); // true
System.out.println(sh instanceof Shape);  // true
```

--- 
# **Dynamic Method Dispatch — Notes**

## **What It Is**

Dynamic Method Dispatch is the mechanism in Java that decides **which overridden method** to run **at runtime**, not compile time.

It’s the foundation of **runtime polymorphism**.

## **Why It Matters**

- Lets Java support **polymorphic behavior**
- Allows the JVM to choose the correct method based on the **actual object**, not the reference type
- Makes code flexible, extensible, and object-oriented
  
## **How It Works**

1. A superclass reference variable refers to a subclass object.
   
2. A method is overridden in the subclass.
   
3. JVM decides **at runtime** which version of the method to call.
   
## **Example**

```java
class Animal {
    void sound() {
        System.out.println("Animal makes sound");
    }
}

class Dog extends Animal {
    void sound() {
        System.out.println("Dog barks");
    }
}

class Test {
    public static void main(String[] args) {
        Animal a = new Dog();   // Upcasting
        a.sound();              // Dog's method runs (runtime decision)
    }
}
```

**Output:**  
`Dog barks`

Even though the reference is `Animal`, the JVM chooses the method from `Dog`.

## **Key Concepts**

- Depends on **overriding**, not overloading
- Happens **only with non-static, non-final, non-private** methods
- Called **runtime polymorphism** or **late binding**
- Decision made by JVM based on **actual object** the reference is pointing to

