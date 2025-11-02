# Structures and Enums in C\#

The .NET Framework and C# language are deeply rooted in object-oriented principles, and both **structures (structs)** and **enumerations (enums)** are integral value-based constructs that extend the expressive power of the language. They allow developers to define **custom data types** that model real-world entities efficiently, without the overhead of full-fledged classes when unnecessary.

##  Structures in C\#

A **structure** (declared using the `struct` keyword) is a **value type** that can encapsulate related data items and behavior. It is similar to a class in that it can contain fields, properties, methods, constructors, and even implement interfaces—but unlike a class, a struct **does not support inheritance** and is **stored on the stack** rather than the heap.

### Syntax Example

```csharp
public struct Point
{
    public int X;
    public int Y;

    public Point(int x, int y)
    {
        X = x;
        Y = y;
    }

    public void Display()
    {
        Console.WriteLine($"X = {X}, Y = {Y}");
    }
}
```

### Key Characteristics

* **Value Type**: Structs are copied **by value**, meaning when you assign one struct variable to another, an independent copy is created.
* **Memory Allocation**: Stored typically on the **stack**, providing faster allocation and deallocation.
* **Default Constructor**: The compiler automatically provides a **parameterless constructor** that initializes all fields to their default values (e.g., `0`, `false`, or `null` for references).
* **User-defined Constructors**: Allowed, but cannot define a **parameterless** one manually.
* **Inheritance**: Structs cannot inherit from other structs or classes, but they can **implement interfaces**.
* **Immutability**: Structs are often used for small, immutable data representations like points, colors, or coordinates.

### Example Usage

```csharp
Point p1 = new Point(10, 20);
Point p2 = p1;     // Copies values
p2.X = 30;

Console.WriteLine(p1.X); // Output: 10 (unaffected)
```

This shows that `p1` and `p2` are **separate copies** — a fundamental difference from class behavior.

---

## When to Use a Struct

A struct should be preferred when:

* The type represents a **small, lightweight object**.
* It contains **primarily data** rather than complex behavior.
* Instances are **short-lived**.
* It is **immutable** (values don’t change after creation).

Examples: `Point`, `Color`, `DateTime`, etc.

---

## 2. Enumerations (Enums) in C#

### Definition

An **enumeration (enum)** is a **distinct type** that defines a set of **named constant values**, typically representing a collection of related integral constants (like days of the week, directions, states, etc.). It increases **code readability**, type safety, and reduces errors from using arbitrary numbers.

### Syntax Example

```csharp
public enum WeekDays
{
    Sunday,
    Monday,
    Tuesday,
    Wednesday,
    Thursday,
    Friday,
    Saturday
}
```

### Underlying Type

* By default, the underlying type of an enum is **`int`**.
* It can be explicitly changed to any **integral type** (`byte`, `short`, `long`, etc.).

Example:

```csharp
enum ErrorCode : byte
{
    None = 0,
    NotFound = 1,
    Unknown = 255
}
```

### Key Features

* **Strongly Typed Constants**: Prevents use of invalid values.
* **Default Value**: The default for any enum is `0` (the first member if not explicitly assigned).
* **Conversion**: Enums can be cast to and from their underlying integer type.
* **Flags Attribute**: When combined with `[Flags]` attribute, enums can represent a set of bit fields.

Example of `[Flags]`:

```csharp
[Flags]
public enum FileAccess
{
    Read = 1,
    Write = 2,
    Execute = 4
}

FileAccess access = FileAccess.Read | FileAccess.Write;
Console.WriteLine(access); // Output: Read, Write
```

---

## Differences Between Structures and Enums

| Feature             | Structure (`struct`)                                           | Enumeration (`enum`)                                      |
| ------------------- | -------------------------------------------------------------- | --------------------------------------------------------- |
| **Purpose**         | To define a composite value type with fields and methods.      | To define a set of named integral constants.              |
| **Keyword**         | `struct`                                                       | `enum`                                                    |
| **Underlying Type** | Can contain multiple data fields and methods.                  | Always integral type (default `int`).                     |
| **Inheritance**     | Cannot inherit but can implement interfaces.                   | Inherits from `System.Enum`.                              |
| **Instantiation**   | Must create an instance using `new` or assign fields directly. | Cannot instantiate; used directly.                        |
| **Use Case**        | When modeling objects like Point, Rectangle, etc.              | When representing fixed sets like days, colors, statuses. |
## Real-world Example: Combined Usage

```csharp
public struct Student
{
    public string Name;
    public GradeLevel Grade;

    public Student(string name, GradeLevel grade)
    {
        Name = name;
        Grade = grade;
    }
}

public enum GradeLevel
{
    Freshman = 1,
    Sophomore,
    Junior,
    Senior
}

Student s1 = new Student("Riya", GradeLevel.Sophomore);
Console.WriteLine($"{s1.Name} is in {s1.Grade} year.");
```

--- 
# The Architecture of a Class in C#

Class is the **fundamental building block of object-oriented programming (OOP)**. It acts as a **blueprint** for creating objects that encapsulate both **data (state)** and **behavior (methods)** into a single logical unit. The architecture of a class in C# defines how these elements are organized, accessed, and interact with one another to represent real-world entities effectively.

## Definition

A **class** in C# is a **reference type** declared using the `class` keyword. It provides a **template** from which multiple objects can be created, each maintaining its own data but sharing the same structure and behavior defined by the class.

```csharp
public class Student
{
    // Fields
    private int rollNo;
    private string name;

    // Constructor
    public Student(int rollNo, string name)
    {
        this.rollNo = rollNo;
        this.name = name;
    }

    // Properties
    public int RollNo
    {
        get { return rollNo; }
        set { rollNo = value; }
    }

    public string Name
    {
        get { return name; }
        set { name = value; }
    }

    // Methods
    public void Display()
    {
        Console.WriteLine($"Roll No: {rollNo}, Name: {name}");
    }

    // Destructor
    ~Student()
    {
        Console.WriteLine("Destructor Called");
    }
}
```

##  Components of Class Architecture

The internal architecture of a C# class is made up of several key elements. Each plays a specific role in defining how a class operates, encapsulates data, and exposes functionality.

### (a) **Fields**

* **Definition:** Variables declared inside a class that hold the **state or data** of the object.
* **Scope:** Usually declared as **private** to enforce **encapsulation**.
* **Example:**

  ```csharp
  private string name;
  ```
  
### (b) **Properties**

* **Definition:** Provide **controlled access** to private fields. They act as intermediaries between the internal data and the outside world.
* **Syntax:**

  ```csharp
  public string Name
  {
      get { return name; }
      set { name = value; }
  }
  ```
* **Auto-Implemented Properties:**

  ```csharp
  public int Age { get; set; }
  ```

### (c) **Constructors**

* **Definition:** Special methods that are **automatically invoked** when an object of the class is created.
* **Purpose:** Initialize data members.
* **Features:**

  * Same name as the class.
  * No return type (not even `void`).
  * Can be overloaded to provide multiple ways to initialize objects.
* **Example:**

  ```csharp
  public Student(int id, string name)
  {
      this.Id = id;
      this.Name = name;
  }
  ```

### (d) **Methods**

* **Definition:** Define the **behavior** or functionality of the class.
* **Purpose:** Allow operations on the data members or provide services related to the class.
* **Example:**

  ```csharp
  public void DisplayInfo()
  {
      Console.WriteLine($"ID: {Id}, Name: {Name}");
  }
  ```
* **Modifiers:** Can be `public`, `private`, `protected`, `static`, or `virtual` depending on usage.

### (e) **Access Modifiers**

Access modifiers define **visibility and accessibility** of class members.

* **`public`** – accessible from anywhere.
* **`private`** – accessible only within the same class.
* **`protected`** – accessible within the class and its derived classes.
* **`internal`** – accessible within the same assembly.
* **`protected internal`** – accessible within the assembly or from derived classes.

### (f) **Static Members**

* **Definition:** Members that belong to the **class itself**, not to any specific object instance.
* **Used for:** Common data or utility methods shared across all instances.
* **Example:**

  ```csharp
  public static int Count;
  public static void ShowCount() => Console.WriteLine(Count);
  ```

### (g) **Destructors**

* **Definition:** Special methods called **automatically** by the **garbage collector** when an object is destroyed.
* **Purpose:** To clean up unmanaged resources.
* **Syntax:**

  ```csharp
  ~Student()
  {
      Console.WriteLine("Destructor Invoked");
  }
  ```

### (h) **Indexers**

* **Definition:** Allow objects to be accessed like arrays, using the `this` keyword.
* **Example:**

  ```csharp
  public class Sample
  {
      private int[] arr = new int[5];
      public int this[int index]
      {
          get { return arr[index]; }
          set { arr[index] = value; }
      }
  }
  ```
  
