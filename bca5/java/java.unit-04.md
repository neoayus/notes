# **Introduction to Exception Handling**

In Java, **exception handling** is a mechanism that allows programmers to detect, respond to, and recover from runtime errors in an organized and predictable way. The term _exception_ refers to an event that disrupts the normal sequence of instructions in a program. These exceptions occur when the Java Virtual Machine (JVM) encounters an abnormal condition during execution — such as dividing a number by zero, accessing a file that doesn’t exist, or using a null reference.

Without exception handling, a single runtime error can cause an entire program to terminate unexpectedly, resulting in data loss or poor user experience. Java’s structured approach allows developers to manage such events gracefully by separating the **normal execution logic** from the **error-handling logic**.

---
## **Need for Exception Handling**

Every program, no matter how carefully written, is prone to errors. These errors may arise due to **programmer mistakes**, **invalid user input**, **hardware failures**, or **unavailable system resources**.

Earlier languages handled such errors through return codes or manual checks, which cluttered the code and made it hard to maintain. Java improved upon this by introducing an _object-oriented_ approach where every exception is represented by an **object**.

Exception handling provides the following advantages:

1. **Maintains program stability:** Prevents abrupt termination by catching and handling exceptions.
   
2. **Improves readability:** Separates regular logic from error-handling code.
   
3. **Promotes debugging and maintenance:** The exception object carries detailed information about the error — including its type, cause, and location.
   
4. **Ensures resource management:** Through the use of `finally` blocks, resources like files and network connections can be safely closed.
   
---

## **Definition of an Exception**

An **exception** is an _object_ that describes an error condition or an unexpected event that occurs during the execution of a program.  
When an exception arises, the **JVM creates an object** representing that error and **throws** it. If the program has an appropriate **handler**, it can **catch** and manage the exception; otherwise, the JVM terminates the program and prints a descriptive error message.

---

## **Exception Hierarchy**

All exception classes in Java are derived from the **`Throwable`** class.  
The hierarchy is as follows:

```
java.lang.Object
   └── java.lang.Throwable
         ├── java.lang.Error
         └── java.lang.Exception
               ├── java.lang.RuntimeException
               └── (Other Checked Exceptions)
```

### **1. Error**

- Represents serious problems beyond the control of the application.

- sually indicates system-level failures such as memory exhaustion.

- Should not be caught or handled by the program.

- Examples: `OutOfMemoryError`, `StackOverflowError`.
   

### **2. Exception**

- Represents conditions that a program _might_ want to catch and handle.
   
- Divided into:
   - **Checked Exceptions:** Checked at compile-time; the compiler ensures they are either handled or declared.
   - Examples: `IOException`, `SQLException`.
   
  - **Unchecked Exceptions (Runtime Exceptions):** Checked only at runtime, generally arising from logical errors.
   - Examples: `NullPointerException`, `ArithmeticException`, `ArrayIndexOutOfBoundsException`.


**Mnemonic:**

> _Checked = compile-time concern._  
> _Unchecked = programmer’s logic concern._

---

## **How Exception Handling Works**

The process of handling exceptions in Java follows a well-defined flow:

1. **Exception Occurs:** An abnormal condition arises in the program.
   
2. **Exception Object Created:** JVM creates an object of the appropriate exception class.
   
3. **Throwing the Exception:** The exception is thrown to the JVM or the calling method using the `throw` keyword.
   
4. **Catching the Exception:** The program searches for a suitable `catch` block to handle the exception.
   
5. **Normal Flow Resumes:** If caught, the program continues from the statement after the catch block; otherwise, the program terminates.
   
---

## **Exception Handling Keywords**

Java provides five specific keywords to manage exceptions effectively:

| Keyword   | Purpose                                                                                 |
| --------- | --------------------------------------------------------------------------------------- |
| `try`     | Defines a block that contains code that may throw an exception.                         |
| `catch`   | Defines a block that handles the exception thrown by the `try` block.                   |
| `finally` | Defines a block that executes regardless of whether an exception occurs or not.         |
| `throw`   | Used to explicitly throw an exception.                                                  |
| `throws`  | Declares exceptions that a method may throw, allowing them to be handled by the caller. |

---

## **Syntax and Control Flow**

```java
try {
    // Risky code that may throw an exception
    int result = 10 / 0;
}
catch (ArithmeticException e) {
    // Handling the specific exception
    System.out.println("Error: Division by zero is not allowed.");
}
finally {
    // Executes whether or not an exception occurred
    System.out.println("Execution completed.");
}
```

### **Explanation:**

- The JVM executes the `try` block first.
- When an exception occurs, normal flow halts and control transfers to the matching `catch` block.
- If no exception occurs, `catch` is skipped.
- The `finally` block always executes, commonly used for cleanup operations.


**Note:**  
Once an exception is caught, remaining code inside the `try` block is skipped.

## **Flow Diagram (Mental Visualization)**

```
        ┌─────────────┐
        │ Try Block   │
        └──────┬──────┘
               │
               ▼
         Exception occurs?
           /          \
        Yes            No
        │              │
        ▼              ▼
   Match found?       Continue
     /     \
   Yes      No
   │        │
   ▼        ▼
Catch Block  JVM Terminates
   │
   ▼
Finally Block Executes
```

---

## **Advantages of Exception Handling**

1. **Improved Program Reliability:** Prevents abrupt crashes.
   
2. **Simplified Code Maintenance:** Error-handling logic is modularized.
   
3. **Error Propagation:** Exceptions can be passed up the call stack for centralized handling.
   
4. **Resource Safety:** Ensures cleanup of resources (files, DB connections, etc.).
  
5. **Debugging Assistance:** Exception objects provide stack trace details that aid in debugging.
   

---
----

# **Types of Exceptions in Java**

In Java, all exceptions are objects derived from the class **`java.lang.Throwable`**. The `Throwable` class has two direct subclasses: **`Error`** and **`Exception`**.

While both represent abnormal conditions, their **purpose and handling mechanisms differ**.

* **Errors** usually indicate serious system-level problems that are *not meant to be handled by applications.*
* **Exceptions** represent conditions that can be *anticipated, caught, and handled* during program execution.

Thus, exceptions are classified into **three main categories**:

1. **Checked Exceptions**
2. **Unchecked Exceptions (Runtime Exceptions)**
3. **Errors**

---

## **1. Checked Exceptions**

Checked exceptions are those that are **checked by the compiler at compile time**. This means the Java compiler ensures that such exceptions are either **handled using a `try-catch` block** or **declared in the method’s signature using the `throws` keyword**.

If a checked exception is not handled properly, the code will **fail to compile**.

These exceptions generally occur due to **external factors beyond the program’s control** — such as input/output failures, missing files, or network problems.

---

### **Common Examples**

* `IOException` – When an input/output operation fails.
* `FileNotFoundException` – When the specified file does not exist.
* `SQLException` – When database access errors occur.
* `ClassNotFoundException` – When an application tries to load a class that cannot be found.
* `InterruptedException` – When a thread is interrupted during execution.

---

### **Example: Checked Exception**

```java
import java.io.*;

public class CheckedExample {
    public static void main(String[] args) {
        try {
            FileReader fr = new FileReader("data.txt");  // File may not exist
            int c = fr.read();
            System.out.println((char)c);
            fr.close();
        } 
        catch (IOException e) {
            System.out.println("File operation failed: " + e.getMessage());
        }
    }
}
```

**Explanation:**
Here, both `FileNotFoundException` and `IOException` are *checked exceptions*. The compiler forces the programmer to handle them using a `try-catch` block or by declaring `throws IOException` in the method header.

If not handled, compilation fails.

---

## **2. Unchecked Exceptions (Runtime Exceptions)**

Unchecked exceptions, also known as **runtime exceptions**, are **not checked at compile time**. The compiler does not require you to handle or declare them explicitly.

They occur **during program execution**, usually due to **programming mistakes or logical errors** such as dividing by zero, accessing invalid indices, or dereferencing null references.

Unchecked exceptions are subclasses of **`RuntimeException`** and its subclasses.

---

### **Common Examples**

* `ArithmeticException` – Division by zero.
* `NullPointerException` – Accessing an object that has not been initialized.
* `ArrayIndexOutOfBoundsException` – Accessing invalid array indices.
* `NumberFormatException` – Invalid numeric string conversion.
* `IllegalArgumentException` – When an illegal or inappropriate argument is passed to a method.

---

### **Example: Unchecked Exception**

```java
public class UncheckedExample {
    public static void main(String[] args) {
        try {
            int[] arr = {10, 20, 30};
            System.out.println(arr[5]);  // Invalid index
        } 
        catch (ArrayIndexOutOfBoundsException e) {
            System.out.println("Error: Invalid array index.");
        }
    }
}
```

**Explanation:**
The compiler does not check this exception. It will only occur when the program runs and attempts to access an out-of-bounds index.

---

### **Why “Unchecked”?**

Unchecked exceptions are typically caused by **developer mistakes** (for example, not validating input or using null references).
Because these are avoidable through careful coding, the compiler assumes it’s the programmer’s responsibility to prevent them — not the language’s responsibility to enforce handling.

---

## **3. Errors**

