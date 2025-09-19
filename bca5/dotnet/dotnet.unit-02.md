# **Features of C# 7.0**

C# is a **modern, object-oriented programming language** developed by Microsoft and standardized by ECMA and ISO. It was designed to be **simple, type-safe, component-oriented, and versatile**, capable of supporting a wide range of applications such as desktop software, web applications, cloud services, and mobile apps.

Over time, different versions of C# introduced new features. By version **7.0**, the language had matured into a powerful and flexible tool that combines the productivity of high-level languages with the performance benefits of low-level control when needed.

## **Core Features of C# (General)**

1. **Simplicity**

   * C# syntax is clean and easy to understand, similar to C, C++, and Java.
   * It eliminates complex features like header files, macros, and pointers (in safe mode).

2. **Object-Oriented Programming (OOP)**

   * Supports key OOP principles: **Encapsulation, Inheritance, Polymorphism, and Abstraction**.
   * Everything in C# is based around objects and classes, ensuring modular and reusable code.

3. **Type-Safety**

   * C# enforces strict type checking at compile time.
   * Prevents illegal type conversions and protects memory with managed code under the CLR.

4. **Rich Standard Library**

   * Provides a vast **Base Class Library (BCL)** for collections, file I/O, networking, database access, and more.

5. **Modern and Versatile**

   * Supports a wide variety of application domains: Windows apps, Web (ASP.NET), cloud services, IoT, and mobile (via Xamarin).

6. **Automatic Memory Management**

   * Uses **Garbage Collection (GC)** to free unused memory automatically, reducing errors like memory leaks.

7. **Interoperability**

   * Can interact with existing code written in C, C++, or COM (Component Object Model).

8. **Component-Oriented**

   * Supports properties, events, delegates, and assemblies, making it ideal for component-based software engineering.

9. **Scalability and Versioning**

   * Well-suited for small-scale to enterprise-level applications.
   * Backward compatibility ensures older applications still run with newer versions.


C# is a **robust, modern, and type-safe language** designed to balance simplicity and power. It supports object-oriented principles, automatic memory management, strong security, and cross-platform development. With version 7.0, advanced features such as **tuples, pattern matching, and local functions** made the language even more expressive and developer-friendly.

# **C# Compilation and Execution**

C# is not directly compiled into machine code like traditional C or C++ programs. Instead, it follows the **.NET two-step execution model**:

1. **Compilation of source code into Intermediate Language (IL)**
2. **Execution of IL under the Common Language Runtime (CLR)** using the Just-In-Time (JIT) compiler.

This process makes C# programs **platform-independent, secure, and managed** while still delivering high performance.

## **Steps of Compilation and Execution**

### **1. Writing Source Code**

* A developer writes a C# program in a `.cs` file using a code editor (e.g., Visual Studio, Visual Studio Code).
* Example:

  ```csharp
  using System;

  class Hello
  {
      static void Main()
      {
          Console.WriteLine("Hello, C# Compilation and Execution!");
      }
  }
  ```

---

### **2. Compilation by C# Compiler (csc)**

* The C# compiler (`csc.exe`) translates the `.cs` source file into **Microsoft Intermediate Language (MSIL/IL)** and **metadata**.
* These are stored inside an **Assembly** (`.exe` or `.dll`).
* Metadata describes types, classes, methods, and security information.

👉 Output at this stage: **IL + Metadata packaged as an Assembly.**

---

### **3. Loading into the CLR**

* When the program is executed, the **CLR (Common Language Runtime)** loads the assembly into memory.
* CLR provides services such as:

  * Memory management (Garbage Collection)
  * Security
  * Exception handling
  * Thread management

---

### **4. JIT Compilation**

* The **Just-In-Time (JIT) compiler** translates IL into **native machine code** for the target operating system and hardware.
* This ensures the same IL can run on different platforms, provided a CLR exists there.

Types of JIT in .NET:

* **Pre-JIT**: Compiles entire code at once.
* **Normal JIT**: Compiles methods when called.
* **Econo-JIT**: Compiles only required methods and frees them later to save memory.

---

### **5. Execution of Native Code**

* After JIT compilation, the CLR executes the native code.
* Execution remains under CLR’s supervision, ensuring **type safety, memory safety, and exception handling.**

---

## **Compilation and Execution Flow (Step-by-Step)**

1. **C# Source Code (`.cs`)**
2. ⬇ Compiled by C# Compiler (`csc`)
3. **IL + Metadata → Assembly (`.exe` / `.dll`)**
4. ⬇ Loaded by CLR
5. **JIT Compiler → Native Machine Code**
6. ⬇ CLR Executes with runtime services

