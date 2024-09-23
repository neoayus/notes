---
---

## **Strings**

A string is a sequence of characters Stored at contagious memory location. Strings are enclosed either in single quotes (`'`) or double quotes (`"`).

```python
text = "Hello, World!"
```

### **String Slices**

- **String Slicing**:  
  String slicing allows you to extract a portion of a string by specifying a range of indices. The syntax is:  
  `string[start:end]` where `start` is the index to begin (inclusive) and `end` is the index to stop (exclusive).

  ```python
  text = "Hello, World!"
  print(text[0:5])  # Output: Hello
  print(text[7:])   # Output: World!
  print(text[:5])   # Output: Hello
  ```

  You can use negative indices to slice from the end of the string:
  ```python
  print(text[-6:-1])  # Output: World
  ```

### **Immutability**

- **Immutability**:  
  Strings in Python are immutable, meaning once a string is created, it cannot be modified. Any operation that seems to modify a string creates a new string.

  ```python
  text = "Hello"
  # Modifying a character directly is not allowed
  # text[0] = "h"  # Error: 'str' object does not support item assignment

  # Creating a new string instead:
  new_text = "h" + text[1:]
  print(new_text)  # Output: hello
  ```

### **String Functions and Methods**

- **Common String Methods**:
  - `len(string)`: Returns the length of the string.
  - `string.lower()`: Converts all characters to lowercase.
  - `string.upper()`: Converts all characters to uppercase.
  - `string.strip()`: Removes leading and trailing spaces.
  - `string.replace(old, new)`: Replaces all occurrences of `old` with `new`.
  - `string.split(separator)`: Splits the string into a list based on the specified separator.

  Example:
  ```python
  text = " Hello, World! "
  print(len(text))            # Output: 15
  print(text.lower())         # Output: hello, world!
  print(text.strip())         # Output: Hello, World!
  print(text.replace("World", "Python"))  # Output: Hello, Python!
  print(text.split(","))      # Output: [' Hello', ' World! ']
  ```

- **String Concatenation**:  
  Strings can be combined using the `+` operator.

  Example:
  ```python
  greeting = "Hello"
  name = "Alice"
  message = greeting + ", " + name + "!"
  print(message)  # Output: Hello, Alice!
  ```
### **String Module**

- **String Module**:  
  The `string` module in Python provides constants and utility functions for working with strings. Common constants include:
  - `string.ascii_letters`: All ASCII letters (both lowercase and uppercase).
  - `string.digits`: All digits (`0-9`).
  - `string.punctuation`: All punctuation characters.

  Example:
  ```python
  import string
  print(string.ascii_letters)  # Output: 'abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ'
  print(string.digits)         # Output: '0123456789'
  ```


## **Lists**

A **list** in Python is a collection of items, which can be of any data type (numbers, strings, other lists, etc.). Lists are defined using square brackets `[]`, and the items are separated by commas.

```python
my_list = [1, 2, 3, "apple", "banana"]
```

### **List Operations**

- **Indexing**:  
  You can access individual items in a list by their index. Indexing starts at `0`.

  ```python
  my_list = [1, 2, 3, "apple", "banana"]
  print(my_list[0])  # Output: 1
  print(my_list[3])  # Output: apple
  ```

- **Updating Lists**:  
  Lists are mutable, meaning you can modify an item at a particular index.

  Example:
  ```python
  my_list[1] = "orange"
  print(my_list)  # Output: [1, 'orange', 3, 'apple', 'banana']
  ```

- **List Concatenation**:  
  You can combine two or more lists using the `+` operator.

  Example:
  ```python
  list1 = [1, 2, 3]
  list2 = [4, 5]
  combined = list1 + list2
  print(combined)  # Output: [1, 2, 3, 4, 5]
  ```

- **Repetition**:  
  Lists can be repeated using the `*` operator.

  Example:
  ```python
  my_list = [1, 2, 3]
  print(my_list * 2)  # Output: [1, 2, 3, 1, 2, 3]
  ```

### **List Slices**

- **List Slicing**:  
  Just like strings, lists can be sliced using the syntax `list[start:end]`.

  Example:
  ```python
  my_list = [10, 20, 30, 40, 50]
  print(my_list[1:4])  # Output: [20, 30, 40]
  print(my_list[:3])   # Output: [10, 20, 30]
  print(my_list[2:])   # Output: [30, 40, 50]
  ```