Errors are serious, **non-recoverable conditions** that occur at runtime.
They represent problems **beyond the control of the application**, often related to system resources, memory, or hardware failures.

Unlike exceptions, errors should **never be caught** or handled by the application — they are meant to signal **critical failures** that require program termination.

---

### **Common Examples**

* `OutOfMemoryError` – When the JVM cannot allocate more memory.
* `StackOverflowError` – When a recursive method calls itself indefinitely.
* `VirtualMachineError` – When the JVM itself is corrupted or cannot continue execution.
* `AssertionError` – Thrown when an assertion statement fails.

---

### **Example: Error**

```java
public class ErrorExample {
    public static void recursiveMethod() {
        recursiveMethod();  // Infinite recursion
    }
    public static void main(String[] args) {
        recursiveMethod();
    }
}
```

**Explanation:**
This program will throw a `StackOverflowError`, which is an **Error**, not an **Exception**.
Even if wrapped inside a `try-catch`, it’s generally not advisable to handle such cases since they indicate severe system-level problems.

---

## **Comparison Table: Checked vs Unchecked vs Errors**

| Feature                   | Checked Exceptions                         | Unchecked Exceptions                          | Errors                                   |
| ------------------------- | ------------------------------------------ | --------------------------------------------- | ---------------------------------------- |
| **Compile-time Checking** | Yes                                        | No                                            | No                                       |
| **Subclass of**           | `Exception` (except `RuntimeException`)    | `RuntimeException`                            | `Error`                                  |
| **Recoverable?**          | Usually recoverable                        | Often avoidable but not always recoverable    | Non-recoverable                          |
| **Caused by**             | External factors (I/O, DB, network)        | Programmer mistakes (logic errors)            | System failures (memory, hardware)       |
| **Handling Requirement**  | Must be handled or declared using `throws` | Handling optional                             | Should not be handled                    |
| **Examples**              | `IOException`, `SQLException`              | `NullPointerException`, `ArithmeticException` | `OutOfMemoryError`, `StackOverflowError` |

## **Visual Hierarchy Representation (Text Diagram)**

```
Throwable
│
├── Error
│   ├── OutOfMemoryError
│   └── StackOverflowError
│
└── Exception
    ├── IOException (Checked)
    │     └── FileNotFoundException
    └── RuntimeException (Unchecked)
          ├── ArithmeticException
          ├── NullPointerException
          └── ArrayIndexOutOfBoundsException
```


---
---
# **Java Try and Catch Block**

Exception handling in Java revolves around five main keywords — `try`, `catch`, `finally`, `throw`, and `throws`. Among these, the **`try`** and **`catch`** blocks form the _core mechanism_ of handling exceptions.

They work together to detect, isolate, and handle abnormal conditions at runtime — preventing the abrupt termination of the program and maintaining normal execution flow.

## **The `try` Block**

The **`try` block** is used to _wrap the code that might throw an exception_.  
It acts as a **monitoring section** — meaning any statement inside the `try` block is under observation for potential exceptions.

If an exception occurs within the `try` block, **normal flow of execution stops immediately**, and control is transferred to the corresponding `catch` block that matches the type of exception thrown.

### **Syntax**

```java
try {
    // Statements that might throw an exception
}
catch (ExceptionType e) {
    // Handling code
}
```

### **Rules for Using `try` Block**

1. The `try` block **must** be followed by at least one `catch` block **or** a `finally` block.
    
    - You cannot have a standalone `try` block.
        
2. Multiple statements can be placed inside the `try` block.
    
3. The `try` block can be nested (i.e., one `try` block inside another).
    
4. A single `try` block can be associated with **multiple `catch` blocks**.
    

---

## **The `catch` Block**

The **`catch` block** is used to **handle exceptions** that occur inside the `try` block.  
Each `catch` block is designed to handle a **specific type** of exception. When an exception is thrown, the JVM searches sequentially through the `catch` blocks to find a **matching type**.

If a match is found, the corresponding `catch` block executes; otherwise, the search continues. If no match is found, the program terminates abnormally.

### **Syntax**

```java
try {
    // Code that might generate an exception
}
catch (ExceptionType e) {
    // Code to handle the exception
}
```

**Example:**

```java
try {
    int a = 10, b = 0;
    int result = a / b;
}
catch (ArithmeticException e) {
    System.out.println("Error: Division by zero is not allowed.");
}
```

**Output:**

```
Error: Division by zero is not allowed.
```

Here, dividing by zero triggers an `ArithmeticException`. The JVM detects it, skips the remaining code inside the `try` block, and executes the `catch` block.

---

## **Flow of Control in Try-Catch**

When an exception occurs inside a `try` block:

1. The remaining statements inside the `try` block are **skipped**.
   
2. Control jumps to the **first `catch` block** whose parameter matches the type of exception.
   
3. Once the exception is handled, the program continues normally after the `catch` block.
   

If **no exception** occurs, the `catch` block is **skipped entirely**, and control moves directly after the try-catch construct.

---

### **Illustrative Flow Diagram (Textual)**

```
   ┌───────────────────────────────────────┐
   │              Try Block                │
   └───────────────────────────────────────┘
                    │
                    ▼
           Exception Occurs?
             /             \
           Yes               No
           │                 │
           ▼                 ▼
   Matching Catch Found?     Continue Normal Flow
        /      \
      Yes       No
      │          │
      ▼          ▼
   Execute     JVM Terminates
   Catch
```

---

## **Multiple Catch Blocks**

A single `try` block can be followed by multiple `catch` blocks, each designed to handle different types of exceptions.

This is useful when different exception types may arise from the same block of code and require **different handling logic**.

**Example:**

```java
try {
    int[] arr = {10, 20, 30};
    System.out.println(arr[5]);  // May throw ArrayIndexOutOfBoundsException
    int result = 10 / 0;         // May throw ArithmeticException
}
catch (ArithmeticException e) {
    System.out.println("Error: Division by zero.");
}
catch (ArrayIndexOutOfBoundsException e) {
    System.out.println("Error: Invalid array index.");
}
catch (Exception e) {
    System.out.println("General exception: " + e);
}
```

**Output:**

```
Error: Invalid array index.
```

**Explanation:**  
The first exception encountered is an `ArrayIndexOutOfBoundsException`. The corresponding `catch` block handles it, and the rest of the code in the `try` block is skipped.  
Notice that the `Exception` class catch block is written **last**, because it can handle _any_ exception (it’s the superclass of all exceptions).

If placed earlier, it would make the later, more specific handlers **unreachable**, resulting in a compilation error.

---

### **Rule for Catch Block Ordering**

Always place **specific exception types first**, followed by **general exception types** like `Exception`.

Example of _incorrect order_:

```java
try {
    // risky code
}
catch (Exception e) { }               // general exception
catch (ArithmeticException e) { }     // specific exception (compile-time error)
```

This causes a **compilation error** because `ArithmeticException` is a subclass of `Exception`, and the compiler flags the second `catch` as _unreachable code_.

---


## **Nested Try-Catch Blocks**

A `try` block can be nested inside another `try` block.  
This structure is useful when a portion of code inside the `try` block may throw different exceptions that need separate handling mechanisms.

**Example:**

```java
try {
    try {
        int[] arr = new int[5];
        arr[5] = 100;  // Inner exception
    }
    catch (ArrayIndexOutOfBoundsException e) {
        System.out.println("Inner catch: Invalid array index.");
    }

    int result = 50 / 0;  // Outer exception
}
catch (ArithmeticException e) {
    System.out.println("Outer catch: Division by zero.");
}
```

**Output:**

```
Inner catch: Invalid array index.
Outer catch: Division by zero.
```

**Explanation:**  
The inner `try` handles its own exception first, and then control passes back to the outer `try` block, which handles its exception independently.

---

## **Advantages of Try-Catch Blocks**

1. **Prevents abrupt termination** of the program.
   
2. **Localizes error handling** – errors are managed close to where they occur.
   
3. **Supports multiple exception handling** – one `try` can handle many error conditions.
   
4. **Improves readability** and maintainability of code.
   
5. **Encourages safe programming practices** through explicit exception management.
   

---

## **Common Mistakes to Avoid**

- Declaring a `try` block without any accompanying `catch` or `finally`.
   
- Placing general exception handlers before specific ones.
   
- Ignoring exceptions silently (empty catch blocks).
   
- Overusing try-catch for logic that can be handled through validation (e.g., checking if a divisor is zero before division).
   
---
---
# **Multiple Catch Blocks in Java**

In Java, a single block of code may generate **different types of exceptions**.
For example, a piece of code might perform **arithmetic operations**, **array manipulations**, or **file input/output**, all of which can cause distinct exceptions.

To handle each of these exceptions appropriately, Java allows **multiple `catch` blocks** to be associated with a single `try` block.
This structure provides flexibility by letting the programmer respond differently based on the *type* of error that occurs.

When an exception occurs inside a `try` block:

1. The Java Virtual Machine (JVM) looks for the **first matching `catch` block** that can handle the exception type.
2. Once a suitable handler is found, **only that catch block executes**, and all remaining `catch` blocks are skipped.
3. If no `catch` block matches the exception, the program terminates abnormally, and the JVM prints a stack trace.

