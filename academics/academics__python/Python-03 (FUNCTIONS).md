## **Functions** 

Functions are blocks of reusable code that perform a specific task. They allow for cleaner, modular, and more readable code, making problem-solving more efficient.

### **Functions as Abstraction Mechanisms**

Functions simplify the code by abstracting away details, allowing you to focus on the bigger picture.

```python
def greet_user(name):
    return f"Hello, {name}!"
```
### **Recursive Functions**

A **recursive function** is a function that calls itself to solve a smaller instance of the same problem. It breaks down a complex task into simpler subproblems, eventually reaching a **base case** that stops the recursion.

#### **Key Elements of a Recursive Function**:

1. **Base Case**: The condition under which the recursion ends. Without a base case, the function would continue calling itself indefinitely, leading to a stack overflow.
2. **Recursive Case**: The part of the function where the function calls itself to solve a smaller problem.


Calculating the sum of a list of numbers recursively.
```python
def sum_list(numbers):
    if len(numbers) == 0:  # Base case
        return 0
    else:
        return numbers[0] + sum_list(numbers[1:])  # Recursive case
```

### **Managing a Program’s Namespace**

A **namespace** holds names (variables, functions, etc.) and maps them to objects. It helps keep track of variables and avoids naming conflicts.

#### **Types of Namespaces**:
1. **Local Namespace**: Inside a function or class.
2. **Global Namespace**: Outside all functions and classes.
3. **Built-in Namespace**: Includes functions like `print()` and `len()`.

```python
x = 10  # Global variable

def example():
    x = 5  # Local variable
    print(x)  # Output: 5

example()
print(x)  # Output: 10 (global x remains unchanged)
```

### **Higher-Order Functions**

A **higher-order function** can take other functions as arguments or return a function as output.

**Example 1**: Using `map()` to apply a function to each element in a list.
```python
numbers = [1, 2, 3, 4]
squared = list(map(lambda x: x ** 2, numbers))
print(squared)  # Output: [1, 4, 9, 16]
```

**Example 2**: `filter()` to filter elements based on a condition.
```python
numbers = [1, 2, 3, 4]
evens = list(filter(lambda x: x % 2 == 0, numbers))
print(evens)  # Output: [2, 4]
```

## **Objects and Classes in Python**

### **Objects and Classes**

A **class** is a blueprint for creating objects (instances). Objects represent data and functionality together. 

#### **Creating a Class**:
```python
class Dog:
    def __init__(self, name, breed):
        self.name = name
        self.breed = breed

    def bark(self):
        return f"{self.name} says Woof!"

# Creating an object (instance)
my_dog = Dog("Buddy", "Golden Retriever")
print(my_dog.bark())  # Output: Buddy says Woof!
```
Here, `Dog` is a class, and `my_dog` is an object created from the `Dog` class.

---

### **Data Modelling: Rational Numbers**

You can model real-world data like **rational numbers** using classes. A rational number can be represented by a numerator and a denominator.

**Example**:
```python
class Rational:
    def __init__(self, numerator, denominator):
        self.numerator = numerator
        self.denominator = denominator

    def __str__(self):
        return f"{self.numerator}/{self.denominator}"

r = Rational(2, 5)
print(r)  # Output: 2/5
```

---

### **Operator Overloading**

You can define custom behaviors for operators like `+`, `-`, etc., in your classes by overloading them.

**Example**: Overloading the `+` operator for `Rational` numbers.
```python
class Rational:
    def __init__(self, numerator, denominator):
        self.numerator = numerator
        self.denominator = denominator

    def __add__(self, other):
        new_numerator = self.numerator * other.denominator + other.numerator * self.denominator
        new_denominator = self.denominator * other.denominator
        return Rational(new_numerator, new_denominator)
    
    def __str__(self):
        return f"{self.numerator}/{self.denominator}"

r1 = Rational(1, 2)
r2 = Rational(1, 3)
print(r1 + r2)  # Output: 5/6
```

---

### **Comparison Methods**

Classes can also have custom comparison methods like `__lt__` (less than), `__eq__` (equal to), etc., to define how objects should be compared.

---

### **Pickle for Permanent Storage of Objects**

Python’s `pickle` module allows you to store and retrieve objects in a file, ensuring that objects can be used later.

#### **Saving an Object to a File**:
```python
import pickle

data = {"name": "Alice", "age": 25}

# Writing the object to a file
with open("data.pkl", "wb") as file:
    pickle.dump(data, file)
```

#### **Reading the Object from a File**:
```python
with open("data.pkl", "rb") as file:
    loaded_data = pickle.load(file)
    print(loaded_data)  # Output: {'name': 'Alice', 'age': 25}
```

---

### **Input of Objects and Try-Except Statements**

When working with user input and objects, use **try-except** blocks to handle errors gracefully.

**Example**:
```python
try:
    age = int(input("Enter your age: "))
    print(f"Your age is {age}")
except ValueError:
    print("Invalid input! Please enter a number.")
```

---

### **Structuring Classes: Inheritance and Polymorphism**

**Inheritance** allows a class to inherit properties and methods from another class, promoting code reuse.

**Polymorphism** lets objects of different classes respond to the same method in different ways.

#### **Inheritance Example**:
```python
class Animal:
    def speak(self):
        return "Animal sound"

class Dog(Animal):
    def speak(self):
        return "Woof!"

dog = Dog()
print(dog.speak())  # Output: Woof!
```
Here, `Dog` inherits from `Animal` but overrides the `speak` method with its own implementation.

---

These detailed notes should help you understand the key concepts and give you solid material to write for your exams. Let me know if you need any further clarification!