## **Example Walkthrough**

* Write `Hello.cs`.
* Compile:

  ```bash
  csc Hello.cs
  ```

  → Produces `Hello.exe` (contains IL + metadata).
* Run:

  ```bash
  Hello.exe
  ```

  → CLR loads the assembly, JIT compiles IL into native code, and executes it.

## **Advantages of This Model**

* **Portability** – IL can run on any machine with a CLR.
* **Security** – CLR enforces strict type and memory safety.
* **Optimization** – JIT compiles and optimizes code at runtime.
* **Language Interoperability** – Multiple .NET languages share the same IL and can work together.

# **General Structure of a C# Program**

Every C# program follows a well-defined structure that makes it easy to read, maintain, and execute under the .NET environment.
This structure is composed of namespaces, classes, methods, statements, and comments. Understanding the structure ensures that a program is syntactically correct and logically organized.

## **Basic Structure of a C# Program**

A simple C# program usually contains the following components:

1. **Namespace Declaration**

   * Groups related classes and code elements together.
   * Avoids name conflicts between classes from different libraries.
   * Example:

     ```csharp
     using System;   // Namespace for Console class
     ```

2. **Class Declaration**

   * C# is an **object-oriented language**, so all executable code must be inside a class.
   * The class is the container for methods, variables, and objects.
   * Example:

     ```csharp
     class Program { ... }
     ```

3. **Main Method**

   * Execution of every C# program begins with the **Main() method**.
   * Declared as:

     ```csharp
     static void Main(string[] args) { ... }
     ```
   * It may take an optional parameter `string[] args` for command-line arguments.
   * Must be declared as `static` since it is invoked by the CLR before any object is created.

4. **Statements and Expressions**

   * Inside the `Main()` method, we write statements that perform actions (printing, calculations, method calls).
   * Example:

     ```csharp
     Console.WriteLine("Hello, World!");
     ```

5. **Comments**

   * Used to explain code for better readability.
   * Types:

     * Single-line: `// comment`
     * Multi-line: `/* comment */`
     * XML Documentation: `/// comment`

---

## **Example of a Simple C# Program**

```csharp
// A simple C# program
using System;          // Namespace declaration

namespace HelloWorldApp // Custom namespace
{
    class Program       // Class declaration
    {
        static void Main(string[] args) // Main method
        {
            Console.WriteLine("Hello, World!"); // Statement
        }
    }
}
```


# **Creating and Using a DLL in C#**

In C#, a **DLL (Dynamic Link Library)** is a file that contains **compiled reusable code** such as classes, methods, and functions. Unlike an executable (`.exe`), a DLL cannot run by itself. Instead, it is referenced and used by other applications.

The purpose of using DLLs is to achieve **modularity, reusability, easy maintenance, and efficient memory usage**.

---
## **Steps for Creating a DLL**

1. **Create a Class Library Project**

   * In Visual Studio (or command-line with `csc`), choose *Class Library* project type.
   * The output of a Class Library project is a `.dll` file.

2. **Write the Code (Public Classes/Methods)**

   * Example:

     ```csharp
     using System;

     namespace MyLibrary
     {
         public class Calculator
         {
             public int Add(int a, int b)
             {
                 return a + b;
             }

             public int Multiply(int a, int b)
             {
                 return a * b;
             }
         }
     }
     ```

   * Here, `Calculator` is a class with public methods `Add` and `Multiply` which will be accessible to other programs.

3. **Build the Project**

   * Compiling this project produces a DLL file, e.g., `MyLibrary.dll`.
   * Using CLI:

     ```bash
     csc /target:library /out:MyLibrary.dll Calculator.cs
     ```
   * `/target:library` tells the compiler to create a DLL instead of an EXE.

---

## **Steps for Using a DLL**

1. **Reference the DLL**

   * In Visual Studio: Right-click project → Add Reference → Browse → Select `MyLibrary.dll`.
   * Using CLI:

     ```bash
     csc /reference:MyLibrary.dll Program.cs
     ```

2. **Import the Namespace**

   * Use `using` keyword to include the DLL’s namespace:

     ```csharp
     using System;
     using MyLibrary;
     ```

3. **Use the DLL Classes/Methods**

   * Example Program:

     ```csharp
     class Demo
     {
         static void Main()
         {
             Calculator calc = new Calculator();
             Console.WriteLine("Sum: " + calc.Add(10, 20));
             Console.WriteLine("Product: " + calc.Multiply(5, 4));
         }
     }
     ```

