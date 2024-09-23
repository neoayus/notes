
## **Python Overview, Data Types, Expressions, and Control Flow**

### **Python Interpreter and Interactive Mode**

- **Python Interpreter**:  
  The Python interpreter is a program that reads and executes Python code. Python code can be executed in two ways:
  
  1.  **Interactive Mode**: This allows you to execute Python commands one at a time. You can access it by typing `python` in the terminal.
  
  2.  **Script Mode**: Python code is written in a file (with a `.py` extension) and executed all at once using `python filename.py`.

- **Interactive Mode Example**:
  ```bash
  $ python
  >>> print("Hello, World!")
  ```

### **Debugging**

- **Debugging**:  
  Debugging is the process of identifying and fixing errors in code. Python provides several ways to debug code:
  - **print statements**: The simplest way to debug is by using `print()` to display the value of variables at different stages in your code.
  - **PDB (Python Debugger)**: Python's built-in debugger can be used to step through your code and inspect its state.
### **Assignment and Comments**

- **Assignment**:  
  Assignment in Python is used to give values to variables. 
  The `=` operator is used for assignment.

  Example:
  ```python
  x = 10
  name = "Alice"
  ```

- **Comments**:  
  Comments are used to explain code and are ignored by the interpreter. They begin with a `#`.

  Example:
  ```python
  # This is a comment
  x = 10  # Assigns 10 to variable x
  ```

### **Numeric Data Types and Character Sets**

- **Numeric Data Types**:  
  Python has several types of numeric data:
  - **Integers (`int`)**: Whole numbers, positive or negative, without a decimal point.
    ```python
    age = 25
    ```
  - **Floating Point Numbers (`float`)**: Numbers that contain a decimal point.
    ```python
    price = 19.99
    ```
  - **Complex Numbers (`complex`)**: Numbers with a real and imaginary part.
    ```python
    z = 3 + 2j
    ```

- **Character Sets**:  
  Python supports Unicode character sets, allowing for a vast range of characters, including non-English letters. Characters are represented as strings in Python.

  Example:
  ```python
  char = 'a'
  ```

### **Expressions**

- **Expressions**:  
  An expression in Python is a combination of variables, operations, and values that produce a result. For example, `5 + 3` is an expression that evaluates to `8`.

  Example:
  ```python
  result = (10 + 2) * 5
  print(result)  # Output: 60
  ```

- **Arithmetic Operations**:  
  Python supports the following arithmetic operations:
  - `+` (Addition)
  - `-` (Subtraction)
  - `*` (Multiplication)
  - `/` (Division)
  - `//` (Floor Division)
  - `%` (Modulus)
  - `**` (Exponentiation)

  Example:
  ```python
  a = 10
  b = 3
  print(a + b)   # Output: 13
  print(a / b)   # Output: 3.333
  print(a // b)  # Output: 3 (Floor Division)
  print(a ** b)  # Output: 1000 (Exponentiation)
  ```

## **Conditionals and Iteration**

### **Conditionals**

- **Boolean Values and Operators**:  
  Boolean values are `True` and `False`, representing truth values. They are used in conditional statements to control the flow of execution. Boolean operators include:
  - **`and`**: Returns `True` if both operands are `True`.
  - **`or`**: Returns `True` if at least one operand is `True`.
  - **`not`**: Returns `True` if the operand is `False`, and `False` if the operand is `True`.

  Example:
  ```python
  x = 10
  y = 20
  print(x > 5 and y < 25)  # Output: True
  print(not (x > 5))      # Output: False
  ```

- **Conditional (if)**:  
  The `if` statement evaluates a condition and executes the block of code if the condition is `True`.

  Example:
  ```python
  age = 18
  if age >= 18:
      print("You are an adult.")
  ```

- **Alternative (if-else)**:  
  The `if-else` statement allows for an alternative block of code to be executed if the condition is `False`.

  Example:
  ```python
  age = 16
  if age >= 18:
      print("You are an adult.")
  else:
      print("You are not an adult.")
  ```

- **Chained Conditional (if-elif-else)**:  
  The `if-elif-else` statement allows for multiple conditions to be evaluated. If the `if` condition is `False`, the `elif` conditions are evaluated in order. If none are `True`, the `else` block is executed.

  Example:
  ```python
  age = 20
  if age < 13:
      print("You are a child.")
  elif age < 20:
      print("You are a teenager.")
  else:
      print("You are an adult.")
  ```

### **Iteration**

- **`while` Loop**:  
  The `while` loop repeatedly executes a block of code as long as its condition is `True`.

  Example:
  ```python
  count = 0
  while count < 5:
      print(count)
      count += 1
  ```

- **`for` Loop**:  
  The `for` loop iterates over a sequence (like a list, tuple, or string) and executes a block of code for each item.

  Example:
  ```python
  for i in range(5):
      print(i)
  ```

- **`break`**:  
  The `break` statement exits the nearest enclosing loop, regardless of the loop's condition.

  Example:
  ```python
  count = 0
  while True:
      print(count)
      if count == 3:
          break
      count += 1
  ```

- **`continue`**:  
  The `continue` statement skips the rest of the code inside the current loop iteration and proceeds to the next iteration.

  Example:
  ```python
  for i in range(5):
      if i == 2:
          continue
      print(i)
  ```

- **`pass`**:  
  The `pass` statement is a placeholder that does nothing. It is used when a statement is syntactically required but you do not want to execute any code.

  Example:
  ```python
  for i in range(5):
      if i == 3:
          pass  # Do nothing
      else:
          print(i)
  ```

---
---
---
# UNIT 01 ENDS HERE ! 
# \>GO TO [UNIT 02](Python-02%20(Strings,%20Lists,%20Tuples,%20Dictionaried).md) 