### **List Methods**

- **Common List Methods**:
  - `list.append(item)`: Adds an item to the end of the list.
  - `list.extend(iterable)`: Adds all items from another list (or any iterable) to the current list.
  - `list.insert(index, item)`: Inserts an item at a specified index.
  - `list.remove(item)`: Removes the first occurrence of the item from the list.
  - `list.pop(index)`: Removes and returns the item at the specified index (defaults to the last item if no index is given).
  - `list.sort()`: Sorts the list in ascending order.
  - `list.reverse()`: Reverses the list in place.
  - `list.index(item)`: Returns the index of the first occurrence of the item.

  ```python
  my_list = [10, 20, 30]
  my_list.append(40)
  print(my_list)  # Output: [10, 20, 30, 40]
  
  my_list.pop(2)
  print(my_list)  # Output: [10, 20, 40]
  ```

### **List Loop**

- **Looping Through Lists**:  
  You can loop through a list using a `for` loop to access each item.

  ```python
  my_list = ["apple", "banana", "cherry"]
  for item in my_list:
      print(item)
  # Output:
  # apple
  # banana
  # cherry
  ```

### **Mutability**

- **Mutability**:  
  Lists are **mutable**, meaning their elements can be changed after the list is created. You can modify, add, or remove elements from a list.

  Example:
  ```python
  my_list = [1, 2, 3]
  my_list[1] = 10
  print(my_list)  # Output: [1, 10, 3]
  ```

### **Aliasing**

 Aliasing occurs when two variables refer to the same list. Changes made to the list using one alias will affect the other.

  ```python
  list1 = [1, 2, 3]
  list2 = list1  # list2 is now an alias of list1
  list1[0] = 100
  print(list2)  # Output: [100, 2, 3]
  ```

### **Cloning Lists**

  To avoid aliasing, you can create a **clone** of a list by slicing or using the `copy()` method.

  Example using slicing:
  ```python
  list1 = [1, 2, 3]
  list2 = list1[:]  # Creates a copy of list1
  list1[0] = 100
  print(list2)  # Output: [1, 2, 3]  (list2 is unaffected)
  ```

  Example using `copy()`:
  ```python
  list1 = [1, 2, 3]
  list2 = list1.copy()  # Creates a copy of list1
  list1[0] = 100
  print(list2)  # Output: [1, 2, 3]
  ```

### **List Parameters**

- **List as Function Parameters**:  
  Lists can be passed to functions as parameters, and any changes made to the list inside the function will affect the original list (due to mutability).

  ```python
  def modify_list(lst):
      lst[0] = "Modified"
  
  my_list = [1, 2, 3]
  modify_list(my_list)
  print(my_list)  # Output: ['Modified', 2, 3]
  ```


## **Tuples**

A **tuple** in Python is a collection of ordered, immutable elements. Once a tuple is created, its values cannot be changed. Tuples are defined using parentheses `()` and can store multiple data types, just like lists.

```python
my_tuple = (1, 2, 3, "apple", "banana")
```

### **Key Characteristics of Tuples**:
- **Ordered**: Elements in a tuple maintain their order.
- **Immutable**: Elements cannot be modified once assigned.
- **Allows Duplicates**: Tuples can contain duplicate values.
- **Multiple Data Types**: A tuple can hold elements of different types (e.g., integers, strings, other tuples).

### **Tuple Assignment**

- **Tuple Packing**: You can assign multiple values to a tuple in a single statement. This is called **tuple packing**.

  ```python
  my_tuple = 1, 2, 3  # Packing values into a tuple
  print(my_tuple)     # Output: (1, 2, 3)
  ```

- **Tuple Unpacking**: You can also extract values from a tuple by assigning the tuple to a sequence of variables. This is called **tuple unpacking**.

  ```python
  my_tuple = (10, 20, 30)
  a, b, c = my_tuple  # Unpacking values into variables
  print(a, b, c)      # Output: 10 20 30
  ```

### **Tuple as Return Value**