## Memory Architecture of a Class

* **Classes are reference types** → stored on the **heap**.
* The **reference variable** (the pointer to the object) is stored on the **stack**.
* When an object is instantiated using `new`, memory for its data fields is allocated dynamically on the heap.
* Once the object is no longer referenced, the **Garbage Collector (GC)** automatically reclaims its memory.

```csharp
Student s1 = new Student(101, "Amit");
```

Here:
* `s1` (reference variable) → stored on stack.
* Actual object (data) → stored on heap.

## 4. Lifecycle of a Class Object

1. **Declaration:** A reference variable is declared.
2. **Instantiation:** The `new` keyword allocates memory for the object.
3. **Initialization:** The constructor initializes the fields.
4. **Usage:** Methods and properties operate on data.
5. **Destruction:** The destructor and garbage collector reclaim memory.

---

# Instance in C#

In object-oriented programming (OOP), the term **instance** refers to a **specific, concrete occurrence** of a **class**. While a **class** defines the blueprint or structure of an object, an **instance** represents an **actual object created from that class at runtime** — with its own unique copy of data members and access to class behaviors.

Thus, creating an instance means **bringing a class to life** by allocating memory and allowing interaction through its members (fields, properties, and methods).

## Understanding the Concept

A **class** itself is an abstract definition — it only describes *what* an object will contain and *how* it will behave. But until an **instance** is created, it doesn’t occupy memory or exist in the program’s execution space.

When you create an instance of a class, the **.NET runtime**:

1. Allocates memory for the object on the **heap**.
2. Initializes its data members (fields, properties) to their default or assigned values.
3. Invokes the appropriate **constructor** to set up initial state.
4. Returns a **reference** to that object, which is stored in a variable.

##  Syntax of Instance Creation

```csharp
ClassName objectName = new ClassName();
```

```csharp
public class Student
{
    public string Name;
    public int RollNo;

    public void Display()
    {
        Console.WriteLine($"Name: {Name}, Roll No: {RollNo}");
    }
}

// Creating an instance of Student
Student s1 = new Student();
s1.Name = "Riya";
s1.RollNo = 101;
s1.Display();   // Output: Name: Riya, Roll No: 101
```

##  The `new` Keyword and Memory Allocation

* The **`new` keyword** is used to create an instance of a reference type (class, array, string, etc.).

* It performs **three essential tasks**:
  1. Allocates memory on the heap for the object.
  2. Calls the **constructor** to initialize the object.
  3. Returns a reference (address) that is stored in a variable.

```csharp
Car myCar = new Car("Toyota");
// `myCar` → variable stored on the stack
// Actual `Car` object → stored on the heap
// The reference `myCar` points to the object in heap memory.
```

## Multiple Instances of a Class

You can create multiple instances from the same class.
Each instance maintains its own separate copy of the class’s non-static fields.

```csharp
Student s1 = new Student();
s1.Name = "Riya";

Student s2 = new Student();
s2.Name = "Amit";

Console.WriteLine(s1.Name);  // Output: Riya
Console.WriteLine(s2.Name);  // Output: Amit
```

Each object (`s1`, `s2`) holds distinct data — even though both are created from the same `Student` blueprint.

## Instance Members vs. Static Members

| Feature              | Instance Member                             | Static Member                |
| -------------------- | ------------------------------------------- | ---------------------------- |
| **Definition**       | Belongs to an individual object (instance). | Belongs to the class itself. |
| **Accessed Through** | An object of the class.                     | The class name directly.     |
| **Memory**           | Each instance gets its own copy.            | Shared across all instances. |
| **Example**          | `s1.Name`                                   | `Student.TotalCount`         |

```csharp
public class Student
{
    public string Name;           // Instance member
    public static int Count = 0;  // Static member

    public Student(string name)
    {
        Name = name;
        Count++;
    }
}

Student s1 = new Student("Riya");
Student s2 = new Student("Amit");

Console.WriteLine(s1.Name);      // Output: Riya
Console.WriteLine(Student.Count); // Output: 2
```
[]()
## Lifetime of an Instance

1. **Creation:** Using `new` keyword → memory allocated on the heap.
2. **Initialization:** Constructor executes → data members set.
3. **Usage:** Access through object reference.
4. **Destruction:** Object becomes unreachable → **Garbage Collector (GC)** reclaims memory.

The **destructor** (`~ClassName()`) is invoked by the GC just before the object is destroyed, to perform cleanup of unmanaged resources.

## Example: 

```csharp
public class Car
{
    public string Brand;
    public int Speed;

    public Car(string brand, int speed)
    {
        Brand = brand;
        Speed = speed;
    }

    public void Accelerate()
    {
        Speed += 10;
        Console.WriteLine($"{Brand} running at {Speed} km/h");
    }
}

class Program
{
    static void Main()
    {
        Car c1 = new Car("BMW", 100); // Instance created
        Car c2 = new Car("Audi", 80); // Another instance
        c1.Accelerate();
        c2.Accelerate();
    }
}
```

Each `Car` instance (`c1`, `c2`) has its own `Brand` and `Speed`, behaving independently.

* A **class** defines the *blueprint*, while an **instance** represents an *actual object* created from that blueprint.
* Instances occupy **memory on the heap**, accessed via **references stored on the stack**.
* Each instance holds **its own copy of instance members**, ensuring independence between objects.
* Instances are created using the **`new` keyword** and destroyed automatically by the **Garbage Collector** when no longer needed.


# Class and Reference Variables in C#

In C#, **classes** form the foundation of object-oriented programming. They serve as **blueprints** for creating objects that encapsulate both **data (fields, properties)** and **behavior (methods)**. However, to actually use a class in a program, we interact with it through **reference variables** — which act as _handles or pointers_ to memory locations where the class objects reside.

## Class: The Blueprint

A **class** defines a user-defined **reference type** that contains data members (fields, properties) and member functions (methods, events, etc.). It represents an _abstract concept_ until instantiated.

```csharp
public class Student //`Student` is a class— it defines what every `Student` object will contain and how it will behave.
{
    public string Name;
    public int RollNo;

    public void Display()
    {
        Console.WriteLine($"Name: {Name}, Roll No: {RollNo}");
    }
}
```

## Reference Variable: The Handle to an Object

A **reference variable** is a variable that **stores the memory address (reference)** of an object created from a class.  
In other words, a reference variable _does not hold the object itself_, but a **reference (link)** to where that object lives in the **heap memory**.

When we declare a reference variable, we’re essentially creating a placeholder that _can point to an object_ of a specific class type.

### Declaration and Initialization

```csharp
Student s1;                // Declaration only – reference variable (no object yet)
s1 = new Student();        // Object created on heap, reference stored in s1
```

Here:
- `Student` → class type (blueprint)
- `s1` → reference variable (stored on the **stack**)
- `new Student()` → actual object created in **heap memory**

## Relationship Between Class, Object, and Reference Variable

Let’s visualize:

```
Memory:
Stack → s1 (reference)
Heap  → [Student Object] { Name = null, RollNo = 0 }
```

So when you write:

```csharp
Student s1 = new Student();
s1.Name = "Amit";
```

- The **object** (`new Student()`) lives on the **heap**.
   
- The **reference variable** (`s1`) lives on the **stack** and holds the memory address of the heap object.
   
- `s1.Name` accesses the actual data inside that heap object.
   
## Null Reference

A reference variable that doesn’t point to any object is said to be **null**.

```csharp
Student s1 = null;
if (s1 == null)
{
    Console.WriteLine("No object assigned yet.");
}
```

Attempting to access members of a null reference will cause a **NullReferenceException** at runtime:

```csharp
s1.Display(); // Error: Object reference not set to an instance of an object
```
## Garbage Collection and Reference Variables

When a reference variable no longer points to an object (either reassigned or set to `null`), and no other reference points to that object, the object becomes **eligible for garbage collection**.

```csharp
Student s1 = new Student();
s1 = null; // Object is now unreachable → eligible for GC
```

The **Garbage Collector (GC)** will automatically release memory for such unreachable objects at a suitable time.

## Example: Class with Multiple Reference Variables

```csharp
public class Car
{
    public string Model;
}

class Program
{
    static void Main()
    {
        Car c1 = new Car();
        c1.Model = "Tesla";

        Car c2 = c1;  // Reference copy
        c2.Model = "BMW";

        Console.WriteLine(c1.Model); // Output: BMW
    }
}
```

| Concept                 | Description                                                                   |
| ----------------------- | ----------------------------------------------------------------------------- |
| **Class**               | Defines a _blueprint_ for objects — contains fields, properties, and methods. |
| **Reference Variable**  | Stores the _memory address_ of an object created on the heap.                 |
| **Object**              | The actual instance of a class created in memory using `new`.                 |
| **Null Reference**      | Reference variable not pointing to any object.                                |
| **Multiple References** | Different variables can point to the same object.                             |
| **Garbage Collection**  | Automatically cleans up objects no longer referenced.                         |

