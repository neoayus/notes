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

---
## Features of Abstraction

* **Hides implementation details** and exposes only necessary functionality.
* Achieved in Java using:

  * **Abstract Classes** → Can contain both abstract (unimplemented) and concrete (implemented) methods.
  * **Interfaces** → Define a contract of methods that a class must implement.
* Encourages **modular and flexible system design**.
* Helps in managing **large, complex codebases** by separating definition from implementation.

---

## Example in Java

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

---

## Real-World Analogy

* **ATM Machine**: Users only see the interface (insert card, enter PIN, withdraw cash) but do not see the internal mechanisms of transaction processing.
* **Car Driving**: A driver uses the steering, brakes, and accelerator without knowing the internal working of the engine.


# Inheritance

Inheritance is a **fundamental concept of OOP** that allows a class (called the *child* or *subclass*) to **acquire properties and behaviors of another class** (called the *parent* or *superclass*).

It promotes **code reusability, modularity, and hierarchical relationships** between classes. Instead of rewriting code, a subclass can extend an existing class and either **reuse, override, or add new features**.

---

## Key Points

* **Superclass (Parent class):** The class whose properties and methods are inherited.
* **Subclass (Child class):** The class that inherits from another class.
* **`extends` keyword (Java):** Used to establish inheritance.
* **Code Reusability:** Shared features can be written once in the superclass.
* **Polymorphism Support:** Subclasses can override methods for different behavior.

---

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

---

## Types of Inheritance in Java

* **Single Inheritance** → One class inherits another.
* **Multilevel Inheritance** → A subclass becomes a superclass for another class.
* **Hierarchical Inheritance** → Multiple classes inherit from a single superclass.

⚠️ **Note**: Java does **not support multiple inheritance** with classes (to avoid ambiguity). Instead, multiple inheritance is achieved using **interfaces**.

---

## Real-World Analogy

* **Family hierarchy**: A child inherits characteristics from parents, but can also have unique traits.
* **Biological species**: Mammals inherit traits from Animals, but each mammal type (like Dog, Cat, Human) has its own specific behavior.

---

## Advantages of Inheritance

* **Code Reusability** → Common functionality is defined once.
* **Faster Development** → New classes can be created quickly by reusing existing ones.
* **Maintainability** → Changes in the superclass automatically reflect in subclasses.
* **Extensibility** → New features can be easily added to subclasses.

```
## Exam Focus

* Define **inheritance** clearly: "The process where one class acquires the properties and methods of another."
* Always mention the **`extends` keyword**.
* Write a **short Java example** (one parent + one child class).
* Remember **types of inheritance** (single, multilevel, hierarchical).
* If asked, state that **Java does not support multiple inheritance with classes** (only via interfaces).

```

# Classes

A **class** in Java is a **blueprint or template** from which objects are created. It defines the **structure** (data members/fields) and **behavior** (methods/functions) of objects.

In Object-Oriented Programming (OOP), a class is the **fundamental building block** because it provides the mechanism to encapsulate **data** and **methods** together in a modular unit.

---

## Characteristics of a Class

* **Data Members (Fields):** Variables that hold the state of an object.
* **Methods (Functions):** Define the behavior or operations an object can perform.
* **Access Modifiers:** Control visibility (e.g., `public`, `private`, `protected`).
* **Constructors:** Special methods used to initialize objects.
* **Objects:** Instances created from a class.

---

## Example in Java

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

Here, `Student` is a **class**, while `s1` and `s2` are **objects** of that class.

---

## Types of Classes in Java

* **Concrete Class** → A normal class with complete implementation.
* **Abstract Class** → A class that may contain abstract methods (unimplemented). Cannot be instantiated directly.
* **Final Class** → A class that cannot be inherited. Declared using `final`.
* **Inner Class** → A class defined within another class.

---

## Real-World Analogy

* Think of a **class as a house blueprint**. It defines how the house will look (rooms, doors, windows), but it is not a real house.
* **Objects** are the actual houses built using that blueprint.

---

## Advantages of Using Classes

* **Modularity**: Code is organized into logical units.
* **Reusability**: The same class can create multiple objects.
* **Encapsulation**: Data and methods are bundled together.
* **Abstraction Support**: Complex systems can be simplified.


```
## Exam Focus

* Definition: **“A class is a user-defined data type that acts as a blueprint for creating objects.”**
* Be ready with a **short Java example** (fields, constructor, method).
* Mention **types of classes** (concrete, abstract, final, inner).
* Use **blueprint analogy** in descriptive answers.

```

# Objects

An **object** is a **real-world entity** or an **instance of a class**. While a class is only a blueprint, objects are the actual runtime entities that hold **data (state)** and perform **operations (behavior)** defined in the class.

Objects are the foundation of Object-Oriented Programming, as they model real-world things such as a *student, car, bank account,* or *employee*.

---

## Characteristics of an Object

* **Identity** → Each object is unique and has its own reference in memory.
* **State** → The data/values stored in its fields (variables).
* **Behavior** → The methods or functions that define what the object can do.

--- ## Example in Java

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

Here:

* `Student` → Class (blueprint)
* `s1`, `s2` → Objects (instances with real data)

---

## How Objects are Created in Java

1. **Using `new` keyword** (most common):

   ```java
   Student s = new Student("Rahul", 21);
   ```
2. **Using `newInstance()` method** (reflection).
3. **Using object cloning**.
4. **Using deserialization** (reading from a file or stream).

---

## Real-World Analogy

* **Class = Car design (blueprint)**
* **Object = Actual car built from that design**.
  Each car (object) may have different colors, speeds, or features, but they all follow the same blueprint (class).

---

## Advantages of Objects

* Represent **real-world entities** in programming.
* Enable **code reuse** (multiple objects from the same class).
* Provide **modularity** and make code **organized and maintainable**.
* Support **interaction** between different objects in large systems.

```
## Exam Focus

* Clear definition: **“An object is an instance of a class, containing state and behavior.”**
* Be ready with a **short Java example** (class + object creation).
* Highlight the **three features of objects**: Identity, State, Behavior.
* Mention **real-world analogy** (class = blueprint, object = actual entity).
* If asked “How are objects created in Java?”, remember **`new` keyword** is the primary way.
```