Thus, multiple `catch` blocks make it possible to write **fine-grained error-handling logic** — where each exception type can be treated individually.

## **Syntax of Multiple Catch Blocks**

```java
try {
    // Code that may throw multiple exceptions
}
catch (ExceptionType1 e1) {
    // Handler for ExceptionType1
}
catch (ExceptionType2 e2) {
    // Handler for ExceptionType2
}
catch (ExceptionType3 e3) {
    // Handler for ExceptionType3
}
```

Each `catch` block is checked **in the order in which it appears**.
The **first block that matches** the thrown exception type will execute; subsequent ones are ignored.

---

## **Example: Multiple Catch Blocks**

```java
public class MultipleCatchExample {
    public static void main(String[] args) {
        try {
            int[] numbers = {10, 20, 30};
            int result = numbers[5] / 0; // May throw multiple exceptions
        } 
        catch (ArithmeticException e) {
            System.out.println("Error: Division by zero is not allowed.");
        } 
        catch (ArrayIndexOutOfBoundsException e) {
            System.out.println("Error: Array index out of bounds.");
        } 
        catch (Exception e) {
            System.out.println("General exception: " + e.getMessage());
        }

        System.out.println("Program execution continues normally.");
    }
}
```

**Output:**

```
Error: Array index out of bounds.
Program execution continues normally.
```

**Explanation:**

* The program first attempts to execute the statements inside the `try` block.
* The statement `numbers[5]` throws an `ArrayIndexOutOfBoundsException`.
* JVM searches for the matching `catch` block and finds one for `ArrayIndexOutOfBoundsException`.
* The corresponding block executes, and the rest of the code continues smoothly.

## **Order of Catch Blocks**

The order of `catch` blocks **matters** because Java checks them *from top to bottom*.

When using multiple catch blocks:

* Always place **specific exception types first**, and the **general ones later**.
* If a superclass exception (like `Exception`) is placed before its subclass (like `ArithmeticException`), the compiler throws an **“Unreachable Code” error**, because the specific handler would never be executed.

---

### **Example of Incorrect Order (Compile-time Error)**

```java
try {
    int x = 10 / 0;
}
catch (Exception e) {
    System.out.println("General exception.");
}
catch (ArithmeticException e) {  // Error: Unreachable code
    System.out.println("Arithmetic exception.");
}
```

**Explanation:**
The `Exception` class is the **superclass** of `ArithmeticException`.
Once `catch(Exception e)` executes, no further catch block can ever be reached — hence, the compiler reports an error.

---

### **Correct Order**

```java
try {
    int x = 10 / 0;
}
catch (ArithmeticException e) {
    System.out.println("Arithmetic error.");
}
catch (Exception e) {
    System.out.println("General exception.");
}
```

**Output:**

```
Arithmetic error.
```

Now the specific exception is caught first, and the general one acts as a fallback for any unhandled exception types.

### **Example: Multi-Catch in Action**

```java
public class MultiCatchExample {
    public static void main(String[] args) {
        try {
            int[] arr = new int[3];
            arr[3] = 50 / 0;  // Can throw ArithmeticException or ArrayIndexOutOfBoundsException
        }
        catch (ArithmeticException | ArrayIndexOutOfBoundsException e) {
            System.out.println("Error: Either division by zero or invalid array index.");
        }
    }
}
```

**Output:**

```
Error: Either division by zero or invalid array index.
```

**Explanation:**
The same handler is used for both possible exceptions.
This feature enhances **code brevity** without sacrificing functionality.

## **Rules for Multiple Catch Blocks**

1. You can associate **one `try` block** with **multiple `catch` blocks**.
2. **Each catch block** must handle a **unique** or **non-overlapping** exception type.
3. Catch blocks are evaluated **in order** — from top to bottom.
4. **Specific exceptions** should always be handled **before general ones**.
5. In a multi-catch block (Java 7+), exception types separated by `|` **cannot be subclasses/superclasses** of each other.
6. Only **one catch block executes** per exception — once matched, others are skipped.

--
## **Advantages of Multiple Catch Blocks**

1. **Fine-grained control:** Each exception type can be handled differently.
2. **Enhanced readability:** Separates distinct error scenarios clearly.
3. **Improved debugging:** Pinpoints the exact source of failure.
4. **Safe fallback:** The final generic catch ensures unhandled exceptions don’t crash the program.
5. **Code optimization:** Multi-catch reduces redundant code when handling exceptions with the same logic.

---
----

# Java Custom Exceptions

In Java, the exception-handling mechanism revolves around predefined classes that represent different categories of errors — for example, `ArithmeticException`, `NullPointerException`, or `IOException`.
However, in many real-world applications, these built-in exceptions are **not enough** to describe *domain-specific* or *application-specific* problems.

That’s where **custom exceptions** come in.
A **custom exception** (also called **user-defined exception**) is a class that we create ourselves to represent a situation that Java’s standard exceptions do not cover.
These help make error reporting **more meaningful** and **context-aware**.

# overview 

A **custom exception** is essentially a class that:

* **extends** either the `Exception` class (for *checked* exceptions)
  or the `RuntimeException` class (for *unchecked* exceptions).
* carries an **error message** that can be retrieved using the `getMessage()` method.
* behaves just like any other Java exception — it can be **thrown** using the `throw` keyword and **caught** using `try–catch` blocks.

By defining your own exception types, you make your code **self-explanatory**, easier to debug, and easier for others to maintain.

## **Why Custom Exceptions Are Needed**

Imagine a banking system where users can withdraw money.
If the balance is insufficient, you might want to throw an exception that specifically says **“Insufficient Balance”** rather than a generic `ArithmeticException` or `IllegalArgumentException`.

Custom exceptions:

1. Help identify **application-specific errors** more clearly.
2. Improve **readability** and **debugging** by making exception messages meaningful.
3. Allow developers to **categorize errors** based on the application’s logic.
4. Promote **consistent error handling** across different parts of the code.

---

## **Creating a Custom Exception**

Creating a custom exception is simple — you just define a new class that extends `Exception` or `RuntimeException`.

---

### **Syntax**

```java
class CustomExceptionName extends Exception {
    // Constructor
    public CustomExceptionName(String message) {
        super(message);  // call superclass constructor
    }
}
```

You can also overload the constructor or add fields/methods if your exception needs to store extra information.

---

### **Example: Checked Custom Exception**

```java
// Step 1: Define custom exception
class InsufficientFundsException extends Exception {
    public InsufficientFundsException(String message) {
        super(message);
    }
}

// Step 2: Use custom exception
public class BankAccount {
    private double balance = 5000;

    public void withdraw(double amount) throws InsufficientFundsException {
        if (amount > balance) {
            throw new InsufficientFundsException("Withdrawal denied: Insufficient balance.");
        } else {
            balance -= amount;
            System.out.println("Withdrawal successful. Remaining balance: " + balance);
        }
    }

    public static void main(String[] args) {
        BankAccount acc = new BankAccount();
        try {
            acc.withdraw(7000);
        } catch (InsufficientFundsException e) {
            System.out.println("Exception caught: " + e.getMessage());
        }
    }
}
```

**Output:**

```
Exception caught: Withdrawal denied: Insufficient balance.
```

**Explanation:**
The `withdraw()` method declares that it might throw an `InsufficientFundsException`.
When the withdrawal exceeds the available balance, the custom exception is thrown with a meaningful message.
The caller (main method) catches it and handles it gracefully.

---

## **Checked vs Unchecked Custom Exceptions**

Custom exceptions can be either **checked** or **unchecked**, depending on which superclass they extend.

| **Type**                   | **Superclass**             | **Compile-Time Behavior**                                 | **Usage Example**                                                                     |
| -------------------------- | -------------------------- | --------------------------------------------------------- | ------------------------------------------------------------------------------------- |
| Checked Custom Exception   | `extends Exception`        | Must be declared using `throws` or handled in `try–catch` | Application errors that must be explicitly handled (e.g. invalid input, missing file) |
| Unchecked Custom Exception | `extends RuntimeException` | Not required to declare or catch                          | Programming logic errors (e.g. invalid index, misuse of API)                          |

---

### **Example: Unchecked Custom Exception**

```java
class InvalidAgeException extends RuntimeException {
    public InvalidAgeException(String message) {
        super(message);
    }
}

public class VotingSystem {
    public void checkEligibility(int age) {
        if (age < 18) {
            throw new InvalidAgeException("Access denied: You must be 18 or older to vote.");
        } else {
            System.out.println("Access granted. You can vote!");
        }
    }

    public static void main(String[] args) {
        VotingSystem voter = new VotingSystem();
        voter.checkEligibility(16);
    }
}
```

**Output:**

```
Exception in thread "main" InvalidAgeException: Access denied: You must be 18 or older to vote.
```

**Explanation:**
Since `InvalidAgeException` extends `RuntimeException`, the compiler doesn’t force us to handle or declare it — but the program will still terminate if it’s thrown and not caught.

---

## **Throwing and Catching Custom Exceptions**

The `throw` keyword is used to explicitly raise an exception, while `try–catch` handles it.

**Example:**

```java
try {
    throw new CustomException("Custom error occurred!");
}
catch (CustomException e) {
    System.out.println(e.getMessage());
}
```

## **Best Practices for Custom Exceptions**