---
# Access Modifiers in C#

Access Modifiers in C# define **the visibility and accessibility level** of types (classes, structs, interfaces, etc.) and their members (fields, methods, constructors, properties, etc.) within the code.

They determine **which parts of your program can see or use a particular class or member.**

> Access modifiers control *who can see what* inside your program.

##  Purpose of Access Modifiers

* To **implement encapsulation**, one of the pillars of OOP.
* To **restrict access** to class members for security and data protection.
* To **control the visibility** of data and methods across different parts of the application.

## Types of Access Modifiers in C#

C# provides **five main access modifiers**:

| Modifier                        | Accessibility                                                                     | Applicable To         |
| ------------------------------- | --------------------------------------------------------------------------------- | --------------------- |
| `public`                        | Accessible from **anywhere**                                                      | All types and members |
| `private`                       | Accessible **only within the same class**                                         | Class members         |
| `protected`                     | Accessible within the **same class and derived classes**                          | Class members         |
| `internal`                      | Accessible within the **same assembly (project)**                                 | Types and members     |
| `protected internal`            | Accessible within **same assembly OR derived classes (even in other assemblies)** | Class members         |
| `private protected` *(C# 7.2+)* | Accessible within **same class OR derived classes in the same assembly**          | Class members         |

## Diagrammatic Representation (Visibility Scope)

```
public                → Everywhere
protected internal    → Derived classes + same assembly
protected             → Derived classes only
internal              → Same assembly only
private protected     → Derived classes in same assembly
private               → Same class only
```

## Detailed Explanation

### 🔹 `public`

* Most permissive access level.
* Accessible **from any other class**, assembly, or project.

```csharp
public class Car
{
    public string Model;
	// You can access `Model` and `Display()` from anywhere.

    public void Display()
    {
        Console.WriteLine(Model);
    }
}
```

### 🔹 `private`

* Most restrictive access level.
* Members are accessible **only inside the same class**.
* Default access modifier for **class members** if none is specified.

```csharp
public class Car
{
    private string model;
	// `model` and `ShowModel()` can’t be accessed from outside the `Car` class.
    private void ShowModel()
    {
        Console.WriteLine(model);
    }
}
```

### 🔹 `protected`

* Accessible **within the same class** and **any class that inherits it**.

```csharp
public class Vehicle
{
    protected int speed;
}
	// `speed` can’t be accessed by objects directly outside these classes.
public class Car : Vehicle
{
    public void ShowSpeed()
    {
        Console.WriteLine(speed); // ✅ Allowed (inherited member)
    }
}
```

### 🔹 `internal`

* Accessible **only within the same assembly** (project or DLL).
* Not visible outside the project.

```csharp
internal class Engine
{
    internal void Start()
    {
        Console.WriteLine("Engine started");
    }
}
```

✅ Accessible anywhere inside the same project.
❌ Not accessible from another assembly.

### 🔹 `protected internal`

* Combines **protected + internal**.
* Accessible within:

  * The **same assembly**, OR
  * A **derived class** in another assembly.

```csharp
public class Vehicle
{
    protected internal string type;
}

public class Car : Vehicle
{
    public void ShowType()
    {
        Console.WriteLine(type); //  Accessible (derived class)
    }
}
```

### 🔹 `private protected` 

* Combines **private + protected**.
* Accessible only **within the same assembly** and **by derived classes**.

```csharp
public class Vehicle
{
    private protected int wheels = 4;
}
	// Not accessible in derived classes from another assembly
public class Car : Vehicle
{
    public void ShowWheels()
    {
        Console.WriteLine(wheels); // ✅ Accessible (same assembly + derived)
    }
}
```

| Modifier             | Access Scope                 | Notes                           |
| -------------------- | ---------------------------- | ------------------------------- |
| `public`             | Anywhere                     | Widest visibility               |
| `private`            | Same class only              | Default for members             |
| `protected`          | Same + Derived classes       | Enables inheritance             |
| `internal`           | Same assembly only           | Common for project-only classes |
| `protected internal` | Same assembly or derived     | Most flexible combo             |
| `private protected`  | Same assembly + derived only | More restrictive combo          |

---
# Abstract Classes in C\#

In object-oriented programming, **abstraction** is one of the core principles that helps hide internal implementation details while exposing only essential functionality.  

**Abstract classes** serve as **blueprints** for other classes — they cannot be instantiated directly but define a **common base structure** that derived classes must extend and complete.

An **abstract class** is a class declared using the `abstract` keyword that **cannot be instantiated directly**.  
It is designed to **define a base behavior or structure** that **derived (child) classes** are expected to implement or override.

> Simply put: An abstract class tells _“what”_ must be done, but not always _“how”_ it should be done.

```csharp
public abstract class Shape
{
    public abstract void Draw(); // Abstract method (no implementation)

    public void Display()
    {
        Console.WriteLine("Displaying shape...");
    }
}
```

- Here, `Shape` is an **abstract class**.
- It defines an **abstract method** `Draw()` that **must be implemented** by any derived class.
- It also defines a **concrete method** `Display()` which can be used directly.

## Characteristics of Abstract Classes

1. **Declared using `abstract` keyword**.
   
```csharp
   abstract class Example { }
```
   
2. **Cannot be instantiated** directly.
   
```csharp
   Shape s = new Shape(); // ❌ Not allowed
```
   
2. **Can contain both abstract and non-abstract members.**
   - Abstract members → No body, only declaration.
   
   - Non-abstract members → Fully implemented.

3. **May include constructors, fields, properties, methods, events, and indexers.**
   
4. **Supports inheritance** — Derived classes extend and complete them.
   
5. **Can provide default functionality** that derived classes can reuse or override.
   
6. **Can include access modifiers** for control (public, protected, etc.).

##  Abstract Methods

An **abstract method**:
- Is declared only inside an abstract class.
- **Has no body** (no `{}` implementation).
- **Must be overridden** in the derived class using the `override` keyword.
   
```csharp
public abstract class Shape
{
    public abstract void Draw(); // Declaration only
}

public class Circle : Shape
{
    public override void Draw()
    {
        Console.WriteLine("Drawing a Circle");
    }
}
```

## Abstract Class with Partial Implementation

Abstract classes often provide **partial implementation** — part abstract, part concrete.  
This allows you to define common behavior that all subclasses can reuse.

```csharp
public abstract class Animal
{
    public void Eat()
    {
        Console.WriteLine("This animal eats food.");
    }

    public abstract void MakeSound(); // Must be implemented
}

public class Dog : Animal
{
    public override void MakeSound()
    {
        Console.WriteLine("Bark Bark!");
    }
}
```

- `Eat()` gives shared functionality to all animals.
- `MakeSound()` lets each animal define its unique behavior.

## Abstract Class vs Interface

Though both provide abstraction, they differ in purpose and use.

| Aspect               | Abstract Class                                            | Interface                                                                 |
| -------------------- | --------------------------------------------------------- | ------------------------------------------------------------------------- |
| Keyword              | `abstract`                                                | `interface`                                                               |
| Members              | Can include **fields, constructors, properties, methods** | Can include only **method/property/event/indexer signatures** (no fields) |
| Implementation       | Can have **partial implementation**                       | Must be **fully implemented** by class                                    |
| Multiple Inheritance | ❌ Only single inheritance allowed                         | ✅ Multiple interfaces can be implemented                                  |
| Access Modifiers     | Supports (`public`, `protected`, etc.)                    | Members are **public by default**                                         |
| Use When             | Classes are **closely related**                           | Classes share **common behavior** but not relationship                    |
## When to Use Abstract Classes

Use **abstract classes** when:
- You want to define a **common base with shared logic**.
- You expect **multiple derived classes** to implement specific methods.
- You need to provide **default or partial implementation**.
- The classes share a **“is-a”** relationship (e.g., `Car` is a `Vehicle`).
   
Avoid using them if:
- You only need to define a **contract** without shared logic → use **interfaces** instead.

# Constructors and Destructors in C#

In Object-Oriented Programming, **constructors** and **destructors** are **special methods** that control the *lifecycle* of an object — from creation to destruction.
They handle how an object **initializes its data** and how it **cleans up resources** when it’s no longer needed.

## Constructors in C#

A **constructor** is a special method of a class that is **automatically invoked** when an instance of the class is created.
It is primarily used to **initialize the object’s fields** and perform any setup required before the object is used.

```csharp
class ClassName
{
    // Constructor
    public ClassName()
    {
        // Initialization code
    }
}
```
#### Key Characteristics:

1. A constructor **has the same name as the class**.
2. It **does not have any return type**, not even `void`.
3. It can be **overloaded** — multiple constructors with different parameter lists.
4. It is **called automatically** when an object is instantiated using `new`.
5. If no constructor is defined, the compiler provides a **default constructor** automatically.

##  Types of Constructors in C#

### **Default Constructor**

A constructor that takes **no parameters** and initializes default values.

```csharp
class Car
{
    public string Model;
    public int Year;

    public Car()
    {
        Model = "Unknown";
        Year = 2020;
    }
}
```

###  **Parameterized Constructor**

Used to initialize objects with **custom values** at the time of creation.

```csharp
class Car
{
    public string Model;
    public int Year;

    public Car(string model, int year)
    {
        Model = model;
        Year = year;
    }
}
```

```csharp
Car c1 = new Car("Tesla", 2024);
```

###  **Copy Constructor**

Creates a **new object** by copying data from another object of the same type.

```csharp
class Car
{
    public string Model;
    public int Year;

    public Car(Car obj)
    {
        Model = obj.Model;
        Year = obj.Year;
    }
}
```

```csharp
Car c1 = new Car("BMW", 2023);
Car c2 = new Car(c1); // Copy constructor
```

### 🔹 **4. Static Constructor**

Used to **initialize static members** of a class.
It runs **only once**, before any instance or static member is accessed.

**Characteristics:**
* Declared using the `static` keyword.
* Has **no access modifiers** and **no parameters**.
* **Cannot be called manually**.
* Automatically called by the CLR when the class is loaded.

```csharp
class Database
{
    static string connectionString;

    static Database()
    {
        connectionString = "Server=localhost;DB=ShopDB;";
        Console.WriteLine("Static constructor executed");
    }
}
```
###  **Private Constructor**

Used to **restrict instantiation** of a class from outside — often in **Singleton** or **Utility** classes.

```csharp
class Logger
{
    private Logger() { }

    public static void Log(string message)
    {
        Console.WriteLine(message);
    }
}
```

✅ Prevents:

```csharp
Logger l = new Logger(); // ❌ Not allowed
```

## Constructor Overloading

Like regular methods, constructors can be **overloaded** — multiple constructors with different parameter types or counts.

```csharp
class Student
{
    public string Name;
    public int Age;

    public Student()               { Name = "Unknown"; Age = 0; }
    public Student(string name)    { Name = name; Age = 18; }
    public Student(string name, int age) { Name = name; Age = age; }
}
```

## Constructor Chaining

Constructor chaining means one constructor **calls another constructor** in the same or base class.
It’s done using the `this()` or `base()` keywords.

### Example — Using `this()`

```csharp
class Student
{
    public string Name;
    public int Age;

    public Student() : this("Unknown", 18)
    {
    }

    public Student(string name, int age)
    {
        Name = name;
        Age = age;
    }
}
```

Here, the parameterless constructor calls the parameterized constructor to reuse initialization logic.

#### Example — Using `base()`

Used when a derived class wants to **call a base class constructor**.

```csharp
class Person
{
    public Person(string name)
    {
        Console.WriteLine("Base Constructor: " + name);
    }
}

class Employee : Person
{
    public Employee(string name) : base(name)
    {
        Console.WriteLine("Derived Constructor");
    }
}
// **Output:**
// Base Constructor: Riya
// Derived Constructor
```

##  Destructors in C\#

A **destructor** is a special method used to **clean up resources** before an object is destroyed by the Garbage Collector (GC).

It is automatically called by the CLR when an object is **no longer accessible**, typically when memory is being reclaimed.

### Syntax:

```csharp
class ClassName
{
    ~ClassName()
    {
        // Cleanup code
    }
}
```

#### Key Characteristics:

1. Defined using **tilde (~)** followed by class name.
2. **Cannot have parameters or access modifiers.**
3. **Cannot be overloaded or called manually.**
4. Automatically invoked by the **Garbage Collector**.
5. Used mainly to **release unmanaged resources** like file handles, database connections, or network sockets.

# The Garbage Collector (GC) in .NET

In the .NET Framework, **memory management** is handled automatically by the **Garbage Collector (GC)** — a component of the **Common Language Runtime (CLR)** that ensures efficient allocation and release of memory for applications.

The GC eliminates the need for developers to manually free memory (like in C or C++ with `free()` or `delete`), reducing bugs such as **memory leaks** and **dangling pointers**.

## Definition

The **Garbage Collector (GC)** is a **memory management mechanism** in .NET that automatically:
* Allocates memory for new objects on the **managed heap**, and
* Reclaims memory that is no longer being used by the program.
## Need for Garbage Collection

In traditional languages (like C/C++), programmers manually allocate and free memory — forgetting to free memory leads to **memory leaks**, freeing it too early leads to **invalid memory access**.

.NET removes these risks by providing **automatic memory management**.
The GC:
* Frees memory for objects that are no longer in use.
* Compacts free memory to reduce fragmentation.
* Improves overall performance and reliability.

## The Managed Heap

All **reference type objects** (like classes, arrays, strings, etc.) in .NET are stored in a region of memory called the **managed heap**.
The heap is managed entirely by the **CLR’s garbage collector**, not the operating system.

When a new object is created:

1. Memory is allocated from the heap.
2. The GC tracks this object’s lifetime.
3. When the object is no longer referenced, GC reclaims that space.

## How the Garbage Collector Works

The GC periodically checks for **objects that are no longer accessible** (no variable or reference points to them).
When it detects such objects, it:

1. **Pauses** the program temporarily (called a “stop-the-world” pause).
2. **Marks** objects that are still in use.
3. **Sweeps** unreferenced (garbage) objects.
4. **Compacts** the heap to optimize free space.

### Steps in GC Process:

1. **Mark**: Identify all objects that are reachable.
2. **Sweep**: Remove unreachable (garbage) objects.
3. **Compact**: Rearrange memory to make allocation faster.

## Generational Garbage Collection

To optimize performance, the GC divides objects in memory into **generations** based on how long they’ve lived.
Most newly created objects die young, so the GC focuses more frequently on younger generations.

| Generation | Description                                  | Example                        |
| ---------- | -------------------------------------------- | ------------------------------ |
| **Gen 0**  | Newly created, short-lived objects.          | Temporary variables, loop data |
| **Gen 1**  | Survived one GC cycle; medium-lived objects. | Cached data                    |
| **Gen 2**  | Long-lived objects; collected less often.    | Static data, app-level caches  |

### How it works:
* When a Gen 0 collection happens, surviving objects are **promoted** to Gen 1.
* Gen 1 survivors move to Gen 2.
* Gen 2 collections happen rarely because they’re more expensive.

This generational model keeps collection efficient — focusing on young, short-lived objects that make up most garbage.

## Forcing Garbage Collection

Normally, GC runs automatically, but you can **force it manually** using:

```csharp
GC.Collect();
```

You can also check memory stats:

```csharp
long mem = GC.GetTotalMemory(false);
Console.WriteLine("Memory Used: " + mem);
```

## Performance Optimization by GC

The GC ensures memory efficiency through:

* **Automatic compaction** of memory blocks.
* **Releasing unused objects** to free up space.
* **Pausing application threads** only briefly.
* **Generational collection** — minimizing unnecessary scans.

The CLR also uses **background GC** and **server GC** for optimized performance in:

* Desktop applications (workstation GC).
* High-performance server environments (server GC).

## Advantages of Garbage Collection

 + Automatic memory management — no need for manual `free()`
 + Prevents memory leaks and fragmentation
 + Improves program stability and security
 + Reduces programmer errors related to pointer misuse
 + Makes memory allocation more predictable and efficient

## Limitations of Garbage Collection

+  The timing of collection is **non-deterministic** (can’t predict exactly when it’ll run).
 + GC pauses can cause slight **performance delays**.
+  **Unmanaged resources** still need manual cleanup.
 + Too many temporary allocations can **trigger frequent collections**, slowing performance.

# **.NET Base Class Library (BCL)**

The **.NET Base Class Library (BCL)** is the **foundation of the entire .NET Framework**.
It is a **comprehensive collection of reusable classes, interfaces, structures, and enumerations** that provide access to essential system functionalities such as file operations, data manipulation, collections, exception handling, input/output, and many more.

## **Definition**

The **Base Class Library (BCL)** is a **subset of the Framework Class Library (FCL)** that provides the **core functionalities** needed by all .NET applications.
It contains the most commonly used types and serves as the **standard library** for .NET languages such as C#, VB.NET, and F#.

All classes in the BCL are organized into **namespaces**, with the root being `System`.

## Role and Purpose

The BCL provides developers with:

* A consistent programming model across all .NET languages.
* Pre-tested, optimized, and reliable components.
* Access to system resources like the file system, console, and network.
* Reusable functionality to reduce code redundancy.

It **abstracts low-level operations**, meaning developers can perform complex tasks (like file handling or database connectivity) without worrying about platform-specific details.

## ** Relationship Between BCL and FCL**

| Term                              | Description                                                                                       |
| --------------------------------- | ------------------------------------------------------------------------------------------------- |
| **BCL (Base Class Library)**      | Core set of fundamental classes for basic functionality like collections, I/O, and data types.    |
| **FCL (Framework Class Library)** | Superset of BCL — includes all libraries required for web, Windows, database, and XML operations. |
## ** Organization of BCL**

All components of the BCL are organized within **namespaces** (logical groupings of related classes).
The **root namespace** is `System`, under which all essential functionality resides.

Some of the most important namespaces in the BCL are:

| Namespace                      | Description                                                               |
| ------------------------------ | ------------------------------------------------------------------------- |
| **System**                     | Core types such as `Object`, `String`, `Int32`, `Boolean`, etc.           |
| **System.IO**                  | Classes for file and stream operations (e.g., `File`, `StreamReader`).    |
| **System.Collections**         | Non-generic collections like `ArrayList`, `Hashtable`.                    |
| **System.Collections.Generic** | Generic collections like `List<T>`, `Dictionary<K,V>`.                    |
| **System.Threading**           | Classes for multithreading and synchronization.                           |
| **System.Net**                 | Networking classes for HTTP requests, sockets, etc.                       |
| **System.Text**                | Classes for text manipulation and encoding (`StringBuilder`, `Encoding`). |
| **System.Data**                | Classes for database access using ADO.NET.                                |
| **System.Reflection**          | For metadata inspection and late binding.                                 |
| **System.Linq**                | For querying collections using LINQ syntax.                               |

## **Core Functionalities Provided by BCL**

### (a) **Data Types and Object Manipulation**

Provides classes for working with data types:

```csharp
System.Object
System.String
System.Int32
System.Boolean
```

### (b) **Collections and Data Structures**

Contains both **generic** and **non-generic** collection classes:

```csharp
ArrayList, Hashtable, List<T>, Dictionary<TKey, TValue>
```

### (c) **Input/Output (I/O) Operations**

Provides stream classes for file handling and console operations:

```csharp
System.IO.File, System.IO.StreamReader, System.IO.StreamWriter
```

### (d) **Exception Handling**

Provides base exception classes:

```csharp
System.Exception, System.IO.IOException, System.NullReferenceException
```

### (e) **Threading**

Manages concurrent operations and synchronization:

```csharp
System.Threading.Thread, System.Threading.Tasks.Task
```

### (f) **Networking**

Handles communication over the Internet or local networks:

```csharp
System.Net.WebClient, System.Net.Sockets.Socket
```

### (g) **Reflection**

Allows inspection and dynamic loading of assemblies:

```csharp
System.Reflection.Assembly, System.Type
```

---

## **Advantages of the BCL**

 **Language Independence** – Common functionality available across all .NET languages.
 **Code Reusability** – Prebuilt, tested, and optimized components reduce development effort.
 **Consistency** – Unified API design makes learning and usage uniform across projects.
 **Platform Independence** – Works uniformly across Windows, Linux, and macOS (in .NET Core / .NET 6+).
 **Performance and Reliability** – Managed, compiled, and optimized code maintained by Microsoft.


# **Inheritance in C#**

**Inheritance** is one of the four core principles of **Object-Oriented Programming (OOP)** — alongside **Encapsulation, Polymorphism,** and **Abstraction**.

In C#, inheritance allows one class to **derive** or **inherit** the properties and behaviors (fields, methods, and other members) of another class.
It supports **code reusability** and promotes a **hierarchical classification** of classes.

## **Definition**

> **Inheritance** is the process by which one class (called the *derived class* or *child class*) acquires the properties and behaviors of another class (called the *base class* or *parent class*).

This means that the derived class can access and reuse members (fields, methods, properties) of the base class without rewriting the same code.

## **Syntax of Inheritance**

```csharp
class BaseClass
{
    // Base class members
}

class DerivedClass : BaseClass
{
    // Derived class members
}
```

Here, `DerivedClass` inherits all accessible members of `BaseClass`.

## **Example: 

```csharp
using System;

class Animal
{
    public void Eat()
    {
        Console.WriteLine("Animal is eating.");
    }
}

class Dog : Animal
{
    public void Bark()
    {
        Console.WriteLine("Dog is barking.");
    }
}

class Program
{
    static void Main()
    {
        Dog d = new Dog();
        d.Eat();   // Inherited from Animal class
        d.Bark();  // Defined in Dog class
    }
}
```

**Output:**

```
Animal is eating.
Dog is barking.
```


## **Types of Inheritance in C#**

C# supports several types of inheritance, but **not all directly** (due to ambiguity issues like in C++).

| Type                                  | Description                                            | Supported in C#           |
| ------------------------------------- | ------------------------------------------------------ | ------------------------- |
| **Single Inheritance**                | One base class → one derived class                     | ✅ Yes                     |
| **Hierarchical Inheritance**          | One base class → multiple derived classes              | ✅ Yes                     |
| **Multilevel Inheritance**            | Derived class acts as a base for another derived class | ✅ Yes                     |
| **Multiple Inheritance (Classes)**    | One derived class inherits from multiple base classes  | ❌ No (C# prevents it)     |
| **Multiple Inheritance (Interfaces)** | One class implements multiple interfaces               | ✅ Yes                     |
| **Hybrid Inheritance**                | Combination of different types                         | ✅ Through interfaces only |
### **(a) Single Inheritance Example**

```csharp
class Parent
{
    public void Display() { Console.WriteLine("Parent"); }
}

class Child : Parent
{
    public void Show() { Console.WriteLine("Child"); }
}
```

### **(b) Multilevel Inheritance Example**

```csharp
class A
{
    public void MethodA() { Console.WriteLine("Class A"); }
}
class B : A
{
    public void MethodB() { Console.WriteLine("Class B"); }
}
class C : B
{
    public void MethodC() { Console.WriteLine("Class C"); }
}
```

**Output:**

```
Class A
Class B
Class C
```

### **(c) Hierarchical Inheritance Example**

```csharp
class Animal
{
    public void Eat() { Console.WriteLine("Eating"); }
}
class Dog : Animal
{
    public void Bark() { Console.WriteLine("Barking"); }
}
class Cat : Animal
{
    public void Meow() { Console.WriteLine("Meowing"); }
}
```

## **The `base` Keyword**

The `base` keyword is used in a derived class to:

1. Call a constructor of the base class.
2. Access members (fields, methods) of the base class that are **hidden or overridden**.

### Example:

```csharp
class Person
{
    public Person(string name)
    {
        Console.WriteLine("Person Constructor: " + name);
    }
}

class Employee : Person
{
    public Employee(string name) : base(name)
    {
        Console.WriteLine("Employee Constructor");
    }
}
//Output:
//Person Constructor: John
//Employee Constructor
```

## **Advantages of Inheritance**

 **Code Reusability** — Common code is written once in the base class.
 **Extensibility** — Existing classes can be extended easily.
 **Polymorphism** — Enables method overriding for dynamic behavior.
 **Maintenance Efficiency** — Changes in the base class automatically reflect in all derived classes.

---

## **Limitations of Inheritance**

 **Tight Coupling** — Derived class depends on the base class.
**Complex Hierarchies** — Deep inheritance chains can reduce clarity.
 **Not suited for all scenarios** — Sometimes, *composition* is preferred over inheritance.

## **Summary **

| Concept              | Description                        |
| -------------------- | ---------------------------------- |
| **Keyword**          | `:` (colon)                        |
| **Base Class**       | The parent class                   |
| **Derived Class**    | The child class inheriting members |
| **Accessed Members** | Public, Protected, Internal        |
| **Base Keyword**     | Used to access base class members  |
| **Virtual/Override** | Used for runtime polymorphism      |
| **Sealed**           | Prevents inheritance or overriding |

---

# **Method Overloading and Method Overriding in C#**

In Object-Oriented Programming (OOP), **polymorphism** means “many forms” — allowing methods to behave differently based on context.
C# achieves polymorphism in **two ways**:

1. **Compile-time Polymorphism** → via **Method Overloading**
2. **Runtime Polymorphism** → via **Method Overriding**

Both allow flexibility, cleaner code, and reusability, but they occur at different stages of program execution.


## **Method Overloading (Compile-Time Polymorphism)**

> Method Overloading means defining **multiple methods** in the same class **with the same name** but **different parameter lists** (type, number, or order of parameters).

It is resolved **at compile time**, hence also called **static or compile-time polymorphism**.

### **Purpose:**
* To perform **similar operations** with different data types or parameters.
* To improve **code readability** by using a common method name.

### **Example:**

```csharp
using System;

class Calculator
{
    public int Add(int a, int b)
    {
        return a + b;
    }

    public double Add(double a, double b)
    {
        return a + b;
    }

    public int Add(int a, int b, int c)
    {
        return a + b + c;
    }
}

class Program
{
    static void Main()
    {
        Calculator calc = new Calculator();
        Console.WriteLine(calc.Add(5, 10));         // Calls int Add
        Console.WriteLine(calc.Add(5.5, 2.5));      // Calls double Add
        Console.WriteLine(calc.Add(1, 2, 3));       // Calls 3-parameter Add
    }
}

// Output:

//15
//8
//6
```

### **Advantages of Method Overloading:**

 Enhances code **readability** and **reusability**
 Reduces method naming confusion
 Improves **maintainability** — same operation across varied inputs


## **Method Overriding (Runtime Polymorphism)**

> Method Overriding allows a **derived class** to provide a **new implementation** of a method that is already defined in its **base class**.

The overridden method in the derived class must have the **same name**, **return type**, and **parameters** as the base class method.
It is resolved **at runtime**, so it’s also known as **dynamic polymorphism**.
### **Example:**

```csharp
using System;

class Animal
{
    public virtual void Speak()
    {
        Console.WriteLine("Animal makes a sound");
    }
}

class Dog : Animal
{
    public override void Speak()
    {
        Console.WriteLine("Dog barks");
    }
}

class Program
{
    static void Main()
    {
        Animal obj = new Dog();  // Base class reference → Derived object
        obj.Speak();             // Calls Dog's Speak() at runtime
    }
}
```
## **Using `base` Keyword in Overriding**

The `base` keyword can call the parent version of the overridden method.

```csharp
class Dog : Animal
{
    public override void Speak()
    {
        base.Speak();  // Calls Animal's Speak()
        Console.WriteLine("Dog barks");
    }
}
```

**Output:**

```
Animal makes a sound
Dog barks
```

## **Using `new` Keyword vs `override`**

Sometimes, a derived class defines a method with the same name as in the base class **without using `override`**.
This **hides** the base class method instead of overriding it.

```csharp
class A
{
    public void Show()
    {
        Console.WriteLine("Base Show");
    }
}

class B : A
{
    public new void Show()
    {
        Console.WriteLine("Derived Show");
    }
}
```

**Output:**

```
Derived Show
```

---

# **Operator Overloading in C#**

> Operator Overloading allows developers to redefine or “overload” the way **operators** (like `+`, `-`, `*`, `==`, etc.) behave when used with **user-defined types** (like classes or structs).

In simple terms, it lets you make your custom objects use operators in a natural, meaningful way.

## **General Syntax:**

```csharp
public static <return_type> operator <symbol>(<parameter_list>)
{
    // operation logic
}
```

* Must be declared **public** and **static**.
* Must use the keyword **`operator`**.
* Overloadable only for **existing operators**, not new symbols.
* At least one operand must be a **user-defined type**.

### **Example: Overloading the `+` Operator**

```csharp
using System;

class Complex
{
    public int Real, Imaginary;

    public Complex(int r, int i)
    {
        Real = r;
        Imaginary = i;
    }

    // Overloading + operator
    public static Complex operator +(Complex c1, Complex c2)
    {
        return new Complex(c1.Real + c2.Real, c1.Imaginary + c2.Imaginary);
    }

    public void Display()
    {
        Console.WriteLine($"{Real} + {Imaginary}i");
    }
}

class Program
{
    static void Main()
    {
        Complex c1 = new Complex(3, 4);
        Complex c2 = new Complex(2, 5);

        Complex sum = c1 + c2;   // Calls overloaded + operator
        sum.Display();
    }
}
```

**Output:**

```
5 + 9i
```

**Explanation:**
The `+` operator now performs addition on complex numbers — not just integers or floats.

> Operators that **cannot** be overloaded:
> `=`, `&&`, `||`, `[]`, `()`, `?:`, `=>`, `new`, `is`, `as`, `sizeof`, `typeof`, `checked`, `unchecked`, `default`, `delegate`.

## **Unary Operator Example**

```csharp
class Counter
{
    public int Value;

    public Counter(int v) { Value = v; }

    public static Counter operator ++(Counter c)
    {
        return new Counter(c.Value + 1);
    }
}

class Program
{
    static void Main()
    {
        Counter c1 = new Counter(5);
        Counter c2 = ++c1;
        Console.WriteLine(c2.Value); // 6
    }
}
```


##  **Advantages:**

* Cleaner, more expressive syntax.
* Makes user-defined types act like built-in types.
* Helps in mathematical or geometric programming (e.g., Vector, Complex, Matrix).
##  **Disadvantages:**

* Can make code **confusing** if overused.
* May cause **unexpected behavior** if not implemented logically.
* Slightly reduces **performance** due to method calls behind operators.

--- 

# **Method Hiding in C#**

> **Method Hiding** is an object-oriented feature in C# that allows a **derived class** to define a new method with the **same name** as one in its **base class**, effectively **hiding** the base class version rather than **overriding** it.

This is achieved using the `new` keyword.
When a method in a derived class hides a method in the base class, the **base class method is not overridden** — it’s simply **hidden** when the object is accessed through a derived class reference.

###  **Syntax**

```csharp
class BaseClass
{
    public void Show()
    {
        Console.WriteLine("BaseClass Show()");
    }
}

class DerivedClass : BaseClass
{
    public new void Show()
    {
        Console.WriteLine("DerivedClass Show()");
    }
}
```

### **Example Explanation**

```csharp
DerivedClass d = new DerivedClass();
d.Show();  // Output: DerivedClass Show()

BaseClass b = new DerivedClass();
b.Show();  // Output: BaseClass Show()
```

* `d.Show()` calls the derived version — because the **derived type reference** is used.
* `b.Show()` calls the base version — because the **base type reference** hides the derived method.

## **Important Notes**

1. The **`new` keyword** indicates that a derived member hides an inherited member with the same name.

   * Without `new`, the compiler gives a **warning** that the method hides another member implicitly.

2. Method Hiding is **not polymorphism** —
   It’s a **compile-time** decision, not a runtime one (unlike **method overriding**).

3. The hidden base method can still be accessed using the **base class reference** or the **base keyword** inside the derived class.

### **Example with Base Keyword**

```csharp
class Animal
{
    public void Speak()
    {
        Console.WriteLine("Animal makes a sound");
    }
}

class Dog : Animal
{
    public new void Speak()
    {
        Console.WriteLine("Dog barks");
    }

    public void CallBaseMethod()
    {
        base.Speak(); // Calls Animal's version
    }
}
```

```csharp
Dog d = new Dog();
d.Speak();          // Dog barks
d.CallBaseMethod(); // Animal makes a sound
```

## **Method Hiding vs Method Overriding**

| Feature                 | Method Hiding                                      | Method Overriding                             |
| ----------------------- | -------------------------------------------------- | --------------------------------------------- |
| **Keyword**             | `new`                                              | `override`                                    |
| **Polymorphism Type**   | Compile-time                                       | Run-time                                      |
| **Method Type**         | Non-virtual methods                                | Must be `virtual` or `abstract` in base class |
| **Behavior Decided By** | Reference type                                     | Actual object type                            |
| **Base method access**  | Can use `base.MethodName()`                        | Can use `base.MethodName()`                   |
| **Purpose**             | Replace base method intentionally in derived class | Extend or modify base class behavior          |

##  **Advantages 

* Allows defining new behavior in derived class **without modifying** the base class.
* Useful when you don’t want to affect existing base class functionality.
* Provides a clear separation between old and new versions of methods.

## **Disadvantages**

* Can cause **confusion** if not used carefully — because which method executes depends on reference type.
* **Not true polymorphism**, so it breaks dynamic behavior.
* Can make debugging difficult if many methods share the same names.

# **Anonymous Methods and Anonymous Types in C#**

These are the features designed to make code more concise, expressive, and flexible, especially when working with delegates, LINQ, and event-driven programming.

Both concepts share one word — *anonymous* — meaning **"without a name"**, but they apply to different things:

* **Anonymous Methods** → nameless *code blocks or functions*
* **Anonymous Types** → nameless *data structures or objects*

## Anonymous Methods

> An **anonymous method** is a block of code that can be passed as a **delegate parameter** without defining a separate, named method.

They provide a **shortcut** to define small methods **inline** where they’re used — improving readability and reducing clutter in your code.

```csharp
delegate void GreetDelegate(string name);

class Program
{
    static void Main()
    {
        // Defining an anonymous method using 'delegate' keyword
        GreetDelegate greet = delegate (string name)
        {
            Console.WriteLine($"Hello, {name}!");
        };

        greet("Sushh");
    }
}
```

**Output:**

```
Hello, Sushh!
```

Here, no named method like `void SayHello(string name)` was defined.
Instead, the `delegate` keyword created a function *inline*.

### **Features**

 Can **access local variables** of the enclosing scope (closure).
 Don’t need a separate declaration in the class.
 Can be **assigned to delegates or events**.
 Can even **omit parameters** if not needed.

### **Example: Anonymous Method Without Parameters**

```csharp
delegate void Display();

class Program
{
    static void Main()
    {
        Display show = delegate
        {
            Console.WriteLine("Anonymous method example");
        };
        show();
    }
}
```

##  **Anonymous Types**

> **Anonymous Types** allow creation of **objects without explicitly defining a class** to hold their data.
> C# automatically generates a **class** behind the scenes with **read-only properties** corresponding to the object’s fields.

### **Syntax**

```csharp
var person = new { Name = "Aisha", Age = 21 };
Console.WriteLine($"Name: {person.Name}, Age: {person.Age}");
```

**Output:**

```
Name: Aisha, Age: 21
```

C# compiler internally creates a class like:

```csharp
internal sealed class __AnonymousType0
{
    public string Name { get; }
    public int Age { get; }
}
```

So `person` is an instance of that hidden compiler-generated type.

### **Key Features**

 Created using `new { }` syntax without class definition.
 Automatically **read-only** (immutable).
 Type name is **compiler-generated** and **not accessible** directly.
 Must be declared with the `var` keyword.
 Can include properties, but **not methods or events**.
 Useful for **temporary data grouping** or **projections in LINQ**.
 
### **Example: Anonymous Type in LINQ**

```csharp
var students = new[]
{
    new { Name = "Ravi", Marks = 88 },
    new { Name = "Maya", Marks = 95 },
    new { Name = "Kiran", Marks = 76 }
};

var toppers = from s in students
               where s.Marks > 80
               select new { s.Name, Grade = "A" };

foreach (var t in toppers)
    Console.WriteLine($"{t.Name} - {t.Grade}");
```

**Output:**

```
Ravi - A
Maya - A
```

Here, the **anonymous type** `{ s.Name, Grade = "A" }` holds a temporary structure for query results.

---

# **Sealed Classes in C#**

> A **sealed class** in C# is a class that **cannot be inherited**.
> Once a class is marked as **sealed**, it becomes the **end of the inheritance chain**.

In other words — you can **create objects** of a sealed class,
but you **can’t use it as a base class** for another class.

The keyword used is  `sealed`.

### **Syntax:**

```csharp
sealed class ClassName
{
    // class members
}
```

Example:

```csharp
sealed class Animal
{
    public void Speak()
    {
        Console.WriteLine("Animal sound");
    }
}

class Dog : Animal  // ❌ ERROR: cannot derive from sealed class
{
}
```

**Compiler Error:**

```
'Dog': cannot derive from sealed type 'Animal'
```

## **Purpose of a Sealed Class**

* To **restrict inheritance** and prevent further derivation.
* To **enhance security and maintainability** of your code.
* To **protect class logic** from being modified via overriding.
* To **optimize performance** — the JIT compiler can make certain optimizations for sealed classes.

##  **Example: Valid Usage**

```csharp
sealed class MathHelper
{
    public int Square(int x)
    {
        return x * x;
    }
}

class Program
{
    static void Main()
    {
        MathHelper obj = new MathHelper();
        Console.WriteLine(obj.Square(5));
    }
}
```

**Output:**

```
25
```

## **Sealed Methods**

Besides sealing a *whole class*, we can also seal **individual methods**.
But that can only be done **inside a derived class** —
to prevent further overriding of a virtual method.

```csharp
class Base
{
    public virtual void Display()
    {
        Console.WriteLine("Base class Display");
    }
}

class Derived : Base
{
    public sealed override void Display()
    {
        Console.WriteLine("Derived class Display");
    }
}

class MoreDerived : Derived
{
    //  ERROR: cannot override sealed method
    // public override void Display() { }
}
```

So, **sealed methods** stop further overriding —
just like sealed classes stop inheritance.

--- 
# **Creating Interfaces in C#**

> An **interface** in C# is a **contract** that defines a set of **methods, properties, events, or indexers** that a class or struct must **implement**.

Interfaces specify **what** a class should do —
not **how** it does it.

They provide a blueprint for functionality, ensuring that different classes follow the same rules or behavior pattern.

* Interfaces **cannot contain implementation** — only **declarations** (method signatures, property definitions, etc.).
* A class or struct that implements an interface **must provide the full implementation** for every member defined in the interface.

## **Syntax**

```csharp
interface IInterfaceName
{
    // method declaration
    void MethodName();

    // property declaration
    int PropertyName { get; set; }
}
```

Then, a **class** implements this interface as:

```csharp
class ClassName : IInterfaceName
{
    public void MethodName()
    {
        // method body
    }

    public int PropertyName { get; set; }
}
```

##  **Example : 

```csharp
interface IAnimal
{
    void Speak();
    void Eat();
}

class Dog : IAnimal
{
    public void Speak()
    {
        Console.WriteLine("Dog barks");
    }

    public void Eat()
    {
        Console.WriteLine("Dog eats bones");
    }
}

class Cat : IAnimal
{
    public void Speak()
    {
        Console.WriteLine("Cat meows");
    }

    public void Eat()
    {
        Console.WriteLine("Cat eats fish");
    }
}
```

### **Output:**

```csharp
IAnimal a = new Dog();
a.Speak(); // Dog barks
a.Eat();   // Dog eats bones
```

 **Polymorphism achieved through interface reference**.

##  **Advantages of Using Interfaces**

* Promotes **code reusability and consistency**.
* Supports **polymorphism** without class inheritance.
* Enables **dependency injection** and **loose coupling**.
* Simplifies **testing and maintenance**.
* Encourages **modular, flexible architecture**.

## **Limitations**

* Can’t define fields, constructors, or destructors.
* Can’t include access modifiers (all members are implicitly `public`).
* Cannot contain method implementation (in versions below C# 8.0).

---  
# **Implementing Interface Inheritance in C#**

> In C#, **interfaces can inherit from other interfaces**, just like classes can inherit from other classes.
> This concept is known as **Interface Inheritance**.

When one interface inherits another, it **extends** the contract — meaning any class that implements the *child interface* must also implement all members of the *parent interface(s)*.

```csharp
interface IParent
{
    void ParentMethod();
}

interface IChild : IParent
{
    void ChildMethod();
}
```

Here, `IChild` inherits from `IParent`.
So, any class implementing `IChild` must provide **definitions for both** `ParentMethod()` and `ChildMethod()`.

##  **Example: Interface Inheritance**

```csharp
interface IReadable
{
    void Read();
}

interface IWritable : IReadable
{
    void Write();
}

class Document : IWritable
{
    public void Read()
    {
        Console.WriteLine("Reading document...");
    }

    public void Write()
    {
        Console.WriteLine("Writing document...");
    }
}
```

* `IWritable` inherits from `IReadable`.
* The `Document` class implements `IWritable`, so it must implement **both `Read()` and `Write()`**.
* Interface inheritance helps group related functionalities together logically.

--- 
##  **Key Points**

1. **An interface can inherit from one or more interfaces.**
   C# allows **multiple interface inheritance**, unlike classes.

2. **All inherited members become part of the derived interface.**
   A class implementing the derived interface must implement **all members** from every parent interface.

3. **Interfaces cannot inherit from classes** —
   they can only inherit from **other interfaces**.

4. **All interface members are implicitly public** —
   you don’t need to (and can’t) specify access modifiers.

## **Multiple Interface Inheritance**

C# supports **multiple inheritance for interfaces**, even though it doesn’t allow it for classes.
This allows developers to build **composite contracts** combining multiple capabilities.

```csharp
interface IReadable
{
    void Read();
}

interface IWritable
{
    void Write();
}

interface IFile : IReadable, IWritable
{
    void Open();
}

class FileManager : IFile
{
    public void Read()
    {
        Console.WriteLine("Reading file...");
    }

    public void Write()
    {
        Console.WriteLine("Writing file...");
    }

    public void Open()
    {
        Console.WriteLine("Opening file...");
    }
}
```

##  **Interface vs Class Inheritance**

| Feature                           | Class Inheritance              | Interface Inheritance     |
| --------------------------------- | ------------------------------ | ------------------------- |
| **Keyword**                       | `:`                            | `:`                       |
| **Multiple inheritance allowed?** | No                             | Yes                       |
| **Can have implementation?**      |  Yes (in base class)           | No (C# 7.0 and below)     |
| **Can inherit from class?**       | Yes                            | No                        |
| **Access modifiers?**             | Can be public, protected, etc. | All are implicitly public |

##  **Why Use Interface Inheritance?**

| Purpose                                   | Benefit                              |
| ----------------------------------------- | ------------------------------------ |
| To group related functionalities          | Better code organization             |
| To create flexible and extensible systems | Enables code reuse through contracts |
| To support multiple capabilities          | Use multiple inheritance safely      |
| To improve abstraction                    | Defines “what” without “how”         |
| To simplify polymorphism<br>              | Unified interface-based calls        |

--- 

# **Declaring Properties within Interfaces in C#**

> In C#, **interfaces** not only define **methods** but can also define **properties**, **indexers**, and **events**.
> Declaring a property in an interface is like **specifying a contract** — it tells that *any class implementing that interface must define how that property works.*

An interface doesn’t contain **implementation** of the property — only its **signature**.
The **get** and/or **set** accessors are declared, but no actual logic is written inside them.

##  **Syntax**

```csharp
interface IInterfaceName
{
    // Property declaration (no body)
    DataType PropertyName { get; set; }
}
```

Then a class implements it as:

```csharp
class ClassName : IInterfaceName
{
    private DataType _field;

    public DataType PropertyName
    {
        get { return _field; }
        set { _field = value; }
    }
}
```

##  **Purpose of Declaring Properties 

Declaring properties inside an interface ensures that:

* The implementing class **exposes specific data** or **state information**.
* All classes that implement that interface **maintain a consistent structure**.
* The interface acts as a **blueprint for data access** in addition to methods.

Basically, it defines **what data** must be accessible — not **how** it’s stored or managed.

##  **Example : Simple Property in an Interface**

```csharp
interface IEmployee
{
    int EmployeeId { get; set; }
    string Name { get; set; }
}

class Developer : IEmployee
{
    public int EmployeeId { get; set; }
    public string Name { get; set; }

    public void DisplayInfo()
    {
        Console.WriteLine($"ID: {EmployeeId}, Name: {Name}");
    }
}
```

* `IEmployee` declares two properties: `EmployeeId` and `Name`.
* `Developer` implements `IEmployee` and must define both properties.
* The class can now store and manipulate employee details, while still conforming to the contract.

##  **Properties in Interfaces vs Classes**

| Feature                     | Interface Property      | Class Property                                |
| --------------------------- | ----------------------- | --------------------------------------------- |
| **Implementation Allowed?** | ❌ No (only declaration) | ✅ Yes (get/set bodies allowed)                |
| **Access Modifiers**        | Implicitly `public`     | Can be `private`, `public`, `protected`, etc. |
| **Purpose**                 | Defines contract        | Defines actual data access                    |

## takeaway: 
Declaring properties within interfaces allows developers to define **data access contracts** without specifying implementation.
It ensures **consistency**, **abstraction**, and **polymorphism** across related classes.

--- 
# **Namespaces in C#**

> In C#, a **namespace** is a way to **organize and group related classes, interfaces, structures, and other types** together.
> Think of it like a **folder** in your computer — it helps keep your code **clean, readable, and free of naming conflicts.**


### Definition: 
A **namespace** is a **declarative region** that provides a scope to the identifiers (the names of types, functions, variables, etc.) inside it.

* It’s used to **logically group code**.
* It helps **avoid naming collisions** between different parts of large projects.

##  **Syntax**

```csharp
namespace NamespaceName
{
    // Classes, structs, enums, interfaces, etc.
    class ClassName
    {
        // code
    }
}
```

You can use multiple namespaces in one program, or even nest them.

##  **Example 

```csharp
namespace Company
{
    class Employee
    {
        public void Display()
        {
            Console.WriteLine("Inside Company namespace");
        }
    }
}

class Program
{
    static void Main()
    {
        Company.Employee emp = new Company.Employee();
        emp.Display();
    }
}
```

* The class `Employee` is inside the `Company` namespace.
* To access it from outside, you must use the **namespace name** (`Company.Employee`).

##  **Using Directive**

Typing the full name every time can get long, so C# lets you use the **`using`** keyword.

```csharp
using Company.Department;

class Program
{
    static void Main()
    {
        Developer dev = new Developer();
        dev.Work();
    }
}
```

 Now you don’t need to prefix `Company.Department` everywhere.

##  **System Namespace**

The .NET Framework provides a large built-in namespace called `System`.

```csharp
using System;

class Program
{
    static void Main()
    {
        Console.WriteLine("Hello World!");
    }
}
```

Here, `Console` is defined inside the **`System`** namespace.
That’s why we add `using System;` at the top of most programs.

##  **Namespaces vs Classes**

| Feature               | Namespace                           | Class                         |
| --------------------- | ----------------------------------- | ----------------------------- |
| **Purpose**           | Organize code logically             | Define data and behavior      |
| **Can Contain**       | Classes, structs, enums, interfaces | Fields, methods, properties   |
| **Memory Allocation** | No                                  | Yes, when objects are created |
| **Access Syntax**     | `NamespaceName.ClassName`           | `ClassName.MethodName`        |
| **Keyword**           | `namespace`                         | `class`                       |

##  **Advantages of Namespaces**

1.  **Organization:** Keeps related classes and types grouped together.
2.  **Avoids Name Conflicts:** Prevents clashes between classes with same names in different modules.
3.  **Code Readability:** Makes large applications easier to navigate.
4.  **Reusability:** Encourages modular design and reusability of code.
5.  **Maintainability:** Simplifies debugging and updates in large projects.

--- 
# **Creating and Using Generic Classes in C#**

> **Generics** in C# allow you to define **classes, methods, interfaces, and structures** with a **placeholder type parameter**, instead of fixing the data type upfront.

They enable **type-safe**, **reusable**, and **efficient** code by allowing you to create a single class or method that works with any data type.

Example: Instead of writing separate classes for integers, strings, or floats — you can write one generic class that handles all.

## **Definition**

A **Generic Class** is a class that takes a **type parameter** when it is declared or instantiated.

```csharp
class ClassName<T>
{
    // T is a type parameter (placeholder for any data type)
    private T data;

    public void Add(T value)
    {
        data = value;
    }

    public T Get()
    {
        return data;
    }
}
```

* `T` is a **type parameter** (can be anything — `int`, `string`, `float`, custom class, etc.).
* It acts like a variable for the data type.

##  **Example: Creating and Using a Generic Class**

```csharp
using System;

class Box<T>
{
    private T content;

    public void Add(T item)
    {
        content = item;
    }

    public T GetContent()
    {
        return content;
    }
}

class Program
{
    static void Main()
    {
        // Create a Box of integers
        Box<int> intBox = new Box<int>();
        intBox.Add(10);
        Console.WriteLine(intBox.GetContent());   // Output: 10

        // Create a Box of strings
        Box<string> strBox = new Box<string>();
        strBox.Add("Hello Generics");
        Console.WriteLine(strBox.GetContent());   // Output: Hello Generics
    }
}
```

* The same class `Box<T>` is used to store different data types.
* `<int>` and `<string>` specify the type at object creation.
* The compiler ensures **type safety** — you can’t mix types accidentally.

##  **Why Use Generic Classes?**

### 1. **Type Safety**

Ensures that the object type is consistent — no need for explicit type casting.

```csharp
List<int> numbers = new List<int>();
numbers.Add(10);  // OK
// numbers.Add("abc"); ❌ Compile-time error
```

### 2. **Reusability**

You write the logic once, and reuse it for any data type.

### 3. **Performance**

Avoids **boxing and unboxing**, since types are known at compile time.

### 4. **Code Clarity**

Generics eliminate redundant code and make classes easy to read and maintain.

##  **Constraints in Generics**

Sometimes, you want to **restrict** what kind of types can be used in a generic class.
Use the **`where`** keyword to specify **constraints**.

```csharp
class Repository<T> where T : class
{
    // Only reference types allowed
}
```

### **Common Constraints**

| Constraint                | Meaning                                      |
| ------------------------- | -------------------------------------------- |
| `where T : struct`        | Only value types allowed                     |
| `where T : class`         | Only reference types allowed                 |
| `where T : new()`         | Must have a public parameterless constructor |
| `where T : BaseClass`     | Must inherit from `BaseClass`                |
| `where T : InterfaceName` | Must implement `InterfaceName`               |

##  **Generic vs Non-Generic Classes**

| Feature                   | Non-Generic              | Generic                              |
| ------------------------- | ------------------------ | ------------------------------------ |
| **Type Safety**           | No (requires casting)    | Yes                                  |
| **Performance**           | Slower (boxing/unboxing) | Faster                               |
| **Reusability**           | Limited                  | High                                 |
| **Compile-time Checking** | No                       | Yes                                  |
| **Example**               | `ArrayList`, `Hashtable` | `List<T>`, `Dictionary<TKey,TValue>` |

##  **takeaway**

* Generics let you define **type-independent** classes and methods.
* Generic classes improve **type safety**, **reusability**, and **performance**.
* Use **constraints (`where`)** to control what types can be used.
* Common in real-world use through collections like `List<T>` and `Dictionary<TKey, TValue>`.