4. **Run the Program**

   * The compiler links the program with the DLL, and CLR executes it normally.

---

## **Advantages of DLLs**

* **Code Reusability** – Write once, use across multiple projects.
* **Modularity** – Large programs can be divided into manageable parts.
* **Easy Maintenance** – Update the DLL without changing the whole project.
* **Memory Efficiency** – Shared code is loaded into memory only once.


# **Data Types in C#**

Data types in C# define the **kind of data** that can be stored in a variable, how much memory it occupies, and what operations can be performed on it.
Being a **strongly typed language**, C# ensures that every variable must have a type declared at compile time. This improves **type safety, memory management, and error detection**.

---

## **Classification of Data Types**

C# data types are broadly divided into **three categories**:

1. **Value Types**
2. **Reference Types**
3. **Pointer Types** (unsafe context)

---

### **1. Value Types**

* Stored directly in **stack memory**.
* Contain actual data, not references.
* Examples: numeric types, structures, enumerations.

**a) Numeric Types**

* **Integral Types**:

  * `sbyte` (−128 to 127), `byte` (0 to 255),
  * `short` / `ushort`, `int` / `uint`, `long` / `ulong`.
* **Floating-Point Types**:

  * `float` (7 digits precision), `double` (15-16 digits).
* **Decimal Type**:

  * `decimal` (28-29 precision, for financial calculations).
* **Character Type**:

  * `char` (16-bit Unicode character).
* **Boolean Type**:

  * `bool` (true/false).

**b) Structs and Enums**

* `struct` → User-defined value type containing fields and methods.
* `enum` → Represents a set of named constants.

---

### **2. Reference Types**

* Store a **reference (address)** to the data, actual data is stored on the **heap**.
* Examples:

  * **Objects** (base type for all classes).
  * **String** (immutable sequence of characters).
  * **Arrays** (fixed-size collection of same type).
  * **Classes** (user-defined reference types).
  * **Delegates** (reference to methods).
  * **Interfaces** (define contracts for classes).

---

### **3. Pointer Types (Unsafe)**

* Represent memory addresses directly.
* Declared using `*` operator inside an **unsafe context**.
* Rarely used except in low-level memory operations.

---

## **Special Category: Nullable Types**

* Allow value types to represent a **null** state.
* Syntax: `int? x = null;`
* Useful in databases and optional data handling.

## **Summary Table of Common C# Data Types**

| []()Category   | Type                   | Example Declaration       | Size     | Example Value |
| -------------- | ---------------------- | ------------------------- | -------- | ------------- |
| Integral       | `int`                  | `int age = 25;`           | 4 bytes  | 25            |
| Floating Point | `float`                | `float pi = 3.14f;`       | 4 bytes  | 3.14          |
| Decimal        | `decimal`              | `decimal salary = 5000m;` | 16 bytes | 5000.00       |
| Character      | `char`                 | `char grade = 'A';`       | 2 bytes  | A             |
| Boolean        | `bool`                 | `bool status = true;`     | 1 byte   | true/false    |
| String         | `string`               | `string name = "John";`   | Varies   | "John"        |
| Array          | `int[]`                | `int[] nums = {1,2,3};`   | Varies   | {1,2,3}       |
| Enum           | `enum Days {Mon, Tue}` | -                         | Depends  | Days.Mon      |


# **Value Types and Reference Types in C#**

In C#, all variables and objects are classified into two broad categories: **Value Types** and **Reference Types**. This classification is fundamental because it determines **how data is stored in memory**, **how it is accessed**, and **how it behaves when assigned or passed to methods**.

---

### **1. Value Types**

* Value types **directly contain their data**.
* When a value type variable is created, the actual value is stored in the **stack memory**.
* Assigning one value type variable to another copies the value itself. This means the two variables work independently after the assignment.

**Examples:** All primitive data types (`int`, `float`, `double`, `char`, `bool`), `struct`, and `enum`.

**Syntax Example:**

```csharp
int a = 10;
int b = a;    // value of 'a' is copied into 'b'
b = 20;       // changing 'b' does not affect 'a'
Console.WriteLine(a);  // Output: 10
Console.WriteLine(b);  // Output: 20
```

**Key Characteristics:**

* Stored in stack memory.
* Assignment copies the value.
* Faster access due to stack allocation.
* Cannot be null unless declared as nullable (e.g., `int?`).

---

### **2. Reference Types**

* Reference types **store references (addresses)** to the actual data, not the data itself.
* The reference is stored in the **stack**, while the actual object is stored in the **heap**.
* Assigning one reference type variable to another copies the reference, meaning both variables point to the **same object in memory**. Any changes via one reference are visible through the other.