- **Returning Multiple Values**:  
  A function can return multiple values by returning a tuple. This allows you to group multiple return values in a single object.

  ```python
  def calculate(a, b):
      sum_result = a + b
      product = a * b
      return sum_result, product  # Returning a tuple
  
  result = calculate(5, 3)
  print(result)  # Output: (8, 15)
  ```

- **Unpacking Return Values**:  
  You can directly unpack the values returned by a function into variables.

  ```python
  def calculate(a, b):
      sum_result = a + b
      product = a * b
      return sum_result, product
  
  sum_value, product_value = calculate(5, 3)
  print(sum_value)     # Output: 8
  print(product_value) # Output: 15
  ```

## **Dictionaries**

A **dictionary** in Python is an unordered collection of key-value pairs. Each key must be unique, and keys are used to access the corresponding values. Dictionaries are defined using curly braces `{}`.

```python
my_dict = {
    "name": "Alice",
    "age": 25,
    "city": "New York"
}
```

In this dictionary:
- Keys: `"name"`, `"age"`, `"city"`
- Values: `"Alice"`, `25`, `"New York"`

### **Dictionary Operations**

- **Accessing Values**:  
  You can access the value associated with a key using square brackets `[]`.

  ```python
  print(my_dict["name"])  # Output: Alice
  ```

- **Modifying Values**:  
  You can modify the value associated with a specific key.

  ```python
  my_dict["age"] = 30
  print(my_dict["age"])  # Output: 30
  ```

- **Adding New Key-Value Pairs**:  
  You can add a new key-value pair to a dictionary by simply assigning a value to a new key.

  ```python
  my_dict["profession"] = "Engineer"
  print(my_dict)  
  # Output: {'name': 'Alice', 'age': 30, 'city': 'New York', 'profession': 'Engineer'}
  ```

- **Deleting Key-Value Pairs**:  
  You can remove a key-value pair using the `del` statement.

  ```python
  del my_dict["city"]
  print(my_dict)  # Output: {'name': 'Alice', 'age': 30, 'profession': 'Engineer'}
  ```

- **Checking if a Key Exists**:  
  You can check if a key exists in a dictionary using the `in` keyword.

  ```python
  if "name" in my_dict:
      print("Key exists!")
  ```

### **Dictionary Methods**

- **`dict.keys()`**:  
  Returns a view object that displays a list of all the keys in the dictionary.

  ```python
  keys = my_dict.keys()
  print(keys)  # Output: dict_keys(['name', 'age', 'profession'])
  ```

- **`dict.values()`**:  
  Returns a view object that displays a list of all the values in the dictionary.

  ```python
  values = my_dict.values()
  print(values)  # Output: dict_values(['Alice', 30, 'Engineer'])
  ```

- **`dict.items()`**:  
  Returns a view object that displays a list of key-value tuple pairs in the dictionary.

  ```python
  items = my_dict.items()
  print(items)  # Output: dict_items([('name', 'Alice'), ('age', 30), ('profession', 'Engineer')])
  ```

- **`dict.get(key, default_value)`**:  
  Returns the value for the specified key. If the key doesn't exist, it returns the `default_value` (or `None` if not provided).

  ```python
  age = my_dict.get("age", "Not Found")
  print(age)  # Output: 30
  
  country = my_dict.get("country", "Not Found")
  print(country)  # Output: Not Found
  ```

- **`dict.update(other_dict)`**:  
  Updates the dictionary with key-value pairs from another dictionary.

  ```python
  new_info = {"city": "Los Angeles", "hobby": "painting"}
  my_dict.update(new_info)
  print(my_dict)
  # Output: {'name': 'Alice', 'age': 30, 'profession': 'Engineer', 'city': 'Los Angeles', 'hobby': 'painting'}
  ```

- **`dict.pop(key)`**:  
  Removes the specified key and returns the corresponding value.

  ```python
  age = my_dict.pop("age")
  print(age)  # Output: 30
  print(my_dict)  # Output: {'name': 'Alice', 'profession': 'Engineer', 'city': 'Los Angeles', 'hobby': 'painting'}
  ```

- **`dict.clear()`**:  
  Removes all the key-value pairs from the dictionary, leaving it empty.

  ```python
  my_dict.clear()
  print(my_dict)  # Output: {}
  ```