1. **Extend the correct superclass** —

   * Use `Exception` for checked exceptions.
   * Use `RuntimeException` for unchecked exceptions.

2. **Provide clear and descriptive messages** that explain *why* the exception occurred.

3. **Use custom exceptions sparingly.**
   Overusing them can clutter your project. Create them only when built-in ones aren’t sufficient.

4. **Document your custom exceptions** in method declarations or API documentation so that other developers know when and why they’re thrown.

5. **Follow naming conventions.**
   Custom exception names usually end with the word *“Exception”* (e.g., `InvalidAgeException`, `InsufficientFundsException`).

6. **Avoid empty exception classes.**
   If you create one, ensure it at least provides a constructor with a message parameter.

## **Advantages of Using Custom Exceptions**

* Promotes **clear communication** of specific problems.
* Makes **debugging and maintenance easier.**
* Helps **enforce business rules** and domain-specific constraints.
* Improves **program readability** and structure.
* Provides **better control** over error management in large systems.

--- 
---
# Java I/O — File Handling

In Java, **I/O (Input/Output)** refers to the process of **reading data from** and **writing data to** various sources and destinations — such as files, keyboard, console, or network sockets.

The **java.io** package provides the fundamental classes and interfaces for performing these operations. Among them, **File Handling** is one of the most essential parts — it allows programs to interact with the file system, storing and retrieving data permanently.

When working with files, Java treats them as **streams** — continuous flows of data.

* An **input stream** is used to *read* data.
* An **output stream** is used to *write* data.

The central class used for representing files and directories in Java is the **`File` class**.

## **The `File` Class**

The `File` class (in the `java.io` package) is not used for reading or writing file data directly.
Instead, it serves as an **abstraction of file and directory paths** — providing methods to **inspect**, **create**, **delete**, and **check properties** of files and directories.

### **Class Declaration**

```java
public class File extends Object implements Serializable, Comparable<File>
```

This means the `File` class:

* Implements the **Serializable** interface (objects can be saved and restored),
* Implements the **Comparable** interface (can be compared based on path names).

### **Commonly Used Constructors**

| **Constructor**                     | **Description**                                                          |
| ----------------------------------- | ------------------------------------------------------------------------ |
| `File(String pathname)`             | Creates a File object representing the given file or directory name.     |
| `File(String parent, String child)` | Creates a File object using a parent directory and child file name.      |
| `File(File parent, String child)`   | Creates a File object from an existing File parent and a child pathname. |

### **Example**

```java
import java.io.File;

public class FileDemo {
    public static void main(String[] args) {
        File f = new File("example.txt");

        System.out.println("File Name: " + f.getName());
        System.out.println("Path: " + f.getPath());
        System.out.println("Absolute Path: " + f.getAbsolutePath());
        System.out.println("Parent: " + f.getParent());
        System.out.println("Exists: " + f.exists());
        System.out.println("Readable: " + f.canRead());
        System.out.println("Writable: " + f.canWrite());
        System.out.println("Is Directory: " + f.isDirectory());
        System.out.println("Is File: " + f.isFile());
    }
}
```

**Explanation:**

* The above code creates a `File` object linked to `"example.txt"`.
* Even if the file doesn’t exist, the `File` object still gets created — but the `exists()` method will return `false`.

### **Important Methods of `File` Class**

| **Method**                                             | **Description**                                    |
| ------------------------------------------------------ | -------------------------------------------------- |
| `boolean exists()`                                     | Checks if the file or directory physically exists. |
| `boolean canRead()` / `canWrite()` / `canExecute()`    | Checks file permissions.                           |
| `boolean isFile()` / `isDirectory()`                   | Checks whether it’s a file or a directory.         |
| `long length()`                                        | Returns the file size in bytes.                    |
| `String getName()` / `getPath()` / `getAbsolutePath()` | Returns the file’s name or path.                   |
| `boolean delete()`                                     | Deletes the file or directory.                     |
| `boolean mkdir()` / `mkdirs()`                         | Creates single or nested directories.              |
| `String[] list()`                                      | Returns an array of filenames inside a directory.  |
| `boolean renameTo(File dest)`                          | Renames the file or moves it.                      |

### **Example: Creating and Deleting Files**

```java
import java.io.*;

public class FileCreateDelete {
    public static void main(String[] args) throws IOException {
        File file = new File("testfile.txt");

        if (file.createNewFile()) {
            System.out.println("File created: " + file.getName());
        } else {
            System.out.println("File already exists.");
        }

        if (file.exists()) {
            System.out.println("Deleting file...");
            file.delete();
        }
    }
}
```

**Output:**

```
File created: testfile.txt
Deleting file...
```

**Explanation:**

* `createNewFile()` actually creates a file on disk.
* If the file already exists, it won’t overwrite it.
* The `delete()` method permanently removes it.

---

## **Reading and Writing Files**

To perform **actual I/O operations** — reading or writing contents — Java provides multiple stream classes in the `java.io` package.

There are two main categories:

| **Stream Type**   | **For**                                    | **Base Classes**              |
| ----------------- | ------------------------------------------ | ----------------------------- |
| Byte Streams      | Binary data (images, videos, etc.)         | `InputStream`, `OutputStream` |
| Character Streams | Text data (files with readable characters) | `Reader`, `Writer`            |

---

## **1. Byte Stream Classes**

These are used for low-level I/O, where data is handled **byte by byte**.

### **Common Byte Stream Classes**

| **Class**          | **Description**                  |
| ------------------ | -------------------------------- |
| `FileInputStream`  | Reads data from a file as bytes. |
| `FileOutputStream` | Writes byte data to a file.      |

---

### **Example: Writing to a File**

```java
import java.io.*;

public class WriteBytes {
    public static void main(String[] args) {
        try {
            FileOutputStream fout = new FileOutputStream("output.txt");
            String data = "Java I/O is powerful.";
            fout.write(data.getBytes());
            fout.close();
            System.out.println("Data written successfully.");
        } catch (IOException e) {
            System.out.println("Error occurred: " + e);
        }
    }
}
```

### **Example: Reading from a File**

```java
import java.io.*;

public class ReadBytes {
    public static void main(String[] args) {
        try {
            FileInputStream fin = new FileInputStream("output.txt");
            int i;
            while ((i = fin.read()) != -1) {
                System.out.print((char) i);
            }
            fin.close();
        } catch (IOException e) {
            System.out.println("Error: " + e);
        }
    }
}
```

**Explanation:**

* `FileOutputStream` writes bytes from memory to the file.
* `FileInputStream` reads bytes from the file one by one.
* `read()` returns `-1` when the end of file (EOF) is reached.

---

## **2. Character Stream Classes**

Character streams handle **text-based files**, working with characters instead of bytes.
These classes automatically handle character encoding and are more suitable for text files.

### **Common Character Stream Classes**

| **Class**    | **Description**               |
| ------------ | ----------------------------- |
| `FileReader` | Reads characters from a file. |
| `FileWriter` | Writes characters to a file.  |

---

### **Example: Writing Characters to a File**

```java
import java.io.*;

public class WriteChars {
    public static void main(String[] args) {
        try {
            FileWriter writer = new FileWriter("notes.txt");
            writer.write("Java character streams handle text files easily.");
            writer.close();
            System.out.println("Data written successfully.");
        } catch (IOException e) {
            System.out.println("Error: " + e);
        }
    }
}
```

### **Example: Reading Characters from a File**

```java
import java.io.*;

public class ReadChars {
    public static void main(String[] args) {
        try {
            FileReader reader = new FileReader("notes.txt");
            int ch;
            while ((ch = reader.read()) != -1) {
                System.out.print((char) ch);
            }
            reader.close();
        } catch (IOException e) {
            System.out.println("Error: " + e);
        }
    }
}
```

---

## **Buffered Streams**

To improve performance, Java provides **buffered stream classes** that temporarily store data in memory before writing/reading.
This reduces the number of direct interactions with the physical disk.

| **Buffered Class**                             | **Used With** | **Purpose**                                  |
| ---------------------------------------------- | ------------- | -------------------------------------------- |
| `BufferedReader`                               | `Reader`      | Efficient reading of characters, lines, etc. |
| `BufferedWriter`                               | `Writer`      | Efficient writing of character data.         |
| `BufferedInputStream` / `BufferedOutputStream` | Byte streams  | Speeds up byte-level I/O.                    |

---

### **Example: Using `BufferedReader`**

```java
import java.io.*;

public class BufferedRead {
    public static void main(String[] args) {
        try {
            BufferedReader br = new BufferedReader(new FileReader("notes.txt"));
            String line;
            while ((line = br.readLine()) != null) {
                System.out.println(line);
            }
            br.close();
        } catch (IOException e) {
            System.out.println("Error: " + e);
        }
    }
}
```

---

## **File Handling with Exceptions**

All file operations can throw exceptions like:

* `IOException` — for general input/output issues,
* `FileNotFoundException` — when the file doesn’t exist,
* `SecurityException` — if access to the file is restricted.

Hence, **every file operation** should be enclosed in `try–catch` blocks or declared with `throws IOException`.

---

## **Deleting, Renaming, and Listing Files**

### **Example: Working with Directories**

