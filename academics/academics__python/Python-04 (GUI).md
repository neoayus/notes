# **Graphical User Interfaces (GUI)**

A **Graphical User Interface (GUI)** allows users to interact with a computer or device using graphical icons, buttons, and other visual indicators, as opposed to typing text-based commands (CLI). GUIs are more intuitive and user-friendly, making them an essential part of modern software development.

---

### **GUI-Based Programs**

A **GUI-based program** is one that utilizes graphical elements (like buttons, windows, text boxes, etc.) to allow interaction with the user. These programs are event-driven, meaning they respond to user actions such as clicks, keystrokes, and mouse movements.

#### **Key Components of a GUI**:

- **Windows**: The primary container for all GUI elements.
- **Widgets**: The individual elements within a window, such as buttons, labels, and entry fields.
- **Event Handling**: The process by which a program responds to user inputs (events) like clicks or key presses.

In Python, libraries like `Tkinter`, `PyQt`, or `Kivy` are commonly used to create GUI applications.

---

### **Terminal-Based Version vs. GUI-Based Version**

1. **Terminal-Based Version**:
    
    - This version of the program relies on text-based interaction through a terminal or command line.
    - User inputs commands, and the program outputs text results.
    - Examples: Console-based applications like text editors (e.g., `vim`) or games (e.g., `Tetris`).
2. **GUI-Based Version**:
    
    - Instead of interacting through a command line, the user interacts with the program via graphical elements like buttons, sliders, and menus.
    - This version is often more user-friendly and visually appealing.
    - Examples: Desktop applications like web browsers (e.g., Chrome) or image editors (e.g., Photoshop).

---

### **Event-Driven Programming**

In **Event-Driven Programming**, the flow of the program is determined by events such as user actions or sensor outputs. The program waits for events to occur (like a button click), and when an event is triggered, the program executes a specific block of code known as an **event handler**.

#### **Example**:

```python
import tkinter as tk

def on_button_click():
    print("Button clicked!")

root = tk.Tk()  # Create a root window
button = tk.Button(root, text="Click Me", command=on_button_click)
button.pack()  # Add the button to the window

root.mainloop()  # Run the GUI loop
```

- The program waits for a button click event.
- When the button is clicked, the function `on_button_click()` is executed.

---

### **Windows and Labels**

- **Windows**: A GUI window is the primary container for displaying widgets. It can be created using libraries like `Tkinter`.
    
    **Example**:
    
    ```python
    import tkinter as tk
    root = tk.Tk()  # Creates a window
    root.title("My Window")  # Set window title
    root.geometry("300x200")  # Set window size (width x height)
    root.mainloop()  # Run the window's event loop
    ```
    
- **Labels**: Labels are used to display text or images in the window.
    
    **Example**:
    
    ```python
    label = tk.Label(root, text="Hello, GUI!")
    label.pack()  # Add the label to the window
    ```
    

---

### **Displaying Images**

Displaying images in a GUI involves using the appropriate widget to show the image in the window. In Tkinter, the `Label` widget can be used with an image object.

#### **Example**:

```python
from tkinter import Tk, Label
from PIL import Image, ImageTk

root = Tk()
img = Image.open("image.jpg")
img = img.resize((200, 200))  # Resize the image
photo = ImageTk.PhotoImage(img)  # Convert image to a format Tkinter can display

label = Label(root, image=photo)
label.pack()
root.mainloop()
```

-  image file `image.jpg` is opened and displayed in the Tkinter window using the `Label` widget.

---

### **Command Buttons and Responding to Events**

Command buttons are interactive GUI elements that allow users to perform actions. When a user clicks a button, an event is triggered, and a response is executed through an event handler.

#### **Example**:

```python
import tkinter as tk

def greet():
    print("Hello, welcome to the GUI!")

root = tk.Tk()
button = tk.Button(root, text="Greet", command=greet)
button.pack()
root.mainloop()
```

In this example, clicking the "Greet" button will call the `greet()` function and print a message.

---

### **Viewing the Images**

Viewing images in a GUI typically involves loading an image file and displaying it in a window. Libraries like `PIL` (Python Imaging Library) or `Pillow` are used to handle image files.

**Example** (in a GUI window using `Tkinter` and `Pillow`):

```python
from tkinter import Tk, Label
from PIL import Image, ImageTk

root = Tk()
image = Image.open("image.png")
photo = ImageTk.PhotoImage(image)

label = Label(root, image=photo)
label.pack()
root.mainloop()
```

---

### **Entry Fields for Input and Output of Text**

Entry fields allow users to input text in a GUI application. You can also use entry fields to display or modify text.

#### **Example**:

```python
import tkinter as tk

def show_input():
    user_input = entry.get()  # Get the text from the entry field
    print(f"User input: {user_input}")

root = tk.Tk()
entry = tk.Entry(root)
entry.pack()

button = tk.Button(root, text="Submit", command=show_input)
button.pack()

root.mainloop()
```

Here, an `Entry` widget is used to take user input, and when the button is clicked, the input text is retrieved and printed.

---

### **Using Pop-up Dialog Boxes and Other Useful GUI Resources**

- **Pop-up Dialog Boxes**: Dialog boxes are small windows used to display information, confirm actions, or take user input.

#### **Message Box Example**:

```python
import tkinter.messagebox

tkinter.messagebox.showinfo("Information", "This is a pop-up message box.")
```

- **File Dialog**: A file dialog box allows users to open or save files.

#### **File Dialog Example**:

```python
from tkinter import filedialog

filename = filedialog.askopenfilename(title="Select a file")
print(f"File selected: {filename}")
```

This will open a file dialog, allowing the user to choose a file, and print the file path.

---
---
---
# UNIT 04 ENDS HERE ! 
# \>GO TO [UNIT 05](Python-05%20(Multi-Threading).md)  