**Examples:** `class`, `object`, `string`, arrays, `interface`, delegates.

**Syntax Example:**

```csharp
class Person
{
    public string Name;
}

Person p1 = new Person();
p1.Name = "Alice";

Person p2 = p1;   // both p1 and p2 reference the same object
p2.Name = "Bob";

Console.WriteLine(p1.Name);  // Output: Bob
Console.WriteLine(p2.Name);  // Output: Bob
```

**Key Characteristics:**

* Reference stored in stack; object stored in heap.
* Assignment copies the reference, not the object.
* Supports null assignment (`Person p = null;`).
* Garbage collection manages heap memory for reference types.


# **Boxing and Unboxing in C#**

Boxing and Unboxing are **type conversion processes** in C# that allow data to move between **value types** and **reference types**. They are essential for understanding how C# manages memory when interacting with objects in the .NET Framework.

---
### **1. Boxing**

* **Definition:** Boxing is the process of **converting a value type into a reference type** by wrapping it inside a `System.Object`.
* During boxing, the value stored on the **stack** is copied to the **heap**, where it is stored as an object.
* Boxing is an **implicit conversion**, which means the compiler automatically handles it.

**Example:**

```csharp
int x = 42;              // value type stored on stack
object obj = x;          // boxing: x is wrapped into an object on heap

Console.WriteLine(obj);  // Output: 42
```

**Explanation:**
Here, the integer `x` (value type) is boxed into the object `obj` (reference type). Now `obj` contains a reference to the value stored on the heap.

---

### **2. Unboxing**

* **Definition:** Unboxing is the process of **extracting the value type from an object**.
* This operation requires **explicit casting**, as the compiler must ensure that the object really contains the correct value type.
* During unboxing, the value is **copied from the heap back to the stack**.

**Example:**

```csharp
object obj = 42;         // boxing
int y = (int)obj;        // unboxing (explicit cast)

Console.WriteLine(y);    // Output: 42
```

**Explanation:**
Here, the object `obj` contains a boxed integer. By explicitly casting `(int)obj`, the original value is unboxed and stored in `y`.

---

### **3. Key Characteristics**

* **Boxing:** Implicit conversion from value type → object (heap allocation).
* **Unboxing:** Explicit conversion from object → value type (stack retrieval).
* Incorrect unboxing (casting to the wrong type) throws an **InvalidCastException**.

**Example of Wrong Unboxing:**

```csharp
object obj = 42;
double d = (double)obj;   // Error: InvalidCastException at runtime
```


# **Single-Dimensional, Multi-Dimensional, and Jagged Arrays in C#**

Arrays in C# are **collections of elements of the same type** stored in a contiguous memory location. They allow efficient storage and retrieval of multiple values using indices. Arrays are objects in C#, derived from the **System.Array** class, and can be of three types: **Single-Dimensional**, **Multi-Dimensional**, and **Jagged Arrays**.

---

### **1. Single-Dimensional Arrays**

* Also called **one-dimensional arrays** or **linear arrays**.
* Elements are stored sequentially in a single row.
* Accessed using a **single index**.
* Syntax:

  ```csharp
  data_type[] array_name = new data_type[size];
  ```

**Example:**

```csharp
int[] numbers = new int[5];    // Declaration of array with size 5
numbers[0] = 10;               // Assigning values
numbers[1] = 20;

foreach (int n in numbers)
    Console.WriteLine(n);
```

**Explanation:** Here, `numbers` is a single-dimensional array holding five integers. Indexing starts from **0**.

### **2. Multi-Dimensional Arrays**

* Arrays with more than one dimension.
* Most commonly used: **two-dimensional arrays (matrices)**.
* Represented in a **rows × columns** structure.
* Syntax:

  ```csharp
  data_type[,] array_name = new data_type[rows, columns];
  ```

**Example:**

```csharp
int[,] matrix = new int[2, 3];   // 2 rows, 3 columns
matrix[0, 0] = 1;
matrix[0, 1] = 2;
matrix[1, 2] = 6;

for (int i = 0; i < 2; i++)
{
    for (int j = 0; j < 3; j++)
        Console.Write(matrix[i, j] + " ");
    Console.WriteLine();
}
```

**Explanation:** The array `matrix` is two-dimensional with 2 rows and 3 columns. Elements are accessed using **two indices**: `[row, column]`. Higher dimensions (3D, 4D, etc.) are also supported.

### **3. Jagged Arrays**