```java
import java.io.*;

public class DirectoryDemo {
    public static void main(String[] args) {
        File dir = new File("MyFolder");
        if (!dir.exists()) {
            dir.mkdir();
        }

        File file = new File(dir, "data.txt");
        try {
            file.createNewFile();
        } catch (IOException e) {
            System.out.println(e);
        }

        String[] files = dir.list();
        System.out.println("Files in directory:");
        for (String name : files) {
            System.out.println(name);
        }
    }
}
```

---

## **Summary**

| **Aspect**      | **Byte Stream**                       | **Character Stream**       |
| --------------- | ------------------------------------- | -------------------------- |
| Base classes    | `InputStream`, `OutputStream`         | `Reader`, `Writer`         |
| Data handled    | Binary (bytes)                        | Text (characters)          |
| Example classes | `FileInputStream`, `FileOutputStream` | `FileReader`, `FileWriter` |
| Use case        | Images, audio, video, raw data        | Text files, documents      |

---
---

# Object Serialization in Java

In Java, **serialization** is the process of **converting an object into a byte stream** so that it can be **stored in a file**, **sent over a network**, or **transferred between JVMs**.

Later, this byte stream can be **reconstructed back into the original object** — a process known as **deserialization**.

Serialization allows Java objects to be:

* Persisted permanently (saved on disk),
* Transmitted easily (across networks or between programs),
* Stored temporarily (for caching or session management).

It is one of the most important features in Java’s **I/O system**, provided by the **`java.io`** package.

## **Concept Overview**

Normally, Java objects exist only in **memory (RAM)** while a program runs.
Once the program ends, all objects are lost unless explicitly stored.

Serialization bridges that gap: it **preserves the state of an object** so it can be recreated later — even after the program exits or runs on a different machine.

You can think of serialization as “freezing” an object into a storable form, and deserialization as “thawing” it back into memory.

--- 

> **Serialization** is the process of writing the state of an object to a byte stream.

> **Deserialization** is the process of reading that byte stream back and recreating the object.

The resulting byte stream contains:

* Object’s data (the values of its fields),
* Type information (class name, version, etc.),
* Metadata to reconstruct it accurately.

## **Classes and Interfaces Involved**

All serialization functionality is available in the **`java.io`** package.

| **Component**              | **Description**                                    |
| -------------------------- | -------------------------------------------------- |
| `Serializable` (interface) | Marks a class as serializable.                     |
| `ObjectOutputStream`       | Writes (serializes) objects to an output stream.   |
| `ObjectInputStream`        | Reads (deserializes) objects from an input stream. |
## **The `Serializable` Interface**

Serialization in Java is **not automatic**.
To make a class serializable, it must **implement the marker interface** `java.io.Serializable`.

A *marker interface* has **no methods**; it only signals to the JVM that objects of this class are allowed to be serialized.

### **Syntax:**

```java
import java.io.Serializable;

public class MyClass implements Serializable {
    // class code
}
```

If a class does not implement `Serializable` but you try to serialize it,
Java will throw a `NotSerializableException`.

## **Serialization Process**

Serialization is done using the **`ObjectOutputStream`** class.
You can wrap it around any output stream (like `FileOutputStream`) to write object data into a file.

### **Steps to Serialize an Object**

1. **Import** `java.io.*`
2. **Create** a class implementing `Serializable`
3. **Create** an `ObjectOutputStream`
4. **Use** the `writeObject()` method to serialize

### **Example: Serialization**

```java
import java.io.*;

class Student implements Serializable {
    int id;
    String name;

    Student(int id, String name) {
        this.id = id;
        this.name = name;
    }
}

public class SerializeExample {
    public static void main(String[] args) {
        try {
            Student s1 = new Student(101, "Riya");

            // FileOutputStream: connects to file
            FileOutputStream fileOut = new FileOutputStream("student.ser");

            // ObjectOutputStream: writes object to stream
            ObjectOutputStream out = new ObjectOutputStream(fileOut);

            out.writeObject(s1); // serialize object
            out.close();
            fileOut.close();

            System.out.println("Object has been serialized successfully.");
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
}
```

**Output:**

```
Object has been serialized successfully.
```

**Explanation:**

* The object `s1` is converted into a byte stream and stored in the file `student.ser`.
* File extension `.ser` stands for *serialized object* (though it’s optional).

## **Deserialization Process**

Deserialization is the **reverse** of serialization.
It reconstructs the object from the stored byte stream using `ObjectInputStream`.

### **Steps to Deserialize an Object**

1. **Create** an `ObjectInputStream` wrapped around a `FileInputStream`
2. **Use** the `readObject()` method
3. **Typecast** the returned object to the appropriate class

### **Example: Deserialization**

```java
import java.io.*;

public class DeserializeExample {
    public static void main(String[] args) {
        try {
            FileInputStream fileIn = new FileInputStream("student.ser");
            ObjectInputStream in = new ObjectInputStream(fileIn);

            Student s = (Student) in.readObject();

            in.close();
            fileIn.close();

            System.out.println("Deserialized Student Data:");
            System.out.println("ID: " + s.id);
            System.out.println("Name: " + s.name);

        } catch (IOException | ClassNotFoundException e) {
            e.printStackTrace();
        }
    }
}
```

**Output:**

```
Deserialized Student Data:
ID: 101
Name: Riya
```

**Explanation:**
The `readObject()` method reconstructs the original `Student` object exactly as it was before serialization.

## **Transient Keyword**

Sometimes you don’t want certain fields of a class to be serialized — for example, passwords, sensitive data, or temporary variables.

To prevent a field from being included in the serialized form, declare it using the **`transient`** keyword.

### **Example:**

```java
class User implements Serializable {
    String username;
    transient String password; // won't be serialized

    User(String username, String password) {
        this.username = username;
        this.password = password;
    }
}
```

If this object is serialized and deserialized:

* `username` will retain its value.
* `password` will be reset to `null` (default value).

**Output after deserialization:**

```
Username: Riya
Password: null
```

**Explanation:**
The transient modifier ensures certain fields are ignored during serialization — useful for protecting sensitive or non-essential data.

---

## **SerialVersionUID**

Every serializable class in Java has an internal **version number** called `serialVersionUID`.
It’s used during deserialization to verify that the class definition of the object being deserialized **matches** the class used during serialization.

If the `serialVersionUID` of the class and the serialized object don’t match,
Java throws an `InvalidClassException`.

By default, JVM generates this ID automatically, but it’s a good practice to declare it explicitly.

### **Example:**

```java
class Student implements Serializable {
    private static final long serialVersionUID = 1L;
    int id;
    String name;
}
```

**Purpose:**

* Ensures compatibility between serialized objects and their class versions.
* Prevents deserialization errors when class definitions change later.

## **Object Graph Serialization**

If an object being serialized contains references to other objects,
those objects are also **recursively serialized** — as long as they also implement `Serializable`.

This is called **object graph serialization**.

**Example:**
If a `Department` object contains a `Manager` object, and both classes implement `Serializable`,
serializing the `Department` will automatically serialize its `Manager`.

## **Serialization with Inheritance**

* If a superclass implements `Serializable`, then all its subclasses are automatically serializable.
* If a superclass **does not** implement `Serializable`, its fields are not serialized,
  but subclass fields still can be (after calling the superclass constructor during deserialization).

## **Serialization and Static Fields**

Static fields **belong to the class**, not the object, so they are **not serialized**.
Serialization only stores *instance data*, not class-level data.

## **Common Exceptions in Serialization**

| **Exception**              | **Cause**                                                   |
| -------------------------- | ----------------------------------------------------------- |
| `NotSerializableException` | Thrown when trying to serialize a non-serializable object.  |
| `InvalidClassException`    | Thrown when serialVersionUID mismatch occurs.               |
| `ClassNotFoundException`   | Thrown when deserializing an object whose class is missing. |
| `IOException`              | Thrown for general I/O errors during file operations.       |
## **Advantages of Serialization**

1. **Persistence:** Objects can be saved permanently for later retrieval.
2. **Data Transmission:** Enables object transfer across JVMs or over a network.
3. **Deep Copying:** Can be used to create exact duplicates of objects.
4. **Simplifies Storage:** Easier than manually saving individual field values.
5. **Framework Support:** Used internally in RMI, EJB, Hibernate, and more.

## **Limitations of Serialization**

1. Serialized files are **platform-dependent** if not carefully handled.
2. Changes in class structure can cause **version mismatch errors**.
3. Large object graphs can lead to **high memory consumption**.
4. **Sensitive data risk** if transient keyword not used properly.
5. **Performance overhead** due to stream I/O operations.

--- 

# Networking Basics — Java and the Net

In the modern world of distributed computing, applications often need to **communicate and exchange data over networks** — whether across computers in a LAN, or globally through the internet.

**Networking in Java** provides a rich API to enable this communication using classes from the **`java.net`** package.
It allows Java programs to send and receive data just like web browsers, mail clients, or servers — making Java an inherently **network-oriented language**.

### **What Is Networking?**

**Networking** refers to connecting two or more computers so that they can **share data, resources, and services**.
When programs running on these computers communicate using network protocols, that’s called **network programming**.

Java simplifies this process by providing **built-in classes** that handle low-level networking details, like IP addressing, port communication, and data transfer.