Here are the notes for **Files: Text Files, Reading and Writing Files, Format Operator** in Markdown format:

---

## **Files**

In Python, files are used to store data permanently. Python provides built-in methods for reading from and writing to files.

### **Types of Files**
1. **Text Files**:  
   Stores data in the form of human-readable characters (e.g., `.txt`, `.csv`, `.html`).
   
2. **Binary Files**:  
   Stores data in binary format (e.g., images, video files, executable files).

### **Opening Files**

Before reading or writing, you need to open the file using the `open()` function. The syntax for opening a file is:
```python
file = open(filename, mode)
```

- `filename`: The name of the file.
- `mode`: Defines the mode in which the file is opened. Common modes are:
  - `'r'`: Read (default mode).
  - `'w'`: Write (creates the file if it doesn't exist).
  - `'a'`: Append (adds content to the file without erasing existing data).
  - `'x'`: Exclusive creation (fails if the file already exists).
  - `'b'`: Binary mode (used with other modes for binary files).
  - `'t'`: Text mode (default).

```python
file = open('example.txt', 'r')  # Opens the file in read mode
```

---

### **Reading Files**

Once a file is opened in read mode, you can use different methods to read its contents.

- **`read()`**: Reads the entire file as a single string.
  ```python
  file = open('example.txt', 'r')
  content = file.read()
  print(content)
  file.close()  # Always close the file after reading
  ```

- **`readline()`**: Reads one line from the file at a time.
  ```python
  file = open('example.txt', 'r')
  line = file.readline()
  print(line)
  file.close()
  ```

- **`readlines()`**: Reads all lines and returns them as a list of strings.
  ```python
  file = open('example.txt', 'r')
  lines = file.readlines()
  print(lines)
  file.close()
  ```

---

### **Opening a File**
To work with files in Python, you use the `open()` function. The `open()` function takes two arguments: the filename and the mode.

#### **Modes**:
- `'r'` - Read mode (default). Opens the file for reading.
- `'w'` - Write mode. Opens the file for writing (creates a new file if it doesn’t exist or truncates the existing file).
- `'a'` - Append mode. Opens the file for writing, but appends to the file instead of overwriting.
- `'b'` - Binary mode (use with `'r'`, `'w'`, or `'a'` for binary files).
- `'x'` - Exclusive creation mode. Fails if the file already exists.

```python
file = open('example.txt', 'r')  # Open file in read mode
```

### **Writing to a File**
To write data to a file, open it in `'w'` (write) or `'a'` (append) mode. Always remember to close the file after writing.

- **`write()`**: Writes a string to the file.
  ```python
  file = open('example.txt', 'w')
  file.write('Hello, World!')
  file.close()
  ```

- **`writelines()`**: Writes a list of strings to the file.
  ```python
  file = open('example.txt', 'w')
  lines = ['Hello, World!\n', 'Welcome to Python.']
  file.writelines(lines)
  file.close()
  ```

### **Closing a File**
It is important to close a file after performing read/write operations. Closing a file ensures that any changes made to the file are saved, and it also frees up system resources.

```python
file.close()
```

### **The `format()` Operator**
The **`format()`** method in Python allows you to format strings by embedding variables or expressions inside them.

- **Basic usage**:
  ```python
  name = "Alice"
  age = 25
  sentence = "My name is {} and I am {} years old.".format(name, age)
  print(sentence)  # Output: My name is Alice and I am 25 years old.
  ```

- **Using numbered placeholders**:
  ```python
  sentence = "I have {0} apples and {1} oranges.".format(5, 10)
  print(sentence)  # Output: I have 5 apples and 10 oranges.
  ```

- **Named placeholders**:
  ```python
  sentence = "Hello, {name}. You are {age} years old.".format(name="Bob", age=30)
  print(sentence)  # Output: Hello, Bob. You are 30 years old.
  ```

The `format()` operator can be useful when writing formatted text to files.

Example:
```python
with open('example.txt', 'w') as file:
    name = "Charlie"
    age = 28
    file.write("My name is {} and I am {} years old.".format(name, age))
```

---
---
---

# UNIT 02 ENDS HERE ! 
# \>GO TO [UNIT 03](Python-03%20(FUNCTIONS).md)  