* A **“jagged” array is an array of arrays**.
* Each sub-array can have a **different length**, unlike multi-dimensional arrays where each row has the same number of columns.
* Syntax:

  ```csharp
  data_type[][] array_name = new data_type[rows][];
  ```

**Example:**

```csharp
int[][] jagged = new int[3][];    // 3 rows
jagged[0] = new int[2];           // First row has 2 elements
jagged[1] = new int[4];           // Second row has 4 elements
jagged[2] = new int[3];           // Third row has 3 elements

jagged[0][0] = 10;
jagged[1][2] = 30;

for (int i = 0; i < jagged.Length; i++)
{
    for (int j = 0; j < jagged[i].Length; j++)
        Console.Write(jagged[i][j] + " ");
    Console.WriteLine();
}
```

**Explanation:** The `jagged` array consists of three sub-arrays of varying lengths. Each element is accessed with **two indices**: `[row][column]`.


# **Nullable Types in C#**

In C#, all **value types** (such as `int`, `float`, `bool`, etc.) are **non-nullable by default**, meaning they must always contain a value. Unlike reference types (e.g., `string`, `object`), which can hold `null`, value types cannot directly represent the absence of a value.

To address scenarios where a value type may not always have a meaningful value (e.g., database fields, optional inputs), C# introduced **nullable types**.

---

### **1. Definition**

- A **nullable type** allows value types to represent all their normal values **plus an additional `null` value**.
    
- Declared using the **`?` modifier** after the value type.
    
- Internally, a nullable type is an instance of the generic structure `System.Nullable<T>`.
    

**Syntax:**

```csharp
int? x = null;          // Nullable integer
bool? flag = null;      // Nullable boolean
```

This means `x` can hold any integer value **or** `null`.

---

### **2. Creating Nullable Types**

- **Shorthand syntax:**
```csharp
	int? num = null;
```

- **Using `System.Nullable<T>`:**
```csharp
	Nullable<int> num = null;
```


### **3. Accessing Nullable Values**

Nullable types have two key properties:

- **`.HasValue`** → returns `true` if the variable is not `null`.

- **`.Value`** → returns the value if present, otherwise throws an exception.

**Example:**

```csharp
int? a = 10;
int? b = null;

Console.WriteLine(a.HasValue);   // True
Console.WriteLine(b.HasValue);   // False

Console.WriteLine(a.Value);      // 10
// Console.WriteLine(b.Value);   // Error: InvalidOperationException
```

### **Use Cases of Nullable Types**

- **Database programming:** Columns often allow `NULL`, and nullable types in C# map directly to such fields.
    
- **Optional values:** Useful in methods where a parameter may or may not have a value.
    
- **Defensive programming:** Helps represent “no value” scenarios without relying on arbitrary defaults.

# **Implicitly Typed Local Variables in C#**

In C# 3.0 and later, the compiler allows **type inference** for local variables using the `var` keyword.
This means the compiler automatically determines the type of a variable at **compile time** based on the value assigned to it, eliminating the need to explicitly specify the data type.

> Note: Despite being called “implicitly typed,” the type is **strongly typed and fixed at compile time**. It is **not dynamic**.

### **1. Syntax**

```csharp
var variableName = value;
```

* The type of `variableName` is inferred from the `value`.
* It can only be used for **local variables inside methods**.
* The variable **must be initialized** at the time of declaration.

### Examples

```csharp
var number = 10;         // Compiler infers 'int'
var name = "Sushh";      // Compiler infers 'string'
var price = 99.99;       // Compiler infers 'double'
var isActive = true;     // Compiler infers 'bool'
```

* Invalid Example:

```csharp
var x;                   // Error: must initialize at declaration
```

### **3. Key Characteristics**

1. **Strongly Typed:** After compilation, `var number` behaves exactly as `int number`.
2. **Readability:** Reduces redundancy, especially for complex types like generics:

   ```csharp
   Dictionary<string, List<int>> studentScores = new Dictionary<string, List<int>>();
   // can be simplified as
   var studentScores = new Dictionary<string, List<int>>();
   ```
3. **Local Scope Only:** `var` cannot be used as **class fields, method return types, or parameters**.
4. **Compile-Time Type Checking:** The compiler still enforces type rules; you cannot assign a value of a different type later.

### **Important Notes**

* `var` **cannot be assigned null directly** because the compiler cannot infer type:

  ```csharp
  var x = null;  // Error
  ```
* Using `var` **does not make it dynamic**; type is fixed once inferred.


# **Var vs Dynamic in C#**

Both `var` and `dynamic` in C# allow flexible variable declaration, but they **behave very differently** in terms of **type checking, compilation, and runtime behavior**.