### **Core Idea**

Every communication over the internet is based on **two main concepts**:

1. **IP Address** – a unique number that identifies a device on a network.
2. **Port Number** – identifies a specific process or application running on that device.

Together, they form a **socket address** (e.g., `192.168.0.10:8080`), which uniquely identifies a communication endpoint.

---

### **Networking Terminology**

Before diving into Java classes, a few terms are essential:

| **Term**       | **Meaning**                                                                                 |
| -------------- | ------------------------------------------------------------------------------------------- |
| **IP Address** | Internet Protocol address; unique identifier for a device on a network (e.g., 192.168.1.2). |
| **Port**       | Logical endpoint for communication within a system.                                         |
| **Protocol**   | Set of rules governing communication (e.g., TCP, UDP, HTTP).                                |
| **Socket**     | A combination of IP and Port; used as a communication endpoint.                             |
| **Client**     | The program or device that initiates a request.                                             |
| **Server**     | The program or device that provides a response or service.                                  |

---

### **Networking Support in Java**

Java provides networking support through the **`java.net` package**, which includes classes for:

* Working with **URLs** (Uniform Resource Locators),
* Managing **IP addresses**,
* Establishing **TCP/UDP connections**,
* Building **client-server applications**,
* Reading and writing data streams over a network.

These classes encapsulate all the **low-level socket programming** details, so developers can work at a high level of abstraction.

---

### **Major Networking Classes in `java.net`**

| **Class / Interface**              | **Purpose**                                                     |
| ---------------------------------- | --------------------------------------------------------------- |
| `InetAddress`                      | Represents an Internet Protocol (IP) address.                   |
| `URL`                              | Represents a Uniform Resource Locator (used for web resources). |
| `URLConnection`                    | Manages a communication link between an application and a URL.  |
| `Socket`                           | Enables TCP client-side communication.                          |
| `ServerSocket`                     | Enables TCP server-side communication.                          |
| `DatagramSocket`, `DatagramPacket` | Used for UDP-based communication.                               |
| `NetworkInterface`                 | Provides information about network interfaces on the system.    |

### **1. The `InetAddress` Class**

The `InetAddress` class represents an IP address — either a local or remote machine’s address.
It provides methods to get the **host name** and **IP address** of any system connected to the network.

#### **Common Methods**

| **Method**               | **Description**                                    |
| ------------------------ | -------------------------------------------------- |
| `getLocalHost()`         | Returns the local host information.                |
| `getByName(String host)` | Returns the IP address of the specified host name. |
| `getHostName()`          | Returns the hostname of the IP address.            |
| `getHostAddress()`       | Returns the IP address as a string.                |

#### **Example:**

```java
import java.net.*;

public class InetAddressExample {
    public static void main(String[] args) {
        try {
            InetAddress ip = InetAddress.getLocalHost();
            System.out.println("Local Host Name: " + ip.getHostName());
            System.out.println("Local Host Address: " + ip.getHostAddress());

            InetAddress google = InetAddress.getByName("www.google.com");
            System.out.println("Google IP: " + google.getHostAddress());
        } catch (UnknownHostException e) {
            e.printStackTrace();
        }
    }
}
```

**Output Example:**

```
Local Host Name: MyPC
Local Host Address: 192.168.1.4
Google IP: 142.250.77.100
```

### **2. The `URL` and `URLConnection` Classes**

The **`URL` (Uniform Resource Locator)** class represents a web address — for example,
`https://www.example.com/index.html`.

Java’s `URL` class allows a program to **access web resources** directly, just like a browser does.
The **`URLConnection`** class handles the actual communication (reading data, sending requests, etc.).

#### **Creating a URL Object**

```java
URL url = new URL("https://www.example.com");
```

#### **Common Methods**

| **Method**         | **Description**                               |
| ------------------ | --------------------------------------------- |
| `getProtocol()`    | Returns the protocol (e.g., “http”, “https”). |
| `getHost()`        | Returns the host name.                        |
| `getPort()`        | Returns the port number.                      |
| `getFile()`        | Returns the file path.                        |
| `openConnection()` | Opens a connection to the resource.           |

#### **Example: Reading Data from a URL**

```java
import java.io.*;
import java.net.*;

public class ReadURLExample {
    public static void main(String[] args) {
        try {
            URL url = new URL("https://www.example.com");
            BufferedReader reader = new BufferedReader(
                new InputStreamReader(url.openStream())
            );

            String line;
            while ((line = reader.readLine()) != null) {
                System.out.println(line);
            }
            reader.close();
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
}
```

**Explanation:**

* The program connects to the given URL.
* It reads data line by line using `InputStreamReader` and prints it to the console.

This demonstrates how Java integrates I/O and networking seamlessly.

### **3. The `Socket` and `ServerSocket` Classes (TCP)**

Java supports both **TCP (Transmission Control Protocol)** and **UDP (User Datagram Protocol)** communication.

**TCP** is *connection-oriented*: it establishes a reliable connection between client and server before data transfer.
In Java, this is done using the `Socket` (for client) and `ServerSocket` (for server) classes.

#### **How TCP Works in Java**

* The **server** creates a `ServerSocket` object to listen on a specific port.
* The **client** creates a `Socket` to connect to that port on the server.
* Once connected, both can send and receive data using `InputStream` and `OutputStream`.

#### **Server Example**

```java
import java.io.*;
import java.net.*;

public class ServerExample {
    public static void main(String[] args) {
        try {
            ServerSocket server = new ServerSocket(8080);
            System.out.println("Server started, waiting for connection...");

            Socket socket = server.accept();
            System.out.println("Client connected.");

            DataInputStream in = new DataInputStream(socket.getInputStream());
            String message = in.readUTF();
            System.out.println("Client says: " + message);

            in.close();
            socket.close();
            server.close();
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
}
```

#### **Client Example**

```java
import java.io.*;
import java.net.*;

public class ClientExample {
    public static void main(String[] args) {
        try {
            Socket socket = new Socket("localhost", 8080);

            DataOutputStream out = new DataOutputStream(socket.getOutputStream());
            out.writeUTF("Hello from client!");

            out.close();
            socket.close();
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
}
```

**Explanation:**
When you run the server first, then the client, the client sends a message through the network socket, and the server receives and displays it.

This is the simplest example of **TCP communication** in Java.

### **4. The `DatagramSocket` and `DatagramPacket` Classes (UDP)**

**UDP (User Datagram Protocol)** is a *connectionless* communication method — faster but less reliable than TCP.
Each piece of data is called a **datagram**, and it’s sent without ensuring delivery.

In Java:

* `DatagramPacket` represents the data itself.
* `DatagramSocket` is used to send or receive packets.

#### **Example (Simple UDP Communication)**

```java
// Sender
DatagramSocket ds = new DatagramSocket();
String msg = "Hello UDP";
InetAddress ip = InetAddress.getByName("localhost");
DatagramPacket dp = new DatagramPacket(msg.getBytes(), msg.length(), ip, 3000);
ds.send(dp);
ds.close();
```

```java
// Receiver
DatagramSocket ds = new DatagramSocket(3000);
byte[] buf = new byte[1024];
DatagramPacket dp = new DatagramPacket(buf, 1024);
ds.receive(dp);
String msg = new String(dp.getData(), 0, dp.getLength());
System.out.println("Received: " + msg);
ds.close();
```

### **5. Differences between TCP and UDP**

| **TCP**                                    | **UDP**                                    |
| ------------------------------------------ | ------------------------------------------ |
| Connection-oriented                        | Connectionless                             |
| Reliable, ensures delivery                 | Unreliable, packets may be lost            |
| Slower, due to acknowledgment              | Faster, minimal overhead                   |
| Uses `Socket` and `ServerSocket`           | Uses `DatagramSocket` and `DatagramPacket` |
| Suitable for file transfer, chat, web apps | Suitable for games, streaming, VoIP        |

### **6. Java Networking Advantages**

1. **Platform Independence:** Works uniformly across operating systems.
2. **Integrated I/O Streams:** Uses the same Input/Output stream classes.
3. **High-Level Abstraction:** Simplifies complex socket communication.
4. **Security Features:** Built-in security mechanisms like sandboxing for applets.
5. **Support for Internet Protocols:** Works with HTTP, FTP, SMTP, etc.


--- 
# TCP/IP Client Sockets

In Java networking, the **Socket** mechanism provides the foundation for communication between two applications — usually referred to as the **client** and the **server**.

When this communication happens using the **TCP/IP protocol (Transmission Control Protocol / Internet Protocol)**, it is handled through **client sockets** and **server sockets**.

A **TCP socket** is essentially a virtual “doorway” through which two programs exchange a continuous stream of data, guaranteeing **reliability**, **ordering**, and **error checking**.

### **Concept of TCP/IP**

**TCP/IP** is the fundamental communication protocol of the internet and most local networks.

* **TCP (Transmission Control Protocol)** ensures that data is transmitted **reliably** — it breaks data into packets, numbers them, sends them, and ensures they reach in the correct order.
* **IP (Internet Protocol)** handles **addressing and routing**, ensuring that data packets reach the right destination.

In Java, the **`java.net`** package implements TCP/IP communication through **Socket programming**.

