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