## **1. `var` (Implicitly Typed Local Variable)**

* **Definition:** `var` allows the compiler to **infer the type at compile time** based on the value assigned.
* The **type is fixed at compile time** and cannot change later.
* Only usable for **local variables** inside methods.

**Example:**

```csharp
var num = 10;      // Compiler infers 'int'
num = 20;          // Valid
// num = "Hello";  // Error: cannot assign string to int
```

## **2. `dynamic`**

* **Definition:** `dynamic` allows variables whose **type is resolved at runtime** rather than at compile time.
* Operations on `dynamic` variables are **not checked by the compiler**, so errors appear only at runtime.
* Can be assigned **any type**, including `null`.

**Example:**

```csharp
dynamic data = 10;   
Console.WriteLine(data);  // Output: 10

data = "Hello";           // Valid, type changes at runtime
Console.WriteLine(data);  // Output: Hello
```

## **Comparison Table**

| Feature                 | `var`                            | `dynamic`                             |
| ----------------------- | -------------------------------- | ------------------------------------- |
| Type Inference          | At compile time                  | At runtime                            |
| Type Safety             | Strongly typed                   | Weakly typed / runtime checked        |
| Type Change             | Not allowed after initialization | Allowed at runtime                    |
| Initialization Required | Yes                              | No                                    |
| Scope                   | Local variables only             | Local, fields, properties, parameters |
| Example                 | `var x = 10;`                    | `dynamic x = 10; x = "Hello";`        |
### **When to Use**

[]()* **`var`:** Use when the type is obvious or complex (e.g., generics, LINQ queries). Provides **compile-time safety**.
* **`dynamic`:** Use when the type is **not known until runtime**, e.g., working with COM objects, JSON, or reflection.

# **`is` and `as` Operators in C#**

In C#, **type conversion and type-checking** are common operations. The `is` and `as` operators are specially designed to **safely check or cast object types** without risking runtime exceptions.

## **1. `is` Operator**

### **Definition:**

* The `is` operator **checks whether an object is compatible with a given type**.
* Returns a **Boolean (`true` or `false`)**.
* Useful to verify type before performing type-specific operations.

### **Syntax:**

```csharp
object obj;
bool result = obj is TypeName;
```

### **Example:**

```csharp
object obj = "Hello World";

if (obj is string)
{
    Console.WriteLine("obj is a string");
}
else
{
    Console.WriteLine("obj is not a string");
}
```

**Output:**

```
obj is a string
```

## **2. `as` Operator**

### **Definition:**

* The `as` operator **casts an object to a given reference type or nullable type**.
* Returns `null` **instead of throwing an exception** if the cast fails.
* Works only with **reference types and nullable types**.

### **Syntax:**

```csharp
TypeName obj = anotherObj as TypeName;
```

### **Example:**

```csharp
object obj = "Hello";

string str = obj as string;   // Successful cast
Console.WriteLine(str);       // Output: Hello

object num = 123;
string s = num as string;     // Unsuccessful cast
Console.WriteLine(s == null); // Output: True
```

**Explanation:**
`as` avoids `InvalidCastException` by returning `null` if the object cannot be converted to the specified type.

## **Key Differences Between `is` and `as`**

| Feature          | `is` Operator                       | `as` Operator                           |
| ---------------- | ----------------------------------- | --------------------------------------- |
| Purpose          | Checks type compatibility (Boolean) | Performs safe type casting              |
| Returns          | `true` / `false`                    | Object of type or `null`                |
| Throws Exception | No                                  | No                                      |
| Applicable Types | Value types and reference types     | Reference types and nullable types only |
| Example          | `obj is string`                     | `obj as string`                         |

# **`ref` vs `out` Keywords in C#**

Both `ref` and `out` are used to **pass arguments by reference** to methods.
That means the method works with the **same memory location** of the variable, not a copy.

But — there are key **differences**.

## **1. `ref` Keyword**

### **Definition:**

* `ref` allows **passing a variable by reference**.
* The **caller must initialize** the variable before passing.
* The method can **read and modify** the value.

### **Syntax:**

```csharp
MethodName(ref variableName);
```

### **Example:**

```csharp
using System;

class Program
{
    static void AddFive(ref int num)
    {
        num += 5;
    }

    static void Main()
    {
        int value = 10;
        AddFive(ref value);
        Console.WriteLine(value);  // Output: 15
    }
}
```

---

## **2. `out` Keyword**

### **Definition:**

* `out` also passes a variable by reference.
* The **caller does not need to initialize** the variable before passing.
* The method **must assign a value** before the method ends.