### **What is a Socket?**

A **socket** represents an endpoint for communication between two machines.
Every socket is defined by a combination of:

* An **IP address** (identifies the machine), and
* A **port number** (identifies a specific process or service).

Together, they form a **unique communication channel**, like:

```
192.168.1.5:8080
```

### **Client–Server Model**

In TCP communication, one application acts as a **server**, waiting for connection requests;
the other acts as a **client**, initiating the connection.

#### **Process Flow:**

1. The **server** creates a `ServerSocket` object and listens on a specific port.
2. The **client** creates a `Socket` object and requests a connection to that port.
3. When the server accepts the request, a **TCP connection** is established.
4. Both can now send and receive data through **I/O streams**.
5. When done, both close their sockets.

### **TCP Client Socket in Java**

On the **client side**, communication begins by creating a **`Socket`** object.
The constructor of `Socket` tries to connect to a specific server (identified by hostname/IP and port number).
### **Syntax:**

```java
Socket clientSocket = new Socket(String host, int port);
```

Here:

* **`host`** → IP address or domain name of the server
* **`port`** → the port number on which the server is listening

If the connection succeeds, a **TCP connection** is established.
If it fails, a **`IOException`** (commonly `ConnectException`) is thrown.

### **Important Classes and Methods**

| **Class / Method**  | **Description**                                           |
| ------------------- | --------------------------------------------------------- |
| `Socket`            | Used by the client to connect to the server.              |
| `getInputStream()`  | Returns an input stream for reading data from the server. |
| `getOutputStream()` | Returns an output stream for sending data to the server.  |
| `close()`           | Closes the socket and releases resources.                 |
### **Example: TCP Client Program**

```java
import java.io.*;
import java.net.*;

public class TCPClient {
    public static void main(String[] args) {
        try {
            // 1. Connect to server at localhost on port 5000
            Socket socket = new Socket("localhost", 5000);
            System.out.println("Connected to the server.");

            // 2. Get output stream to send data to server
            DataOutputStream out = new DataOutputStream(socket.getOutputStream());
            out.writeUTF("Hello, Server! This is the Client.");

            // 3. Get input stream to read response from server
            DataInputStream in = new DataInputStream(socket.getInputStream());
            String message = in.readUTF();
            System.out.println("Server says: " + message);

            // 4. Close streams and socket
            in.close();
            out.close();
            socket.close();
        } catch (IOException e) {
            System.out.println("Connection error: " + e.getMessage());
        }
    }
}
```

### **Example: TCP Server Program (for Reference)**

```java
import java.io.*;
import java.net.*;

public class TCPServer {
    public static void main(String[] args) {
        try {
            // 1. Create server socket on port 5000
            ServerSocket serverSocket = new ServerSocket(5000);
            System.out.println("Server started. Waiting for client...");

            // 2. Wait for client connection
            Socket socket = serverSocket.accept();
            System.out.println("Client connected.");

            // 3. Create input/output streams for communication
            DataInputStream in = new DataInputStream(socket.getInputStream());
            DataOutputStream out = new DataOutputStream(socket.getOutputStream());

            // 4. Read client message
            String message = in.readUTF();
            System.out.println("Client says: " + message);

            // 5. Send reply back
            out.writeUTF("Message received loud and clear.");

            // 6. Close connections
            in.close();
            out.close();
            socket.close();
            serverSocket.close();
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
}
```

**Execution Order:**

1. Run the `TCPServer` first — it waits for a client connection.
2. Then run the `TCPClient` — it connects and sends a message.
3. Both programs exchange data using the socket streams.

### **Explanation of Client Socket Communication**

When the client executes:

```java
Socket socket = new Socket("localhost", 5000);
```

it performs these actions:

1. Contacts the server machine at IP `localhost`.
2. Requests a connection on port `5000`.
3. If the server is listening, TCP sets up a reliable connection.
4. The `Socket` object now provides two streams:

   * **InputStream** (to receive data)
   * **OutputStream** (to send data)

### **How TCP Ensures Reliability**

TCP provides several mechanisms that make it **connection-oriented and reliable**:

* **Acknowledgment:** Each packet sent is confirmed by the receiver.
* **Retransmission:** Lost packets are resent automatically.
* **Sequencing:** Data arrives in the same order it was sent.
* **Error Checking:** Ensures data integrity.
* **Flow Control:** Balances sending and receiving speeds.

Because of these features, TCP is ideal for applications like:

* File transfer
* Chat systems
* Web communication (HTTP)
* Email (SMTP, POP3)

### **Client Socket Stream Handling**

Once a connection is established, data transfer occurs through **streams**, similar to file I/O.

| **Stream Type** | **Purpose**                    |
| --------------- | ------------------------------ |
| `InputStream`   | Receives data from the server. |
| `OutputStream`  | Sends data to the server.      |

You can use:

* **`DataInputStream` / `DataOutputStream`** for primitive data types, or
* **`BufferedReader` / `PrintWriter`** for text communication.

### **Example (Using PrintWriter and BufferedReader)**

```java
import java.io.*;
import java.net.*;

public class TCPClientText {
    public static void main(String[] args) {
        try (Socket socket = new Socket("localhost", 6000);
             PrintWriter out = new PrintWriter(socket.getOutputStream(), true);
             BufferedReader in = new BufferedReader(new InputStreamReader(socket.getInputStream()))) {

            out.println("Hello Server, how are you?");
            String response = in.readLine();
            System.out.println("Server: " + response);

        } catch (IOException e) {
            e.printStackTrace();
        }
    }
}
```

**Explanation:**
Here we use text streams for simplicity — great for small message-based communication.

### **Advantages of TCP Client Sockets**

1. **Reliable Communication:** No data loss or duplication.
2. **Ordered Delivery:** Packets arrive in sequence.
3. **Stream-Based:** Allows continuous flow of data like reading/writing files.
4. **Error-Free Transmission:** TCP performs error detection and correction.
5. **High Control:** You can manage connection, buffering, and data flow.

### **Limitations**

1. **Slightly Slower:** Reliability comes with overhead.
2. **More Resources Needed:** Each connection consumes system resources.
3. **Blocking Nature:** Sockets block until data is available (unless made non-blocking).
4. **Not Ideal for Real-Time Data:** UDP is better for streaming or live feeds.

### **Common Exceptions**

| **Exception**          | **Cause**                                    |
| ---------------------- | -------------------------------------------- |
| `UnknownHostException` | Invalid host name or IP address.             |
| `ConnectException`     | Connection refused or server not running.    |
| `SocketException`      | Socket closed or broken connection.          |
| `IOException`          | General I/O errors during data transmission. |
### **Real-Life Applications**

* **Web browsers and servers (HTTP over TCP/IP)**
* **Chat applications and messengers**
* **FTP clients and servers**
* **Database communication**
* **Remote method invocation (RMI)**


--- 
# URL and URLConnection in Java

Networking in Java is largely built around the concept of the **URL (Uniform Resource Locator)**, which represents an address of a resource on the Internet — such as a web page, image, file, or API endpoint.

To interact with these resources, Java provides two key classes:

* **`java.net.URL`** – represents the actual resource’s address.
* **`java.net.URLConnection`** – provides a communication link (connection) between the Java application and the resource referred to by the URL.

Both are part of the **`java.net`** package, which allows programs to access and interact with networked data in a platform-independent manner.

## **1. The `URL` Class**

A **URL (Uniform Resource Locator)** is a standardized way to identify and locate resources on the internet.
In Java, the **`URL` class** represents such an address and provides methods to **parse, query, and connect** to that resource.

**Package:** `java.net`
**Class Declaration:**

```java
public final class URL extends Object implements Serializable
```

### **General Syntax**

```java
URL url = new URL("protocol://host:port/filepath#ref");
```

Where:

* **protocol:** Communication protocol (e.g., `http`, `https`, `ftp`, `file`).
* **host:** Name or IP address of the server.
* **port:** (Optional) The port number (default for HTTP is 80).
* **filepath:** Path to the resource.
* **ref:** (Optional) A reference or anchor within the resource (like `#section1` in HTML).

### **Example**

```java
import java.net.*;

public class URLExample {
    public static void main(String[] args) throws Exception {
        URL url = new URL("https://www.example.com:443/index.html#intro");

        System.out.println("Protocol: " + url.getProtocol());
        System.out.println("Host: " + url.getHost());
        System.out.println("Port: " + url.getPort());
        System.out.println("File: " + url.getFile());
        System.out.println("Reference: " + url.getRef());
    }
}
```

**Output:**

```
Protocol: https
Host: www.example.com
Port: 443
File: /index.html
Reference: intro
```

### **Important URL Methods**

| Method             | Description                                                              |
| ------------------ | ------------------------------------------------------------------------ |
| `getProtocol()`    | Returns the protocol (e.g., `http`, `ftp`).                              |
| `getHost()`        | Returns the hostname of the URL.                                         |
| `getPort()`        | Returns the port number or -1 if not set.                                |
| `getFile()`        | Returns the file name or path of the URL.                                |
| `getRef()`         | Returns the reference or anchor part of the URL.                         |
| `openConnection()` | Opens a connection to the resource and returns a `URLConnection` object. |
| `openStream()`     | Opens an input stream to read data directly from the resource.           |

### **Example: Reading Data via URLConnection**

```java
import java.io.*;
import java.net.*;

public class URLConnectionRead {
    public static void main(String[] args) throws Exception {
        URL url = new URL("https://www.example.com");
        URLConnection conn = url.openConnection();

        BufferedReader br = new BufferedReader(new InputStreamReader(conn.getInputStream()));
        String input;
        while ((input = br.readLine()) != null) {
            System.out.println(input);
        }
        br.close();
    }
}
```

This version uses the `URLConnection` instead of a direct stream — allowing more control, such as modifying headers or setting timeouts before reading data.

---

### **Example: Writing Data via URLConnection (POST Request)**

```java
import java.io.*;
import java.net.*;

public class URLConnectionWrite {
    public static void main(String[] args) throws Exception {
        URL url = new URL("https://example.com/submit");
        URLConnection conn = url.openConnection();

        conn.setDoOutput(true);  // enable writing
        OutputStreamWriter out = new OutputStreamWriter(conn.getOutputStream());
        out.write("name=John&age=25");
        out.close();

        BufferedReader br = new BufferedReader(new InputStreamReader(conn.getInputStream()));
        String line;
        while ((line = br.readLine()) != null) {
            System.out.println(line);
        }
        br.close();
    }
}
```

**Explanation:**
This demonstrates sending data to a server (like an HTTP form submission).
We enable output with `setDoOutput(true)` and then write the data through the connection.

---

## **3. Difference Between URL and URLConnection**

| Feature         | `URL`                                          | `URLConnection`                                                                       |
| --------------- | ---------------------------------------------- | ------------------------------------------------------------------------------------- |
| **Purpose**     | Represents the address of a resource.          | Represents an active connection to that resource.                                     |
| **Creation**    | Created directly using `new URL()`.            | Created by calling `url.openConnection()`.                                            |
| **Control**     | Limited (only reading via `openStream()`).     | Full control (headers, request properties, both read/write).                          |
| **Data Access** | Only reading possible.                         | Reading and writing both possible.                                                    |
| **Methods**     | Parsing methods like `getHost()`, `getFile()`. | Connection control methods like `connect()`, `getInputStream()`, `getOutputStream()`. |

---  
# Datagram

In networking, a **datagram** is a **self-contained, independent packet of data** that carries enough information to be routed from the source to the destination *without relying on previous exchanges*.

In Java, **datagrams** are used to implement communication based on the **UDP (User Datagram Protocol)** — which is a **connectionless, unreliable, but fast** transport protocol.

Unlike TCP (which uses streams and requires a persistent connection), **UDP** sends messages as individual packets — each packet (datagram) is sent independently, and delivery is *not guaranteed*.

## **Datagram in Java**

To implement UDP-based communication, Java provides two main classes in the **`java.net`** package:

| Class                | Description                                                                          |
| -------------------- | ------------------------------------------------------------------------------------ |
| **`DatagramPacket`** | Represents the actual data packet sent or received over the network.                 |
| **`DatagramSocket`** | Provides the mechanism (socket) through which datagram packets are sent or received. |

Together, they form the foundation for connectionless communication in Java.

## **Characteristics of Datagram Communication**

1. **Connectionless:**
   No dedicated connection between sender and receiver; packets can travel different routes.

2. **Unreliable but Fast:**
   Delivery order and success are not guaranteed, but communication is faster and lightweight.

3. **Packet-Based:**
   Each message is sent in an independent packet (a `DatagramPacket` object).

4. **No Acknowledgement:**
   The sender does not know whether the receiver received the packet.

5. **Used For:**

   * Real-time systems (voice/video streaming)
   * Games
   * Broadcast or multicast data

## **Classes Involved**

### **A. `DatagramPacket` Class**

`DatagramPacket` represents a **packet of data** that can be sent or received via a `DatagramSocket`.

**Class Declaration:**

```java
public final class DatagramPacket extends Object
```

#### **Constructors**

1. **For Receiving Data**

```java
DatagramPacket(byte[] buffer, int length)
```

* `buffer` – byte array to store received data
* `length` – size of the buffer

2. **For Sending Data**

```java
DatagramPacket(byte[] buffer, int length, InetAddress address, int port)
```

* `buffer` – byte array containing data to send
* `length` – number of bytes to send
* `address` – destination address
* `port` – destination port number

#### **Common Methods**

| Method                 | Description                                          |
| ---------------------- | ---------------------------------------------------- |
| `getData()`            | Returns the data buffer.                             |
| `getLength()`          | Returns the number of bytes of data.                 |
| `getAddress()`         | Returns the IP address of the destination or source. |
| `getPort()`            | Returns the port number.                             |
| `setData(byte[] data)` | Sets the data buffer.                                |

### **B. `DatagramSocket` Class**

`DatagramSocket` is the **endpoint** used to send and receive datagram packets.

**Class Declaration:**

```java
public class DatagramSocket extends Object
```

#### **Constructors**

1. **Default Constructor**

```java
DatagramSocket()
```

Creates a datagram socket and binds it to an available port on the local host.

2. **Parameterized Constructor**

```java
DatagramSocket(int port)
```

Binds the socket to a specific port (useful for the receiving side).

#### **Common Methods**

| Method                      | Description                                       |
| --------------------------- | ------------------------------------------------- |
| `send(DatagramPacket p)`    | Sends the specified datagram packet.              |
| `receive(DatagramPacket p)` | Receives a datagram packet.                       |
| `close()`                   | Closes the socket.                                |
| `getLocalPort()`            | Returns the port number of the socket.            |
| `setSoTimeout(int timeout)` | Sets timeout for blocking `receive()` operations. |


## **Working of Datagram Communication**

Datagram communication in Java works like this:

1. **Sender** creates a `DatagramSocket`.
2. Data is converted into bytes and wrapped into a `DatagramPacket` with the destination IP and port.
3. The packet is sent using the `send()` method.
4. **Receiver** listens on a specific port using a `DatagramSocket`.
5. It creates an empty `DatagramPacket` and calls `receive()` to fetch incoming data.
6. Once received, the byte data is converted back into a string or object.

## **Example: Sending a Datagram (UDP Sender)**

```java
import java.net.*;

public class UDPSender {
    public static void main(String[] args) throws Exception {
        DatagramSocket socket = new DatagramSocket();
        String msg = "Hello from UDP Sender!";
        byte[] buffer = msg.getBytes();

        InetAddress receiverAddress = InetAddress.getByName("localhost");
        int port = 9876;

        DatagramPacket packet = new DatagramPacket(buffer, buffer.length, receiverAddress, port);
        socket.send(packet);

        System.out.println("Message sent to receiver.");
        socket.close();
    }
}
```

## **Example: Receiving a Datagram (UDP Receiver)**

```java
import java.net.*;

public class UDPReceiver {
    public static void main(String[] args) throws Exception {
        DatagramSocket socket = new DatagramSocket(9876);
        byte[] buffer = new byte[1024];

        DatagramPacket packet = new DatagramPacket(buffer, buffer.length);
        socket.receive(packet);  // waits for a packet

        String msg = new String(packet.getData(), 0, packet.getLength());
        System.out.println("Received message: " + msg);

        socket.close();
    }
}
```

### **Explanation of Flow**

1. **Receiver** runs first and waits on port `9876`.
2. **Sender** sends a message to that port using the `DatagramPacket`.
3. Receiver’s socket picks it up, extracts data, and displays it.
4. Both sides close their sockets after communication.

## **Key Advantages of Datagram (UDP) Communication**

* **Speed:** Very fast as there is no connection setup overhead.
* **Efficiency:** Ideal for small, frequent messages.
* **Broadcasting/Multicasting:** Supports one-to-many communication.
* **Low Resource Usage:** Lightweight compared to TCP.

## **Limitations of Datagram Communication**

* **Unreliable:** No guarantee of delivery, order, or duplication control.
* **No Connection Tracking:** No acknowledgment or retransmission.
* **Packet Size Limit:** Typically limited to around 64 KB per packet.
* **Error Handling:** Application itself must handle missing data or reordering.

## **Difference Between TCP and UDP (Datagram)**

| Feature             | TCP                                        | UDP (Datagram)                     |
| ------------------- | ------------------------------------------ | ---------------------------------- |
| **Connection Type** | Connection-oriented                        | Connectionless                     |
| **Reliability**     | Reliable (error checking & acknowledgment) | Unreliable                         |
| **Speed**           | Slower due to overhead                     | Faster                             |
| **Data Flow**       | Stream-based                               | Packet-based                       |
| **Use Case**        | File transfer, email, web                  | Streaming, gaming, voice chat      |
| **Classes Used**    | `Socket`, `ServerSocket`                   | `DatagramSocket`, `DatagramPacket` |
## **Exception Handling in Datagram**

Possible exceptions:

* **`SocketException`** – Error creating or accessing socket.
* **`UnknownHostException`** – Invalid or unresolvable hostname.
* **`IOException`** – General I/O or network errors during send/receive.

--- 

> “A Datagram in Java is a lightweight, connectionless packet of data sent over the network using the UDP protocol, represented by `DatagramPacket`, and managed by `DatagramSocket`.”