### **Syntax:**

```csharp
MethodName(out variableName);
```

### **Example:**

```csharp
using System;

class Program
{
    static void GetValues(out int a, out int b)
    {
        a = 10;
        b = 20;
    }

    static void Main()
    {
        int x, y;  // not initialized
        GetValues(out x, out y);
        Console.WriteLine($"x = {x}, y = {y}"); // Output: x = 10, y = 20
    }
}
```

## **3. Key Differences Between `ref` and `out`**

| Feature                    | `ref`                                     | `out`                                |
| -------------------------- | ----------------------------------------- | ------------------------------------ |
| Initialization before call | Must be initialized                       | Not required                         |
| Assignment inside method   | Optional                                  | Mandatory (must assign value)        |
| Purpose                    | Pass already existing data, allow changes | Return multiple values from a method |
| Usage scenario             | When method modifies existing value       | When method gives back values        |
## **Summary**

* `ref` = initialized before call, modified optionally.
* `out` = not initialized, **must be assigned** inside method.
* Both = pass variables **by reference** (same memory).


# **The `object` Base Class in .NET**

In the .NET Framework (including C#), **all types are derived from a single root class called `System.Object` (commonly written as `object`)**.
This means whether we are dealing with **value types** (like `int`, `double`, `struct`) or **reference types** (like `class`, `string`, `array`), they all inherit, directly or indirectly, from the `object` class.

Thus, `object` is the **ultimate base class** of the .NET type system, ensuring a **unified type hierarchy**.

### **2. Key Points**

* **Namespace**: `System`
* **Assembly**: `mscorlib.dll` (for .NET Framework) / `System.Private.CoreLib.dll` (for .NET Core/.NET 5+)
* All types, regardless of being user-defined or built-in, can be treated as `object`.
* Provides **basic services** like equality comparison, object lifetime control, and conversion to string.

### **3. Methods Defined in `object`**

The `object` class defines several fundamental methods that are inherited by all .NET types.

1. **`Equals(Object obj)`**

   * Determines whether the current instance is equal to another object.
   * Can be overridden for custom equality logic.

   ```csharp
   int a = 5, b = 5;
   Console.WriteLine(a.Equals(b));  // True
   ```

2. **`GetHashCode()`**

   * Provides a numerical value (hash code) corresponding to the object.
   * Used in hashing algorithms (e.g., dictionaries).

3. **`ToString()`**

   * Returns a string representation of the object.
   * Default: fully qualified type name.
   * Usually overridden for meaningful output.

   ```csharp
   class Student 
   {
       public string Name { get; set; }
       public override string ToString() => $"Student: {Name}";
   }
   ```


# **`Equals()` vs `==` in C#**

In C#, both `Equals()` and `==` are used to **compare objects or values**, but they are **not the same thing**.
Their behavior depends on whether the type is a **value type** or a **reference type**, and whether the operators are **overridden** in that type.

---

### **2. `Equals()` Method**

* Defined in the **`System.Object`** base class.
* Virtual method: can be **overridden** in user-defined types.
* Compares **contents (values)** by default for **value types**, and **references (addresses)** for reference types unless overridden.
* Commonly overridden in classes like `string`, where equality means *same sequence of characters*.

**Example:**

```csharp
int a = 10, b = 10;
Console.WriteLine(a.Equals(b));   // True (compares values)

object obj1 = new object();
object obj2 = new object();
Console.WriteLine(obj1.Equals(obj2));  // False (different references)
```

---

### **3. `==` Operator**

* Behavior depends on the type:

  * For **value types** (like `int`, `double`), `==` compares **values**.
  * For **reference types**, `==` by default compares **reference identity** (memory addresses).
* Can be **overloaded** in user-defined classes to provide custom behavior.

**Example:**

```csharp
int x = 5, y = 5;
Console.WriteLine(x == y);   // True (values compared)

[]()string s1 = "hello";
string s2 = "hello";
Console.WriteLine(s1 == s2); // True (string overrides == to compare content)

object o1 = new object();
object o2 = new object();
Console.WriteLine(o1 == o2); // False (different references)
```

### **Special Case: `string`**

`string` in C# **overrides both `Equals()` and `==`**, so they both check **content equality**, not reference.

```csharp
string a = "dotnet";
string b = new string("dotnet".ToCharArray());
Console.WriteLine(a.Equals(b)); // True
Console.WriteLine(a == b);      // True (because string overloads ==)
```

# **String vs StringBuilder in C#**

In C#, both `String` and `StringBuilder` represent sequences of characters, but they differ fundamentally in **mutability**.  
- **`String`**: Immutable (cannot be changed after creation).  
- **`StringBuilder`**: Mutable (can be modified without creating new objects).  

This difference makes them suitable for different scenarios in terms of **performance** and **memory management**.  

---

### **2. String**
- Defined in **`System.String`** (alias: `string`).  
- **Immutable**: Once created, it cannot be changed. Any modification creates a **new string object** in memory.  
- Common operations: concatenation, substring, comparison, searching, etc.  
- Suitable when the number of string manipulations is **low** or data is **constant**.  

**Example:**
```csharp
string s1 = "Hello";
string s2 = s1 + " World";  // Creates a new object
Console.WriteLine(s2);      // Output: Hello World
```

Here, the original `s1` remains unchanged; `s2` points to a new object.  

---

### **3. StringBuilder**
- Defined in **`System.Text.StringBuilder`**.  
- **Mutable**: Modifications happen on the same object (no new object creation).  
- Useful when performing **frequent string manipulations** (loops, concatenation, replacement).  
- Provides methods like `Append()`, `Insert()`, `Remove()`, `Replace()`, `Clear()`.  

**Example:**
```csharp
using System.Text;

StringBuilder sb = new StringBuilder("Hello");
sb.Append(" World");     // Modifies the same object
Console.WriteLine(sb);   // Output: Hello World
```

Unlike `string`, this does not create multiple objects in memory.  

### Key Differences

| Feature           | String (`System.String`)           | StringBuilder (`System.Text.StringBuilder`) |
| ----------------- | ---------------------------------- | ------------------------------------------- |
| Mutability        | Immutable                          | Mutable                                     |
| Memory usage      | Creates new object on modification | Modifies existing object                    |
| Performance       | Slower for repeated changes        | Faster for repeated modifications           |
| Namespace         | `System`                           | `System.Text`                               |
| Methods available | Concatenation, Substring, Compare  | Append, Insert, Remove, Replace, Clear      |
| Suitable for<br>  | Small/constant text data           | Large/repetitive modifications              |

- **Use `string`** when data is fixed or modifications are rare.  
- **Use `StringBuilder`** when working with large texts or frequent concatenations.  
- Both are important to ensure **performance optimization** in .NET applications.  

# **Various String Class Methods in C#**

The `String` class in C# (defined in the `System` namespace) represents a sequence of characters.
Strings are **immutable**, meaning any modification creates a new string object.
To work with strings effectively, the `String` class provides a wide range of methods for **searching, comparison, manipulation, and formatting**.

### ** Commonly Used `String` Methods**

#### **(a) Length Property**

* Returns the total number of characters in the string.

```csharp
string s = "DotNet";
Console.WriteLine(s.Length);  // Output: 6
```

---

#### **(b) ToUpper() / ToLower()**

* Converts all characters to **uppercase** or **lowercase**.

```csharp
string name = "CSharp";
Console.WriteLine(name.ToUpper());  // CSHARP
Console.WriteLine(name.ToLower());  // csharp
```

---

#### **(c) Trim(), TrimStart(), TrimEnd()**

* Removes whitespace (or specified characters) from the start and/or end of the string.

```csharp
string text = "   hello   ";
Console.WriteLine(text.Trim());       // "hello"
Console.WriteLine(text.TrimStart());  // "hello   "
Console.WriteLine(text.TrimEnd());    // "   hello"
```

---

#### **(d) Substring(int startIndex, int length)**

* Extracts a portion of the string starting at a given index.

```csharp
string s = "Programming";
Console.WriteLine(s.Substring(0, 6)); // "Progra"
```

---

#### **(e) Contains(string value)**

* Returns `true` if the string contains the specified value.

```csharp
string s = "C# Programming";
Console.WriteLine(s.Contains("Pro")); // True
```

---

#### **(f) IndexOf() / LastIndexOf()**

* Finds the position of the first or last occurrence of a character or substring.

```csharp
string s = "hello world";
Console.WriteLine(s.IndexOf("o"));     // 4
Console.WriteLine(s.LastIndexOf("o")); // 7
```

---

#### **(g) Replace(string oldValue, string newValue)**

* Replaces all occurrences of one substring with another.

```csharp
string s = "I like Java";
Console.WriteLine(s.Replace("Java", "C#")); // I like C#
```

---

#### **(h) Split(char\[])**

* Splits the string into an array of substrings based on a delimiter.

```csharp
string fruits = "apple,banana,grape";
string[] arr = fruits.Split(',');
foreach (string f in arr)
    Console.WriteLine(f);
```

