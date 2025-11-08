# Applet Basics

An **applet** is a **small Java program** that can be **embedded into a web page** and executed inside a **web browser** or **Java Applet Viewer**.

Unlike standalone applications (which run using the Java interpreter from the command line), **applets run within a Java-enabled environment**, often controlled by a browser or a special viewer.

Applets are part of Java’s **Graphical User Interface (GUI)** technology and are mainly used to create **interactive web components** such as animations, charts, or small tools.

## **Characteristics of Applets**

1. **Runs in a browser or applet viewer** (not from the console).
2. **Does not have a `main()` method** — execution starts automatically with lifecycle methods.
3. **Platform-independent GUI program**, built using AWT or Swing components.
4. **Secure and sandboxed** — limited access to system resources for safety.
5. **Event-driven** — responds to user input like mouse clicks or keypresses.

## **The `Applet` Class**

All applets in Java inherit from the **`java.applet.Applet`** class (for AWT applets) or **`javax.swing.JApplet`** (for Swing applets).

**Package:**

* `java.applet.*` (for classic AWT-based applets)
* `java.awt.*` (for UI components)

**Class Declaration:**

```java
public class MyApplet extends Applet
```

## **Applet Lifecycle**

An applet goes through **five distinct phases**, managed automatically by the Java runtime environment.

Each phase is represented by a method that you can override in your applet class.

### **Applet Lifecycle Methods**

| Method              | Purpose                                                                                                                            |
| ------------------- | ---------------------------------------------------------------------------------------------------------------------------------- |
| `init()`            | Called once when the applet is first loaded. Used for initialization (like variable setup, UI creation).                           |
| `start()`           | Called each time the applet becomes active (e.g., when a user revisits the page). Usually used for starting animations or threads. |
| `paint(Graphics g)` | Called whenever the applet needs to redraw its output on the screen. All drawing operations happen here.                           |
| `stop()`            | Called when the applet is no longer visible or the user leaves the page. Used to pause threads or animations.                      |
| `destroy()`         | Called once when the applet is being completely removed from memory. Used for cleanup.                                             |

### **Lifecycle Diagram**

```
        +-----------+
        |  init()   |   --> called once at startup
        +-----------+
              |
              v
        +-----------+
        |  start()  |   --> called when applet starts or resumes
        +-----------+
              |
              v
        +-----------+
        |  paint()  |   --> called whenever GUI needs repainting
        +-----------+
              |
              v
        +-----------+
        |  stop()   |   --> called when applet is paused or hidden
        +-----------+
              |
              v
        +-----------+
        | destroy() |   --> called before applet is unloaded
        +-----------+
```

## **Example: Simple Applet Program**

```java
import java.applet.Applet;
import java.awt.Graphics;

/*
 <applet code="SimpleApplet.class" width="300" height="150">
 </applet>
*/

public class SimpleApplet extends Applet {
    public void init() {
        System.out.println("Applet initialized");
    }

    public void start() {
        System.out.println("Applet started");
    }

    public void paint(Graphics g) {
        g.drawString("Hello, Applet World!", 100, 80);
    }

    public void stop() {
        System.out.println("Applet stopped");
    }

    public void destroy() {
        System.out.println("Applet destroyed");
    }
}
```

### **Explanation**

* The `<applet>` tag (in a web page or comment block) specifies how to load and display the applet.
* `init()` runs first when the applet is loaded.
* `paint()` draws text or graphics on the applet window.
* `start()` and `stop()` handle active/inactive states.
* `destroy()` cleans up before termination.

## **Executing an Applet**

Applets can be run in **two ways:**

### **(a) Using an HTML file**

Create a file `SimpleApplet.html`:

```html
<html>
  <body>
    <applet code="SimpleApplet.class" width="300" height="150"></applet>
  </body>
</html>
```

Then open it in a Java-enabled browser.

### **(b) Using Applet Viewer**

Use the `appletviewer` command:

```bash
appletviewer SimpleApplet.java
```

The Applet Viewer reads the `<applet>` tag and launches the applet without needing a browser.

## **Drawing and Graphics in Applets**

The `paint(Graphics g)` method is used for all drawing operations.
It receives a `Graphics` object as an argument, which allows you to draw shapes, text, and images.

**Example:**

```java
public void paint(Graphics g) {
    g.drawString("Welcome to Java Applet", 50, 50);
    g.drawLine(20, 20, 200, 20);
    g.drawRect(50, 70, 100, 50);
    g.setColor(Color.blue);
    g.fillOval(100, 150, 50, 50);
}
```

## **Advantages of Applets**

1. **Platform Independent:** Runs on any machine with JVM.
2. **Secure:** Runs in a restricted environment (sandbox).
3. **Interactive GUI:** Can respond to user actions.
4. **Easy Distribution:** Downloaded automatically with a webpage.
5. **Lightweight:** Uses minimal system resources.

## **Limitations of Applets**

1. **Browser Dependency:** Requires Java plugin or Applet Viewer.
2. **Security Restrictions:** Cannot access local files or system resources.
3. **Obsolete Technology:** Modern browsers no longer support applets (replaced by JavaFX or web-based UIs).
4. **Limited Performance:** Slower than native applications for complex tasks.

## **Difference Between Application and Applet**

| Feature            | Java Application         | Java Applet                                        |
| ------------------ | ------------------------ | -------------------------------------------------- |
| **Entry Point**    | Has `main()` method      | Uses lifecycle methods (`init()`, `start()`, etc.) |
| **Execution**      | Run via JVM/command line | Runs inside a browser or viewer                    |
| **Security**       | Full system access       | Restricted (sandboxed)                             |
| **User Interface** | Console or window-based  | GUI embedded in webpage                            |
| **Communication**  | Can access local files   | Cannot access local files directly                 |

---

# Applet Architecture

The **architecture of an applet** defines how an applet is *created, loaded, executed,* and *managed* inside a browser or applet viewer.

It describes the **relationship between the browser (or applet viewer)**, the **Java Virtual Machine (JVM)**, and the **applet code** itself — explaining how the browser controls the applet’s lifecycle, manages resources, and communicates with the system.

## **Basic Idea**

When a browser encounters an `<applet>` tag inside an HTML page:

1. It **downloads the `.class` file** containing the applet’s bytecode.
2. The **JVM** embedded in the browser executes the applet.
3. The **Applet class** methods (`init()`, `start()`, `paint()`, etc.) are called in a specific order by the browser’s **Applet Engine**.
4. The applet runs within a **sandbox environment**, meaning it has **restricted access** to local resources for security.

## **Components of Applet Architecture**

An applet operates through interaction among the following components:

1. **Applet Class (User Code)**

   * The user-defined class extending `java.applet.Applet`.
   * Contains overridden lifecycle methods like `init()`, `start()`, and `paint()`.
   * Handles GUI logic and event responses.

2. **Applet Container (Browser/Applet Viewer)**

   * The environment in which the applet runs.
   * Provides the display area for the applet.
   * Invokes the lifecycle methods automatically.
   * Manages loading, initialization, and destruction.

3. **Java Plug-in / JVM**

   * Executes the bytecode of the applet.
   * Handles memory allocation, security checks, and thread management.

4. **Applet Context**

   * An interface provided by the container to the applet.
   * Allows an applet to communicate with its environment (e.g., loading images, playing sounds, or finding other applets on the same page).
   * Retrieved using `getAppletContext()`.

5. **Security Manager (Sandbox)**

   * Prevents unauthorized actions such as file system access, local data manipulation, or network communication to external hosts.
   * Ensures that downloaded applets cannot harm the client system.

6. **Graphics Context**

   * Manages all the drawing done by the applet in its display area.
   * The `paint(Graphics g)` method interacts with this context to render visuals.

## **Applet Architecture Diagram (Text Representation)**

```
                 +--------------------------------------+
                 |           Web Browser /              |
                 |         Applet Viewer                |
                 +--------------------------------------+
                       |        |        |       |
                       v        v        v       v
          +----------------+  +----------------+  +----------------+
          | Applet Context |  | Security Mgmt  |  | Event Handling |
          +----------------+  +----------------+  +----------------+
                       |
                       v
               +------------------+
               |  Applet Class    |
               | (User-Defined)   |
               +------------------+
                       |
                       v
               +------------------+
               |  Graphics Area   |
               | (paint method)   |
               +------------------+
```

## **Applet Lifecycle in Architecture**

1. **Loading Phase**

   * The browser detects the `<applet>` tag in the HTML file.
   * The `.class` file of the applet is downloaded to the client.
   * The JVM loads the applet into memory and creates an instance of it.

2. **Initialization Phase**

   * The browser calls the applet’s `init()` method once.
   * Used for one-time setup such as UI creation, variable initialization, or reading parameters via `getParameter()`.

3. **Starting Phase**

   * The browser calls the `start()` method.
   * Executed every time the applet becomes active (like when the user revisits the page).
   * Used for starting animations, timers, or threads.

4. **Running / Painting Phase**

   * The applet draws on the screen through the `paint(Graphics g)` method.
   * The browser invokes `paint()` whenever the applet needs to refresh its display.
   * Event handling (mouse, keyboard, etc.) also occurs here.

5. **Stopping Phase**

   * Called when the applet is no longer visible or user switches pages.
   * The `stop()` method is executed to suspend animations or threads.

6. **Destruction Phase**

   * When the applet is about to be unloaded, the `destroy()` method is called once.
   * Used for releasing resources or closing network connections.

## **Communication within the Architecture**

* **Browser ↔ JVM:**
  The browser delegates execution to the JVM when an applet is found.
* **JVM ↔ Applet Class:**
  The JVM controls the applet’s lifecycle by calling its lifecycle methods.
* **Applet ↔ Applet Context:**
  The applet communicates with its container to load media, navigate pages, or locate other applets.

**Example:**

```java
AppletContext context = getAppletContext();
context.showDocument(new URL("https://www.example.com"));
```

This loads a new webpage from inside the applet.

## **Security Model (Sandboxing)**

Applets run under strict security restrictions called the **sandbox model**.
This prevents them from performing potentially harmful actions on the user’s system.

### **Restrictions**

* Cannot read/write local files.
* Cannot execute local programs.
* Cannot connect to servers other than the one they were downloaded from.
* Cannot access system properties or devices.

This model ensures the applet remains safe and controlled.

## **Example: Basic Flow**

```java
import java.applet.*;
import java.awt.*;

/*
<applet code="DemoApplet.class" width="300" height="150">
</applet>
*/
public class DemoApplet extends Applet {
    public void init() {
        setBackground(Color.cyan);
    }
    public void start() {
        System.out.println("Applet started");
    }
    public void paint(Graphics g) {
        g.drawString("Applet Architecture Demo", 50, 80);
    }
    public void stop() {
        System.out.println("Applet stopped");
    }
    public void destroy() {
        System.out.println("Applet destroyed");
    }
}
```

### **How it works:**

* Browser loads `DemoApplet.class` → JVM executes it.
* Browser calls `init()` → sets background.
* Calls `start()` → applet becomes active.
* Invokes `paint()` → displays string on screen.
* When the user leaves the page, `stop()` → `destroy()` are called.

## **Advantages of Applet Architecture**

1. **Automatic Lifecycle Management** — The browser handles all method calls automatically.
2. **Security** — Sandbox model prevents system-level abuse.
3. **GUI Integration** — Applets can easily embed rich, interactive visuals inside web pages.
4. **Platform Independence** — Runs on any system with JVM support.
5. **Event Handling** — Supports AWT and Swing for responsive user interfaces.

## **Limitations**

1. **Browser Support:** Most modern browsers no longer support applets.
2. **Security Restrictions:** Prevents many useful local operations.
3. **Performance:** Slower than standalone applications.
4. **Requires JVM Plug-in:** Not all users have it installed.

---

# Lifecycle of Java Applets

When an applet is embedded inside an HTML page, the **browser loads the applet’s bytecode**, creates an instance of the applet class, and then sequentially calls the lifecycle methods defined by the Java API. These methods provide hooks for initialization, execution, suspension, and cleanup activities.

An applet’s lifecycle ensures proper **resource allocation, execution flow, and destruction** within the controlled environment of the browser.

### **The Five Core Lifecycle Methods**

The applet’s lifecycle is governed by **five key methods**, which the browser calls in a fixed order:

#### **(a) `init()`**

* Called **once** when the applet is first loaded.
* Used for **one-time initialization**, such as:

  * Setting up the user interface.
  * Allocating resources (fonts, colors, images).
  * Reading parameters using `getParameter()`.
* Comparable to a constructor, but specifically meant for applets.

**Example:**

```java
public void init() {
    setBackground(Color.lightGray);
    msg = getParameter("welcomeMsg");
}
```

#### **(b) `start()`**

* Invoked **after `init()`** and **every time** the applet becomes active (for example, when the user revisits the page).
* Ideal for starting **threads, animations, or processes** that need to run while the applet is visible.
* May be called multiple times during an applet’s life.

**Example:**

```java
public void start() {
    animationFlag = true;
    animationThread = new Thread(this);
    animationThread.start();
}
```

#### **(c) `paint(Graphics g)`**

* Called **automatically** after `start()` whenever the applet’s window needs to be redrawn (e.g., minimized and restored).
* Handles **all visual rendering** and UI drawing.
* Uses the **`Graphics` object** provided by the AWT framework.

**Example:**

```java
public void paint(Graphics g) {
    g.drawString("Applet Lifecycle Demo", 60, 80);
}
```

#### **(d) `stop()`**

* Invoked when the user **leaves the page** or **minimizes the browser** window containing the applet.
* Used to **pause execution** (e.g., suspend animations or threads).
* Unlike `destroy()`, it does not free resources permanently; it only suspends activity.

**Example:**

```java
public void stop() {
    animationFlag = false;
}
```

#### **(e) `destroy()`**

* Called **once** when the applet is **completely unloaded** from memory (e.g., when the browser closes or the user navigates away permanently).
* Used for **cleanup** — releasing memory, closing files, or terminating connections.

**Example:**

```java
public void destroy() {
    animationThread = null;
}
```

### **Sequence of Lifecycle Events**

The lifecycle follows this **strict sequence**:

```
          +-------+       +--------+       +--------+
          | init()| --->  | start()| --->  | paint()|
          +-------+       +--------+       +--------+
                                           | Running |
                                           +----------+
                                                  |
                                                  v
                                            +-------------+
                                            | stop()      |
                                            +-------------+
                                                  |
                                                  v
                                            +-------------+
                                            | destroy()   |
                                            +-------------+
```

**Explanation of flow:**

* **init()** → runs once when applet loads.
* **start()** → runs when applet becomes active.
* **paint()** → draws output on the screen.
* **stop()** → suspends applet when not visible.
* **destroy()** → cleans up before termination.

### **Example Demonstrating Lifecycle Methods**

```java
import java.applet.*;
import java.awt.*;

/*
<applet code="LifeCycleDemo.class" width=300 height=150>
</applet>
*/

public class LifeCycleDemo extends Applet {
    String msg;

    public void init() {
        msg = "Applet Initialized.";
    }

    public void start() {
        msg += " Applet Started.";
    }

    public void paint(Graphics g) {
        g.drawString(msg, 50, 80);
    }

    public void stop() {
        msg = "Applet Stopped.";
        System.out.println(msg);
    }

    public void destroy() {
        System.out.println("Applet Destroyed.");
    }
}
```

**Output behavior:**

* When the page loads → “Applet Initialized. Applet Started.” appears.
* When you switch tabs → `stop()` executes.
* When you close the page → `destroy()` executes.

### **Practical Notes for Exams**

* The **browser or applet viewer** controls when each method is called; the programmer **cannot** call them manually.
* The **`init()`** and **`destroy()`** methods run **exactly once**, while **`start()`** and **`stop()`** may execute multiple times.
* **`paint()`** is called automatically whenever the applet’s display area must be refreshed.
* Together, these five methods ensure controlled initialization, execution, suspension, and termination.

--- 
# Creation of Applet

The process of creating an applet involves **four key stages**:

### **Step 1: Import Required Packages**

To work with applets, you must import:

```java
import java.applet.*;
import java.awt.*;
```

- `java.applet.*` → Provides the `Applet` class and related interfaces.
   
- `java.awt.*` → Used for graphical rendering and GUI components.
   
### **Step 2: Define a Class Extending Applet**

You must define a class that extends the predefined `Applet` class.  
This makes your class inherit the applet’s default behavior.

**Example:**

```java
public class MyApplet extends Applet {
    // lifecycle methods go here
}
```

This class becomes the _core_ of your applet.

### **Step 3: Override Lifecycle Methods**

An applet’s behavior is controlled through five main lifecycle methods (`init()`, `start()`, `paint()`, `stop()`, and `destroy()`), but for creation and display, you at least need to define **`paint()`**.

**Example:**

```java
public void paint(Graphics g) {
    g.drawString("Hello, Applet World!", 20, 30);
}
```

- The `Graphics` object `g` is automatically passed to `paint()` by the AWT subsystem.
   
- The `drawString()` method displays text on the applet window.
   
### **Step 4: Compile the Applet**

Save the file with a `.java` extension (e.g., `MyApplet.java`) and compile it using the Java compiler:

```bash
javac MyApplet.java
```

This produces a bytecode file:

```
MyApplet.class
```

### **Step 5: Create an HTML File to Run the Applet**

Since applets are designed to run inside browsers, we use an HTML file to load and display them.

**Example HTML File:**

```html
<html>
  <body>
    <applet code="MyApplet.class" width="300" height="150">
    </applet>
  </body>
</html>
```

**Explanation:**

- `code` → specifies the name of the compiled `.class` file.
- `width` and `height` → define the display area for the applet.
   

> **Note:** The `<applet>` tag is deprecated in modern browsers but remains important for academic and theoretical understanding.

### **Step 6: Run the Applet**

You can run the applet using the **Applet Viewer** tool that comes with the JDK:

```bash
appletviewer MyApplet.html
```

This opens a small window and executes the applet code exactly as a browser would.

---

## **3. Complete Example: Basic Applet Creation**

```java
import java.applet.*;
import java.awt.*;

/*
<applet code="WelcomeApplet.class" width="300" height="150">
</applet>
*/

public class WelcomeApplet extends Applet {

    public void init() {
        setBackground(Color.yellow);
    }

    public void paint(Graphics g) {
        g.setColor(Color.red);
        g.drawString("Welcome to Java Applets!", 50, 80);
    }
}
```

**Explanation of the Example:**

1. The class `WelcomeApplet` extends `Applet`.
2. `init()` initializes the background color once.
3. `paint()` draws a message inside the applet window.
4. The `<applet>` tag embedded in the comment lets the applet viewer know how to load it.

## **4. Compilation and Execution Flow**

1. Write and save the Java source file → `WelcomeApplet.java`
2. Compile it → `javac WelcomeApplet.java`
3. Create HTML → `WelcomeApplet.html`
4. Run using → `appletviewer WelcomeApplet.html`

When executed:

- The **browser or viewer** loads the applet.
- The **JVM** creates an instance of it.
- The **`init()`** method executes first, followed by **`paint()`** for visual rendering.
   

## **Key Points to Remember**

- Every applet class **must inherit** from `Applet` (or `JApplet` for Swing).
   
- The `paint()` method is **essential** for displaying output.
   
- Applets **cannot** have a `main()` method.
   
- The applet runs inside a **restricted environment** (sandbox).
   
- Execution always happens within a **browser or applet viewer**, not the command line.
   
- To pass input from HTML to the applet, we use the `<param>` tag and `getParameter()` method (discussed in the next topic).
   
--- 
# Parameter Passing to Applets

In Java applets, the HTML file that loads the applet can **send input values** to it using **parameters**.
This process is called **parameter passing** — it allows us to make applets **dynamic and customizable** without changing or recompiling their code.

For example, you could pass a *welcome message, username, color, or speed value* from the web page directly into the applet at runtime.

The mechanism uses:

* The `<param>` tag (inside the `<applet>` tag in HTML), and
* The `getParameter(String paramName)` method (inside the applet).

## **Purpose of Parameter Passing**

Parameter passing lets applets:

1. **Adapt behavior** according to HTML data.
2. **Avoid hardcoding values** in Java code.
3. **Personalize output** (e.g., greetings, color themes).
4. **Simplify updates**, since you only modify the HTML, not the Java file.

Example scenario:
You can write one applet that displays a message — and decide *what message to show* from the HTML page, not inside Java code.

## **The `<param>` Tag**

The `<param>` tag in HTML provides **key-value pairs** to send information into the applet.
It is written **inside** the `<applet>` tag and has the following syntax:

```html
<param name="parameterName" value="parameterValue">
```

* **`name`** → specifies the name (or key) of the parameter.
* **`value`** → specifies the value that will be sent to the applet.

### **Example:**

```html
<applet code="GreetingApplet.class" width="300" height="150">
  <param name="username" value="Sushh">
  <param name="color" value="blue">
</applet>
```

Here, two parameters are passed to the applet:

* `username = "Sushh"`
* `color = "blue"`

## **Retrieving Parameters inside the Applet**

To access these parameters in Java, we use the method:

```java
String getParameter(String parameterName)
```

* Returns the **value of the parameter** as a `String`.
* Returns `null` if the parameter name doesn’t exist in the HTML.

This method is defined in the `Applet` class and is usually called inside the **`init()`** method, since initialization happens right after the applet loads.

### **Example Code:**

```java
import java.applet.*;
import java.awt.*;

/*
<applet code="GreetingApplet.class" width="300" height="150">
  <param name="username" value="Sushh">
  <param name="color" value="red">
</applet>
*/

public class GreetingApplet extends Applet {
    String name;
    Color c;

    public void init() {
        // Retrieving parameters from HTML
        name = getParameter("username");
        String colorParam = getParameter("color");

        // Converting color name to actual Color object
        if (colorParam.equalsIgnoreCase("red"))
            c = Color.red;
        else if (colorParam.equalsIgnoreCase("blue"))
            c = Color.blue;
        else
            c = Color.black;

        setBackground(c);
    }

    public void paint(Graphics g) {
        g.setColor(Color.white);
        g.drawString("Welcome, " + name + "!", 50, 80);
    }
}
```

### **Explanation of Example:**

1. The `<param>` tags in the HTML define two parameters:

   * `username` → passed as `"Sushh"`
   * `color` → passed as `"red"`

2. The applet retrieves them using `getParameter()`.

3. Depending on the color value, it sets the background.

4. Finally, it displays the personalized message:

   ```
   Welcome, Sushh!
   ```

## **Key Rules for Parameter Passing**

1. **Parameters are always Strings.**

   * You must manually convert them to numeric or logical types (e.g., using `Integer.parseInt()` for numbers).

2. **Case-sensitive names:**

   * Both the parameter name in HTML and the argument passed to `getParameter()` must match exactly.

3. **`getParameter()` returns null** if the parameter isn’t defined in the HTML, so null checks are important.

4. **Used mostly in `init()`** because it runs once, right after the applet loads and before display rendering.

5. **HTML and Java must stay synchronized** — if you change a parameter name in one, update the other.

## **Example: Passing Numeric Values**

```java
import java.applet.*;
import java.awt.*;

/*
<applet code="CircleApplet.class" width="300" height="200">
  <param name="radius" value="50">
</applet>
*/

public class CircleApplet extends Applet {
    int r;

    public void init() {
        String radiusStr = getParameter("radius");
        r = Integer.parseInt(radiusStr);
    }

    public void paint(Graphics g) {
        g.drawOval(100, 50, 2 * r, 2 * r);
    }
}
```

**Explanation:**

* The `<param>` tag sends the radius value as `"50"`.
* The applet retrieves it as a String, converts it to `int`, and draws a circle of radius 50 pixels.

## **Advantages of Parameter Passing**

1. **Reusability:** The same applet can behave differently for different HTML parameter values.
2. **Flexibility:** No need to recompile code for small changes.
3. **Dynamic Execution:** Inputs can be customized based on user or environment.
4. **Separation of Code and Configuration:** Values are managed externally through HTML.

## **Common Errors & Solutions**

| Error                    | Cause                            | Solution                                         |
| ------------------------ | -------------------------------- | ------------------------------------------------ |
| `NullPointerException`   | Parameter name misspelled        | Check spelling in `<param>` and `getParameter()` |
| Wrong color/text display | Parameter case mismatch          | Use `equalsIgnoreCase()`                         |
| NumberFormatException    | Parameter value not numeric      | Validate before converting                       |
| Parameter not received   | `<param>` tag outside `<applet>` | Keep `<param>` inside `<applet>` block           |

--- 
# Applet Graphics 

In Java applets, **graphics** are created using the **`Graphics` class** (from the `java.awt` package).
Every applet has a built-in **drawing surface**, and you can use that to draw **shapes, text, or images**.

All drawing operations are done inside the **`paint(Graphics g)`** method — which is automatically called by the JVM when:

* The applet window is first displayed,
* The window is resized or uncovered, or
* You explicitly call `repaint()`.

## **The `Graphics` Class**

`Graphics` is an **abstract class** that provides methods to draw and fill shapes, set colors, and write text.
It acts like a **pen** that you use to draw on the applet screen.

### **Commonly Used Graphics Methods**

| **Method**                                                                        | **Description**                               |
| --------------------------------------------------------------------------------- | --------------------------------------------- |
| `void drawLine(int x1, int y1, int x2, int y2)`                                   | Draws a line between two points.              |
| `void drawRect(int x, int y, int width, int height)`                              | Draws an outline of a rectangle.              |
| `void fillRect(int x, int y, int width, int height)`                              | Draws a filled rectangle.                     |
| `void drawOval(int x, int y, int width, int height)`                              | Draws an oval inside the specified rectangle. |
| `void fillOval(int x, int y, int width, int height)`                              | Draws a filled oval.                          |
| `void drawArc(int x, int y, int width, int height, int startAngle, int arcAngle)` | Draws an arc (portion of an oval).            |
| `void fillArc(int x, int y, int width, int height, int startAngle, int arcAngle)` | Fills the area of the arc.                    |
| `void drawPolygon(int[] xPoints, int[] yPoints, int nPoints)`                     | Draws a polygon with the given coordinates.   |
| `void fillPolygon(int[] xPoints, int[] yPoints, int nPoints)`                     | Draws a filled polygon.                       |
| `void drawString(String str, int x, int y)`                                       | Displays a text string.                       |
| `void setColor(Color c)`                                                          | Sets the current drawing color.               |
## **Coordinate System**

Applet coordinates start from the **top-left corner (0,0)** of the window.

* The **x-axis** increases **to the right**.
* The **y-axis** increases **downwards**.

So `(0, 0)` → top-left corner,
and `(width, height)` → bottom-right corner.

## **Setting Colors**

Before drawing, you can set a drawing color using:

```java
g.setColor(Color.red);
```

Common colors from the `Color` class:

* `Color.red`, `Color.blue`, `Color.green`, `Color.yellow`,
* `Color.black`, `Color.white`, `Color.orange`, `Color.pink`, etc.

You can also create custom colors:

```java
Color myColor = new Color(120, 180, 240); // RGB
g.setColor(myColor);
```

## **Example 1 – Drawing Basic Shapes**

```java
import java.applet.*;
import java.awt.*;

/*
<applet code="BasicShapes.class" width="400" height="300"></applet>
*/

public class BasicShapes extends Applet {
    public void paint(Graphics g) {
        // Set color for the line
        g.setColor(Color.red);
        g.drawLine(20, 20, 120, 20);

        // Draw rectangle
        g.setColor(Color.blue);
        g.drawRect(20, 40, 100, 50);

        // Filled rectangle
        g.setColor(Color.green);
        g.fillRect(140, 40, 100, 50);

        // Draw oval
        g.setColor(Color.orange);
        g.drawOval(20, 110, 100, 50);

        // Filled oval
        g.setColor(Color.pink);
        g.fillOval(140, 110, 100, 50);

        // Draw arc
        g.setColor(Color.magenta);
        g.drawArc(20, 180, 100, 100, 0, 180);

        // Filled arc
        g.setColor(Color.cyan);
        g.fillArc(140, 180, 100, 100, 0, 180);
    }
}
```

### **Explanation:**

* `drawLine()` draws a simple line.
* `drawRect()` and `fillRect()` create outlined and filled rectangles.
* `drawOval()` and `fillOval()` create outlined and filled ovals.
* `drawArc()` draws a half-circle using angles in degrees.

## **example 2 – drawing a polygon**

```java
import java.applet.*;
import java.awt.*;

/*
<applet code="PolygonExample.class" width="400" height="300"></applet>
*/

public class PolygonExample extends Applet {
    public void paint(Graphics g) {
        int xPoints[] = {50, 100, 150, 100, 50};
        int yPoints[] = {150, 100, 150, 200, 200};
        int n = 5;

        g.setColor(Color.blue);
        g.drawPolygon(xPoints, yPoints, n);

        g.setColor(Color.lightGray);
        g.fillPolygon(xPoints, yPoints, n);
    }
}
```

### **Explanation:**

* Polygon is drawn by connecting the points in the arrays `xPoints` and `yPoints`.
* The last point automatically connects back to the first.
* `n` defines how many points are in the polygon.

## **Example 3 – Mixing Text and Graphics**

```java
import java.applet.*;
import java.awt.*;

/*
<applet code="TextGraphics.class" width="400" height="200"></applet>
*/

public class TextGraphics extends Applet {
    public void paint(Graphics g) {
        g.setColor(Color.black);
        g.drawString("Java Applet Graphics Example", 50, 50);

        g.setColor(Color.red);
        g.drawLine(50, 60, 300, 60);

        g.setColor(Color.blue);
        g.drawRect(50, 80, 150, 80);

        g.setColor(Color.green);
        g.fillOval(250, 90, 80, 60);
    }
}
```

## **Using `repaint()`**

If you need to redraw the applet dynamically (for animations, user actions, etc.), call:

```java
repaint();
```

This triggers `update()` → which internally calls `paint(Graphics g)` again.

## **Important Notes**

1. The **origin (0,0)** is always the top-left corner.
2. All coordinates and dimensions are in **pixels**.
3. Always perform drawing inside **`paint(Graphics g)`**, not `init()`.
4. The background color can be changed using `setBackground(Color c)`.
5. For complex shapes, **polygons** and **arcs** are used.


--- 

# Applet Class

The **`Applet` class** is the **core class** in Java that allows a program to run inside a web browser or an applet viewer.  
It provides the **foundation for all applet programs**, handling the basic structure, environment, and event management necessary for displaying and controlling graphical user interfaces in a browser window.

This class is part of the **`java.applet`** package and serves as the **superclass** for all applets.

In short:

> Every applet you create is a subclass of `java.applet.Applet`.

## **Package and Hierarchy**

The `Applet` class belongs to the package:

```java
package java.applet;
```

### **Class Hierarchy**

```
java.lang.Object
    ↳ java.awt.Component
        ↳ java.awt.Container
            ↳ java.awt.Panel
                ↳ java.applet.Applet
```

This shows that an applet **inherits GUI capabilities** from `Component`, `Container`, and `Panel`.  
That means it can display graphical components (buttons, text fields, etc.) and respond to user actions.

## **Purpose of the Applet Class**

The `Applet` class provides methods to:

- Control the **life cycle** of an applet (initialize, start, stop, destroy).
   
- Handle **user interaction and events**.
   
- Access the **browser environment**, such as the document base or code base.
   
- Play sounds and display images within the applet’s window.
   
- Draw graphics using the `Graphics` object.
   
## **4. Important Methods of the Applet Class**

### **Lifecycle Methods (inherited from Applet class)**

These methods define the **lifecycle** of an applet and are automatically invoked by the browser or applet viewer.

| **Method**                      | **Description**                                                                     |
| ------------------------------- | ----------------------------------------------------------------------------------- |
| `public void init()`            | Called once when the applet is first loaded. Used for initialization tasks.         |
| `public void start()`           | Called each time the applet becomes active (e.g., when the user revisits the page). |
| `public void stop()`            | Called when the applet is stopped or the user moves away from the page.             |
| `public void destroy()`         | Called when the applet is being permanently removed from memory.                    |
| `public void paint(Graphics g)` | Used for drawing graphics, text, or shapes on the applet window.                    |

### **Utility Methods (specific to Applet)**

| **Method**                               | **Description**                                             |
| ---------------------------------------- | ----------------------------------------------------------- |
| `public String getAppletInfo()`          | Returns a short description about the applet.               |
| `public String[][] getParameterInfo()`   | Returns info about parameters accepted by the applet.       |
| `public AudioClip getAudioClip(URL url)` | Loads an audio clip from a specified URL.                   |
| `public Image getImage(URL url)`         | Loads an image from a specified URL.                        |
| `public URL getDocumentBase()`           | Returns the URL of the HTML document containing the applet. |
| `public URL getCodeBase()`               | Returns the URL from where the applet’s code was loaded.    |
| `public void showStatus(String msg)`     | Displays a message in the browser’s status bar.             |

## **Example: Simple Applet using Applet Class**

```java
import java.applet.*;
import java.awt.*;

/*
<applet code="MyApplet.class" width="400" height="200"></applet>
*/

public class MyApplet extends Applet {
    String msg;

    public void init() {
        msg = "Applet Initialized!";
    }

    public void start() {
        msg = "Applet Started!";
    }

    public void stop() {
        msg = "Applet Stopped!";
    }

    public void destroy() {
        msg = "Applet Destroyed!";
    }

    public void paint(Graphics g) {
        g.drawString(msg, 50, 100);
    }
}
```

### **Explanation:**

- The class `MyApplet` extends `Applet`.
   
- Lifecycle methods (`init`, `start`, `stop`, `destroy`) are overridden.
   
- The `paint()` method displays the current message on the applet window.
   
- `<applet>` tag specifies how the applet is embedded in HTML.

## **Accessing HTML Parameters through Applet**

You can pass parameters to the applet using the `<param>` tag in HTML, and retrieve them in Java using:

```java
getParameter(String name)
```

Example:

```java
String user = getParameter("username");
```

## **Example: Displaying Document and Code Base**

```java
import java.applet.*;
import java.awt.*;
import java.net.*;

/*
<applet code="BaseExample.class" width="400" height="150"></applet>
*/

public class BaseExample extends Applet {
    public void paint(Graphics g) {
        g.drawString("Document Base: " + getDocumentBase(), 20, 40);
        g.drawString("Code Base: " + getCodeBase(), 20, 70);
    }
}
```

### **Explanation:**

- `getDocumentBase()` returns the URL of the HTML file.
   
- `getCodeBase()` returns the directory where the applet’s `.class` file was loaded from.
   
## **Example: Playing a Sound and Displaying a Status Message**

```java
import java.applet.*;
import java.awt.*;
import java.net.*;

/*
<applet code="SoundApplet.class" width="300" height="150"></applet>
*/

public class SoundApplet extends Applet {
    AudioClip clip;

    public void init() {
        clip = getAudioClip(getDocumentBase(), "sound.wav");
    }

    public void start() {
        clip.play();
        showStatus("Playing sound...");
    }

    public void stop() {
        clip.stop();
        showStatus("Sound stopped.");
    }
}
```

## **Characteristics of the Applet Class**

1. **Subclass of Panel** – inherits layout and GUI features.
2. **Runs under control of a browser or viewer** – no `main()` method.
3. **Portable and secure** – runs in a sandbox environment.
4. **Graphical interface ready** – can use AWT components directly.
5. **Interactive** – can handle user inputs and events easily.
6. **Event-driven** – responds to user actions like mouse clicks or key presses.
   
## **Limitations of Applet**

- Cannot directly access local files or system resources.
- Depends on browser support (modern browsers no longer support Java applets).
- Requires JVM plug-ins for execution.
   
Still, understanding the `Applet` class is important for **legacy Java GUI concepts** and **event-driven programming foundations**.

--- 
# AWT Components and Container**

**AWT (Abstract Window Toolkit)** is Java’s **original platform-dependent GUI framework**.  
It provides **graphical user interface components**, **containers**, **layouts**, and **event-handling mechanisms** to build window-based applications.

AWT is a part of the `java.awt` package and works closely with the operating system’s native windowing system.  
Hence, it is called **“heavyweight”**, meaning its components rely on native (platform-specific) peers for rendering.

> AWT forms the foundation of all Java GUI frameworks, including Swing and JavaFX.

## **AWT Hierarchy Overview**

The **top-level hierarchy** of AWT GUI classes is as follows:

```
java.lang.Object
    ↳ java.awt.Component
         ↳ java.awt.Container
              ↳ java.awt.Panel
                   ↳ java.applet.Applet
              ↳ java.awt.Window
                   ↳ java.awt.Frame
                        ↳ java.awt.Dialog
```

This shows how every visual element in AWT starts from the **Component** class, and larger building blocks (like windows or panels) are **Containers** that can hold other components.

## **Component Class**

The **`Component`** class is the **base class** for all AWT visual elements.  
It represents **any object that can be displayed on the screen and interact with the user** — such as buttons, text fields, labels, etc.

### **Package:**

```java
java.awt.Component
```

### **Key Responsibilities of Component:**

- Defines **position and size** (via `setBounds()`).
- Handles **painting** and **event-handling**.
- Provides **methods for enabling/disabling, showing/hiding**, etc.
- Acts as the **root class** for all GUI components in AWT.
   

### **Commonly Used Methods of Component Class**

| **Method**                                            | **Description**                           |
| ----------------------------------------------------- | ----------------------------------------- |
| `void setSize(int width, int height)`                 | Sets the size of the component.           |
| `void setLocation(int x, int y)`                      | Sets the component’s position.            |
| `void setBounds(int x, int y, int width, int height)` | Sets both position and size.              |
| `void setVisible(boolean b)`                          | Shows or hides the component.             |
| `boolean isVisible()`                                 | Returns whether the component is visible. |
| `void setEnabled(boolean b)`                          | Enables or disables user interaction.     |
| `boolean isEnabled()`                                 | Checks if the component is enabled.       |
| `void setBackground(Color c)`                         | Sets the background color.                |
| `void setForeground(Color c)`                         | Sets the text or drawing color.           |
| `Font getFont()` / `void setFont(Font f)`             | Gets or sets font for display.            |
| `void repaint()`                                      | Requests the component to redraw itself.  |
## **Container Class**

The **`Container`** class is a subclass of `Component`.  
It acts as a **special component that can hold and organize other components**.  
In other words, containers are components that can **contain** other components — like buttons, text fields, or even other containers.

### **Hierarchy:**

```
java.awt.Component → java.awt.Container
```

Every **window, panel, frame, or applet** is essentially a container.

### **Responsibilities of Container:**

1. **Holds child components**.
2. **Manages layout** of its components via Layout Managers.
3. Provides **methods to add or remove components** dynamically.
4. Acts as the **parent** for all GUI components in a window.
   
### **Commonly Used Methods of Container Class**

| **Method**                                  | **Description**                                  |
| ------------------------------------------- | ------------------------------------------------ |
| `void add(Component c)`                     | Adds a component to the container.               |
| `void add(Component c, Object constraints)` | Adds a component using layout constraints.       |
| `void remove(Component c)`                  | Removes a component from the container.          |
| `void removeAll()`                          | Removes all components from the container.       |
| `int getComponentCount()`                   | Returns number of components in the container.   |
| `Component[] getComponents()`               | Returns an array of components in the container. |
| `LayoutManager getLayout()`                 | Returns the current layout manager.              |
| `void setLayout(LayoutManager mgr)`         | Sets a layout manager for the container.         |
## **Types of AWT Containers**

There are **two main categories** of containers:

### **1. Top-Level Containers**

These are containers that **exist independently** (not inside another container).

| **Class** | **Description**                                            |
| --------- | ---------------------------------------------------------- |
| `Frame`   | The main top-level window with a title bar, menu bar, etc. |
| `Dialog`  | A pop-up window for user interaction, usually modal.       |
| `Window`  | A generic top-level window without borders or title.       |

### **2. Intermediate Containers**

These are **used within other containers** to group or organize components.

| **Class**    | **Description**                                            |
| ------------ | ---------------------------------------------------------- |
| `Panel`      | A simple container used for grouping components.           |
| `Applet`     | A panel designed to run inside a browser or applet viewer. |
| `ScrollPane` | Provides scrolling support for components.                 |
| `Canvas`     | Used for custom drawing or rendering graphics.             |

## **Example: Creating a Simple AWT Container**

```java
import java.awt.*;

public class ContainerExample {
    public static void main(String[] args) {
        Frame f = new Frame("AWT Container Example");

        // Create components
        Label lbl = new Label("Enter Name:");
        TextField tf = new TextField(20);
        Button btn = new Button("Submit");

        // Add components to frame
        f.add(lbl);
        f.add(tf);
        f.add(btn);

        // Set layout
        f.setLayout(new FlowLayout());

        // Set frame properties
        f.setSize(300, 150);
        f.setVisible(true);
    }
}
```

### **Explanation:**

- A `Frame` is a **top-level container**.
- Components like `Label`, `TextField`, and `Button` are **added** to it.
- `FlowLayout` manages their arrangement.
- `setVisible(true)` displays the frame window.
   
## **Relationship Between Component and Container**

| **Aspect**                        | **Component**                       | **Container**                          |
| --------------------------------- | ----------------------------------- | -------------------------------------- |
| **Purpose**                       | Basic visual element.               | Holds and manages multiple components. |
| **Inheritance**                   | Base class for all UI elements.     | Subclass of `Component`.               |
| **Examples**                      | Button, Label, TextField, Checkbox. | Frame, Panel, Applet, Dialog.          |
| **Can Contain Other Components?** | No                                  | Yes                                    |
| **Methods**                       | `setSize()`, `setVisible()`, etc.   | `add()`, `setLayout()`, etc.           |
## **Important Notes**

1. **Every container is also a component**, but not every component is a container.
2. Components must be **added to a container** before they are displayed.
3. Containers rely on **layout managers** (like FlowLayout, BorderLayout, GridLayout) to position components.
4. GUI rendering is **platform-dependent** in AWT.
5. **Event-handling** is often attached directly to components (like `Button`, `TextField`, etc.) inside containers.
   

## **Diagrammatic View (Conceptual)**

```
Frame (Container)
 ├── Label (Component)
 ├── TextField (Component)
 └── Button (Component)
```

The `Frame` acts as the **parent container**, and each sub-element (Label, TextField, Button) is a **child component**.

--- 
# Layout Manager

In Java AWT, when multiple components (like buttons, labels, or text fields) are added to a container (such as a Frame or Panel), they must be arranged in a specific order and position.
This arrangement is controlled by an object known as the **Layout Manager**.

> A **Layout Manager** is an object that **automatically controls the size, position, and alignment** of components within a container.

Without a layout manager, all components would need to be placed manually using coordinates, which makes GUIs less flexible and harder to maintain.
Layout managers make your interfaces **adaptive**, so they look correct even if the window is resized or the platform changes.

## **Package and Interface**

All layout managers are part of the **`java.awt`** package and implement the **`LayoutManager`** interface.

```java
public interface LayoutManager {
    void addLayoutComponent(String name, Component comp);
    void removeLayoutComponent(Component comp);
    Dimension preferredLayoutSize(Container parent);
    Dimension minimumLayoutSize(Container parent);
    void layoutContainer(Container parent);
}
```

Every layout manager defines its own rules for how components are arranged within a container.

## **Why Use Layout Managers**

* To ensure **platform independence** of GUI appearance.
* To make windows **responsive and resizable** without breaking layout.
* To simplify arrangement of components automatically.
* To avoid pixel-based (manual) positioning.

## **Types of Layout Managers in AWT**

Java provides several pre-defined layout managers.
Each one arranges components differently based on logic, direction, and spacing.

### **(1) FlowLayout**

**Class:** `java.awt.FlowLayout`

**Description:**

* The **default layout manager** for `Panel` and `Applet`.
* Arranges components **left to right**, in the order they are added.
* When the current row is full, it moves to the **next row** (like text in a paragraph).

**Constructors:**

```java
FlowLayout()
FlowLayout(int alignment)
FlowLayout(int alignment, int hgap, int vgap)
```

**Common Alignments:**

* `FlowLayout.LEFT`
* `FlowLayout.CENTER` (default)
* `FlowLayout.RIGHT`

**Example:**

```java
import java.awt.*;

public class FlowExample {
    public static void main(String[] args) {
        Frame f = new Frame("FlowLayout Example");
        f.setLayout(new FlowLayout(FlowLayout.LEFT));

        f.add(new Button("One"));
        f.add(new Button("Two"));
        f.add(new Button("Three"));

        f.setSize(250, 150);
        f.setVisible(true);
    }
}
```

**Output:**
Buttons appear in a row from **left to right**, automatically adjusting when the window resizes.

### **(2) BorderLayout**

**Class:** `java.awt.BorderLayout`

**Description:**

* The **default layout manager** for `Frame` and `Dialog`.
* Divides the container into **five regions**:
  `NORTH`, `SOUTH`, `EAST`, `WEST`, `CENTER`.

**Constructors:**

```java
BorderLayout()
BorderLayout(int hgap, int vgap)
```

**Example:**

```java
import java.awt.*;

public class BorderExample {
    public static void main(String[] args) {
        Frame f = new Frame("BorderLayout Example");
        f.setLayout(new BorderLayout());

        f.add(new Button("North"), BorderLayout.NORTH);
        f.add(new Button("South"), BorderLayout.SOUTH);
        f.add(new Button("East"), BorderLayout.EAST);
        f.add(new Button("West"), BorderLayout.WEST);
        f.add(new Button("Center"), BorderLayout.CENTER);

        f.setSize(300, 200);
        f.setVisible(true);
    }
}
```

**Explanation:**
Each region can contain only **one component**, and the **center region** expands to fill the remaining space.

### **(3) GridLayout**

**Class:** `java.awt.GridLayout`

**Description:**

* Arranges components in a **grid (rows and columns)**.
* All cells in the grid are **equal size**.

**Constructors:**

```java
GridLayout(int rows, int cols)
GridLayout(int rows, int cols, int hgap, int vgap)
```

**Example:**

```java
import java.awt.*;

public class GridExample {
    public static void main(String[] args) {
        Frame f = new Frame("GridLayout Example");
        f.setLayout(new GridLayout(2, 3));

        for(int i=1; i<=6; i++) {
            f.add(new Button("Button " + i));
        }

        f.setSize(300, 200);
        f.setVisible(true);
    }
}
```

**Explanation:**
Creates a 2×3 grid where all buttons occupy equal space.

### **(4) CardLayout**

**Class:** `java.awt.CardLayout`

**Description:**

* Treats each component as a **“card”** — only **one card** is visible at a time.
* Useful for implementing **tabbed panes, forms, or wizard-style interfaces**.

**Constructors:**

```java
CardLayout()
CardLayout(int hgap, int vgap)
```

**Example:**

```java
import java.awt.*;
import java.awt.event.*;

public class CardExample extends Frame implements ActionListener {
    CardLayout cl;
    Panel p;

    public CardExample() {
        cl = new CardLayout();
        p = new Panel();
        p.setLayout(cl);

        p.add("1", new Button("Card 1"));
        p.add("2", new Button("Card 2"));
        p.add("3", new Button("Card 3"));

        Button b = new Button("Next");
        b.addActionListener(this);

        add(p, BorderLayout.CENTER);
        add(b, BorderLayout.SOUTH);

        setSize(300, 200);
        setVisible(true);
    }

    public void actionPerformed(ActionEvent e) {
        cl.next(p);
    }

    public static void main(String[] args) {
        new CardExample();
    }
}
```

**Explanation:**
Each button represents a “card,” and clicking “Next” switches between them.

### **(5) GridBagLayout**

**Class:** `java.awt.GridBagLayout`

**Description:**

* The **most flexible and complex layout manager**.
* Components can occupy **multiple rows or columns** and have **different sizes**.
* Uses a helper class **`GridBagConstraints`** to specify alignment and spacing.

**Example (simplified):**

```java
import java.awt.*;

public class GridBagExample {
    public static void main(String[] args) {
        Frame f = new Frame("GridBagLayout Example");
        f.setLayout(new GridBagLayout());
        GridBagConstraints gbc = new GridBagConstraints();

        gbc.gridx = 0; gbc.gridy = 0;
        f.add(new Button("Button 1"), gbc);

        gbc.gridx = 1; gbc.gridy = 0;
        f.add(new Button("Button 2"), gbc);

        gbc.gridx = 0; gbc.gridy = 1;
        gbc.gridwidth = 2;
        f.add(new Button("Button 3"), gbc);

        f.setSize(300, 200);
        f.setVisible(true);
    }
}
```

**Explanation:**
`GridBagLayout` allows components to span across cells and adjust flexibly as the window resizes.

## **Setting and Removing Layout Managers**

To **set a layout** for a container:

```java
setLayout(new FlowLayout());
```

To **remove layout management** (manual positioning):

```java
setLayout(null);
component.setBounds(x, y, width, height);
```

## **Comparison of Layout Managers**

| **Layout Manager** | **Arrangement**               | **Flexibility** | **Default For** |
| ------------------ | ----------------------------- | --------------- | --------------- |
| FlowLayout         | Left-to-right flow            | Moderate        | Panel, Applet   |
| BorderLayout       | Divides into 5 regions        | High            | Frame, Dialog   |
| GridLayout         | Equal-sized grid              | Low             | None            |
| CardLayout         | Stack of cards                | High            | None            |
| GridBagLayout      | Grid with flexible cell sizes | Very High       | None            |
| Null Layout        | Manual positioning            | Low             | None            |

## **Advantages of Using Layout Managers**

1. Automatic component resizing and repositioning.
2. Platform-independent design (adjusts to different screens).
3. Cleaner and more organized code.
4. Simplifies window resizing.
5. Easier maintenance compared to absolute positioning.

## **Disadvantages**

1. Limited control compared to pixel-based layout.
2. Complex managers (like `GridBagLayout`) can be hard to configure.
3. Sometimes unpredictable behavior if constraints are misused.

--- 
# Listeners

In Java’s AWT, *events* occur whenever the user interacts with GUI components — for example, clicking a button, moving the mouse, pressing a key, or resizing a window.
To **respond** to these events, Java uses a mechanism called the **Event Delegation Model**.

At the heart of this model lies the concept of a **Listener**.

> A **Listener** in Java is an **object that waits for an event to occur** and defines **what should happen** when that event occurs.

Listeners are implemented as **interfaces** in the `java.awt.event` package (and some in `javax.swing.event`).
Each listener interface contains one or more **callback methods** that are automatically invoked by the AWT Event Dispatch Thread (EDT) when the user performs the associated action.

## **Event Delegation Model (Quick Recap)**

Before understanding listeners fully, recall the three participants in Java’s event handling model:

| **Component**                            | **Event Source**                                                                | **Listener**                                                  |
| ---------------------------------------- | ------------------------------------------------------------------------------- | ------------------------------------------------------------- |
| The GUI element that generates an event. | The actual object that emits the event (like a Button, TextField, or Checkbox). | The object that wants to be notified when that event happens. |

**Flow:**

1. A user interacts with a GUI component (e.g., clicks a button).
2. That component (event source) **creates an event object** (like `ActionEvent`).
3. The event object is **passed to a listener** that has registered interest in that event.
4. The listener’s method (like `actionPerformed()`) executes the response code.

This model is called *delegation* because the source *delegates* the handling of the event to the listener.

## **Listener Interfaces**

All listener interfaces are defined in the **`java.awt.event`** package.
Each type of event has a corresponding **listener interface** and **event class**.

Let’s go through the most important ones:

### **(1) ActionListener**

**Package:** `java.awt.event`
**Event class:** `ActionEvent`

Used for components that generate **action events** — like Buttons, MenuItems, or TextFields (when Enter is pressed).

**Method:**

```java
void actionPerformed(ActionEvent e)
```

**Example:**

```java
import java.awt.*;
import java.awt.event.*;

public class ActionListenerExample extends Frame implements ActionListener {
    Button b;

    ActionListenerExample() {
        b = new Button("Click Me");
        b.addActionListener(this);
        add(b);
        setSize(200, 150);
        setLayout(new FlowLayout());
        setVisible(true);
    }

    public void actionPerformed(ActionEvent e) {
        b.setLabel("Clicked!");
    }

    public static void main(String[] args) {
        new ActionListenerExample();
    }
}
```

### **(2) ItemListener**

**Event class:** `ItemEvent`
Used for **item selection events**, like in Checkboxes, Choice, or List components.

**Method:**

```java
void itemStateChanged(ItemEvent e)
```

**Example:**

```java
Checkbox cb1 = new Checkbox("Music");
cb1.addItemListener(new ItemListener() {
    public void itemStateChanged(ItemEvent e) {
        System.out.println("Checkbox state changed!");
    }
});
```

### **(3) KeyListener**

**Event class:** `KeyEvent`
Used for handling **keyboard inputs** — pressing, releasing, or typing keys.

**Methods:**

```java
void keyPressed(KeyEvent e)
void keyReleased(KeyEvent e)
void keyTyped(KeyEvent e)
```

**Example:**

```java
TextField tf = new TextField();
tf.addKeyListener(new KeyListener() {
    public void keyPressed(KeyEvent e) {}
    public void keyReleased(KeyEvent e) {}
    public void keyTyped(KeyEvent e) {
        System.out.println("Key: " + e.getKeyChar());
    }
});
```

### **(4) MouseListener**

**Event class:** `MouseEvent`
Used to handle **mouse clicks and entry/exit events**.

**Methods:**

```java
void mouseClicked(MouseEvent e)
void mousePressed(MouseEvent e)
void mouseReleased(MouseEvent e)
void mouseEntered(MouseEvent e)
void mouseExited(MouseEvent e)
```

### **(5) MouseMotionListener**

**Event class:** `MouseEvent`
Used to handle **mouse drag and movement**.

**Methods:**

```java
void mouseDragged(MouseEvent e)
void mouseMoved(MouseEvent e)
```

### **(6) FocusListener**

**Event class:** `FocusEvent`
Used for handling **focus gained or lost** by components.

**Methods:**

```java
void focusGained(FocusEvent e)
void focusLost(FocusEvent e)
```

### **(7) WindowListener**

**Event class:** `WindowEvent`
Used for handling **window-level actions**, like open, close, minimize, etc.

**Methods:**

```java
void windowOpened(WindowEvent e)
void windowClosing(WindowEvent e)
void windowClosed(WindowEvent e)
void windowIconified(WindowEvent e)
void windowDeiconified(WindowEvent e)
void windowActivated(WindowEvent e)
void windowDeactivated(WindowEvent e)
```

**Example:**

```java
import java.awt.*;
import java.awt.event.*;

public class WindowExample extends Frame implements WindowListener {
    WindowExample() {
        addWindowListener(this);
        setSize(300, 200);
        setVisible(true);
    }
    public void windowClosing(WindowEvent e) {
        System.out.println("Window closing...");
        dispose();
    }
    // other methods can be left empty
    public void windowOpened(WindowEvent e) {}
    public void windowClosed(WindowEvent e) {}
    public void windowIconified(WindowEvent e) {}
    public void windowDeiconified(WindowEvent e) {}
    public void windowActivated(WindowEvent e) {}
    public void windowDeactivated(WindowEvent e) {}
    public static void main(String[] args) {
        new WindowExample();
    }
}
```

## **Adapter Classes**

Implementing listener interfaces like `WindowListener` or `MouseListener` can be tedious because they contain multiple methods, even if you need only one.

To simplify this, Java provides **adapter classes** — abstract classes that **implement listener interfaces** with **empty method bodies**.
You can **extend** these adapter classes and **override only the methods you need**.

**Common adapter classes:**

| **Event Interface** | **Adapter Class**  |
| ------------------- | ------------------ |
| MouseListener       | MouseAdapter       |
| MouseMotionListener | MouseMotionAdapter |
| KeyListener         | KeyAdapter         |
| FocusListener       | FocusAdapter       |
| WindowListener      | WindowAdapter      |

**Example (Using WindowAdapter):**

```java
addWindowListener(new WindowAdapter() {
    public void windowClosing(WindowEvent e) {
        dispose();
    }
});
```

This avoids having to define all seven methods of `WindowListener`.

## **Event Registration**

To make a component respond to an event, a listener must be **registered** with that component using methods like:

```java
component.add<ListenerType>(ListenerObject);
```

Examples:

```java
button.addActionListener(this);
checkbox.addItemListener(this);
textField.addKeyListener(this);
frame.addWindowListener(new MyWindowAdapter());
```

You can register **multiple listeners** to one component, and one listener can listen to **multiple components**.

## **Advantages of Using Listeners**

* Decouples event-handling logic from component design.
* Simplifies maintenance and readability.
* Allows reusable listener classes.
* Encourages clean object-oriented design.
* Supports multiple listeners for one event source.

--- 
# Adapter Classes

> **Definition:**
> An **Adapter Class** in Java is an **abstract class** that implements a **listener interface** and provides **default (empty)** implementations for all its methods.
> Programmers can **extend** this adapter class and **override only the methods they need**, making event handling simpler and cleaner.

## **Package and Nature**

All adapter classes are part of the **`java.awt.event`** package.
They are **abstract classes** that implement one or more listener interfaces.
Because the methods have empty bodies, subclasses can selectively override the ones they actually need.

**Syntax pattern:**

```java
class <ComponentName>Adapter implements <ListenerInterface> {
    // Empty method implementations
}
```

## **Why Adapter Classes Are Needed**

Let’s take an example:
The `WindowListener` interface contains **seven methods**:

```java
void windowOpened(WindowEvent e);
void windowClosing(WindowEvent e);
void windowClosed(WindowEvent e);
void windowIconified(WindowEvent e);
void windowDeiconified(WindowEvent e);
void windowActivated(WindowEvent e);
void windowDeactivated(WindowEvent e);
```

If you only want to perform an action when the window closes,
you’d still be forced to define all seven methods — even if six of them are empty.

That’s unnecessary and messy.

So instead, Java provides a class called **`WindowAdapter`** that already implements all seven methods with empty bodies.
You can **extend** it and override only the one you care about (`windowClosing()`).

## **Commonly Used Adapter Classes**

Here’s a list of major adapter classes, their corresponding listener interfaces, and what they handle:

| **Adapter Class**          | **Implements Interface**  | **Used For Handling**                           |
| -------------------------- | ------------------------- | ----------------------------------------------- |
| **ComponentAdapter**       | `ComponentListener`       | Component resize, move, or show/hide events     |
| **ContainerAdapter**       | `ContainerListener`       | Adding or removing components in a container    |
| **FocusAdapter**           | `FocusListener`           | Focus gained or lost events                     |
| **KeyAdapter**             | `KeyListener`             | Keyboard key press/release/typed events         |
| **MouseAdapter**           | `MouseListener`           | Mouse click, press, release, enter, exit events |
| **MouseMotionAdapter**     | `MouseMotionListener`     | Mouse dragging or movement events               |
| **WindowAdapter**          | `WindowListener`          | Window open, close, minimize, etc. events       |
| **HierarchyBoundsAdapter** | `HierarchyBoundsListener` | Component hierarchy changes                     |

## **Example 1 — Without Adapter Class**

Here’s how verbose code looks **without** using an adapter class:

```java
import java.awt.*;
import java.awt.event.*;

public class NoAdapterExample extends Frame implements WindowListener {
    NoAdapterExample() {
        addWindowListener(this);
        setSize(300, 200);
        setVisible(true);
    }

    public void windowClosing(WindowEvent e) {
        dispose();
    }

    // All other methods must be defined, even if empty
    public void windowOpened(WindowEvent e) {}
    public void windowClosed(WindowEvent e) {}
    public void windowIconified(WindowEvent e) {}
    public void windowDeiconified(WindowEvent e) {}
    public void windowActivated(WindowEvent e) {}
    public void windowDeactivated(WindowEvent e) {}

    public static void main(String[] args) {
        new NoAdapterExample();
    }
}
```

See how it’s unnecessarily long?
## **Example 2 — Using Adapter Class**

Now look at the **simplified** version using an adapter class:

```java
import java.awt.*;
import java.awt.event.*;

public class AdapterExample extends Frame {
    AdapterExample() {
        addWindowListener(new WindowAdapter() {
            public void windowClosing(WindowEvent e) {
                dispose();
            }
        });

        setSize(300, 200);
        setVisible(true);
    }

    public static void main(String[] args) {
        new AdapterExample();
    }
}
```

**Explanation:**

* `WindowAdapter` is extended anonymously using an **anonymous inner class**.
* Only the relevant method (`windowClosing()`) is overridden.
* All other methods are inherited from `WindowAdapter` with empty definitions.

This makes the code **clean, concise, and readable**.

## **Key Characteristics of Adapter Classes**

* Defined as **abstract**.
* Provide **empty implementations** of all methods in a listener interface.
* Make code **shorter and easier to maintain**.
* Can be used directly through **anonymous inner classes**.
* Belong to the **`java.awt.event`** package.

## **Advantages**

1. **Simplifies event handling** — override only required methods.
2. **Reduces boilerplate code**.
3. **Improves readability and clarity**.
4. Works seamlessly with **anonymous inner classes** for concise implementations.
5. Encourages better **encapsulation** of event logic.

## **Limitations**

1. Can only be used for interfaces that have corresponding adapter classes.
2. Since adapter classes are **abstract**, they cannot be instantiated directly.
3. Not suitable for functional-style or lambda-based event handling (used more in Swing/JavaFX).
4. Slightly increases class hierarchy depth.

--- 

# Event Delegation Model

> The **Event Delegation Model** in Java is a mechanism that **separates the event-handling logic from the event-generating components** by delegating the task of handling an event to a different object called a **listener**.

This model is **object-oriented**, **flexible**, and **efficient**, forming the backbone of Java’s GUI event-handling system.

## **Before the Delegation Model (Old Approach)**

In early versions of Java (before JDK 1.1), event handling used the **Inheritance Model**, where every component was responsible for handling its own events.  
For example, to handle a button click, the button class itself had to override event-handling methods.

This approach caused:

- Tight coupling between UI components and logic,
    
- Inefficient event handling, and
    
- Poor code reusability.
    

Thus, the **Delegation Event Model** was introduced in **Java 1.1** to overcome these limitations.

## **Core Concept**

The Event Delegation Model divides event handling into **three key participants**:

| **Participant**    | **Role**                                                                                                     |
| ------------------ | ------------------------------------------------------------------------------------------------------------ |
| **Event Source**   | The object (component) that generates an event (e.g., Button, TextField, Frame).                             |
| **Event Object**   | An instance of a class (like `ActionEvent`, `KeyEvent`, etc.) that encapsulates information about the event. |
| **Event Listener** | An object that receives and handles the event through callback methods.                                      |

When an event occurs, the **event source** creates an **event object** and sends it to the **listener** that is registered to handle it. The listener’s method executes the response logic.

## **Flow of Event Handling (Step-by-Step)**

1. **User Action**  
    A user performs an action (click, key press, etc.) on a GUI component.
   
2. **Event Generation**  
    The component (source) creates an **event object** representing that specific action.
   
3. **Event Registration**  
    The source has one or more **listeners** registered to it. Registration happens using methods like `addActionListener()`, `addKeyListener()`, etc.
   
4. **Event Delegation**  
    The event source **delegates the event object** to the registered listener(s).
   
5. **Event Handling**  
    The listener’s corresponding **callback method** (like `actionPerformed()`) is automatically invoked to handle the event.
   
6. **Event Response**  
    The listener executes the code that defines how the program should respond to that event.
   

## **Example: Button Click Event Using Delegation Model**

```java
import java.awt.*;
import java.awt.event.*;

public class DelegationExample extends Frame implements ActionListener {
    Button b;

    DelegationExample() {
        b = new Button("Click Me");
        add(b);
        b.addActionListener(this);  // Register listener
        setSize(300, 200);
        setLayout(new FlowLayout());
        setVisible(true);
    }

    // Event-handling method (callback)
    public void actionPerformed(ActionEvent e) {
        b.setLabel("Clicked!");
    }

    public static void main(String[] args) {
        new DelegationExample();
    }
}
```

### **Explanation**

- The **Button (event source)** generates an `ActionEvent` when clicked.
   
- The **Frame (listener)** implements `ActionListener`.
   
- The button calls `addActionListener(this)` to **register** the listener.
   
- When clicked, the button **delegates** the event to the listener’s `actionPerformed()` method.
   

## **Key Interfaces and Event Classes**

All listener interfaces and event classes are defined in the **`java.awt.event`** package.

| **Listener Interface** | **Event Class** | **Triggered By**          |
| ---------------------- | --------------- | ------------------------- |
| ActionListener         | ActionEvent     | Button, MenuItem          |
| ItemListener           | ItemEvent       | Checkbox, Choice          |
| KeyListener            | KeyEvent        | Keyboard actions          |
| MouseListener          | MouseEvent      | Mouse clicks              |
| MouseMotionListener    | MouseEvent      | Mouse drag or move        |
| WindowListener         | WindowEvent     | Window operations         |
| FocusListener          | FocusEvent      | Component focus gain/loss |
## **Event Registration Methods**

Each component provides methods to register and remove listeners dynamically.

| **Register Listener**                 | **Remove Listener**                      |
| ------------------------------------- | ---------------------------------------- |
| `addActionListener(ActionListener l)` | `removeActionListener(ActionListener l)` |
| `addItemListener(ItemListener l)`     | `removeItemListener(ItemListener l)`     |
| `addMouseListener(MouseListener l)`   | `removeMouseListener(MouseListener l)`   |
| `addKeyListener(KeyListener l)`       | `removeKeyListener(KeyListener l)`       |

This allows flexible event handling where multiple listeners can listen to the same source or one listener can handle multiple components.

## **Event Object**

Every event generated is represented as an **object** that carries detailed information about the event.  
All event classes are derived from the **`java.util.EventObject`** superclass.

**Hierarchy Example:**

```
java.lang.Object  
    ↳ java.util.EventObject  
         ↳ java.awt.AWTEvent  
              ↳ ActionEvent, MouseEvent, KeyEvent, etc.
```

Each event object provides methods to obtain details:

- `getSource()` – returns the source of the event.
    
- `getID()` – returns event type identifier.
    
- Other event-specific methods like `getKeyChar()`, `getX()`, `getButton()`, etc.
    

## **Advantages of Event Delegation Model**

1. **Separation of concerns:**  
    Keeps event-handling code separate from UI components.
   
2. **Reusability:**  
    Listeners can be reused for multiple sources.
   
3. **Flexibility:**  
    Multiple listeners can handle the same event source.
   
4. **Clean design:**  
    Encourages modular, object-oriented architecture.
   
5. **Efficiency:**  
    Events are processed only by the registered listeners, reducing unnecessary overhead.
   
6. **Better maintainability:**  
    Easier to update event logic without affecting UI design.
   

## **10. Example Diagram (Explained in Words)**

Imagine a **Button** named `b1` and a **Listener** object named `handler`.

When `b1` is clicked:  
→ `b1` (event source) creates an `ActionEvent` object.  
→ That event is **delegated** to the `handler` (event listener).  
→ The listener’s method (`actionPerformed()`) executes.  
→ The UI responds (e.g., text changes, dialog opens, etc.).

This is why it’s called the _delegation_ model — the source _delegates_ the responsibility of handling the event to a separate object.

---

## **11. Comparison: Old Event Model vs. Event Delegation Model**

| **Aspect**  | **Old Model (Inheritance)**                        | **Event Delegation Model**                    |
| ----------- | -------------------------------------------------- | --------------------------------------------- |
| Coupling    | Tightly coupled (component handles its own events) | Loosely coupled (listener handles separately) |
| Reusability | Low                                                | High                                          |
| Flexibility | Limited                                            | Highly flexible                               |
| Maintenance | Difficult                                          | Easier                                        |
| Efficiency  | Processes all events                               | Processes only relevant events                |
| Design      | Procedural                                         | Object-oriented                               |

---
# Swing: Introduction to Swing Component and Container Classes

**Swing** is a **GUI (Graphical User Interface)** toolkit built on top of AWT (Abstract Window Toolkit) in Java.  
It is part of **Java Foundation Classes (JFC)** and provides a **rich set of lightweight components** for building interactive desktop applications.

> Swing is a **platform-independent, lightweight, and extensible** GUI toolkit for Java that allows developers to create windows-based applications with a modern look and feel.

### **Key Package**

All Swing classes are part of the **`javax.swing`** package.

## **Why Swing Was Introduced**

The **AWT** components were **heavyweight**, meaning each GUI control relied on native (OS-level) components.  
This caused **platform dependency**, **inconsistent look and feel**, and **limited flexibility**.

Swing was introduced to fix these issues:

- It’s **100% Java**, so platform-independent.
- Offers **custom look and feel** that can mimic Windows, Linux, or Mac styles.
- Provides **advanced GUI components** like tables, trees, toolbars, sliders, etc.
- Fully **MVC (Model-View-Controller)** based design for better separation between data, view, and logic.
   
## **3. Features of Swing**

| **Feature**                 | **Description**                                                         |
| --------------------------- | ----------------------------------------------------------------------- |
| **Lightweight Components**  | Do not rely on native OS peers; drawn by Java itself.                   |
| **Platform Independent**    | Works identically across all OS environments.                           |
| **MVC Architecture**        | Separates data (Model), presentation (View), and behavior (Controller). |
| **Pluggable Look and Feel** | Can switch between multiple UI styles dynamically.                      |
| **Rich Component Set**      | Provides advanced widgets like JTable, JTree, JTabbedPane, etc.         |
| **Highly Customizable**     | Developers can easily extend and style components.                      |
| **Double Buffering**        | Prevents flickering in UI rendering.                                    |
| **Event-Driven**            | Uses the AWT Event Delegation Model for interaction handling.           |
## **Difference Between AWT and Swing**

| **Aspect**          | **AWT**                     | **Swing**                                 |
| ------------------- | --------------------------- | ----------------------------------------- |
| Component Type      | Heavyweight (uses OS peers) | Lightweight (pure Java)                   |
| Package             | `java.awt`                  | `javax.swing`                             |
| Platform Dependence | Platform-dependent          | Platform-independent                      |
| Look and Feel       | Native OS look              | Pluggable look and feel                   |
| Architecture        | Partially MVC               | Fully MVC                                 |
| Flexibility         | Limited                     | High customization possible               |
| Advanced Controls   | Basic controls only         | Includes JTable, JTree, JTabbedPane, etc. |
## **Swing Architecture**

Swing is built on **three layers**:

1. **AWT Core** — basic event handling and windowing system.
   
2. **Pluggable Look & Feel Layer** — defines the appearance of components.
   
3. **Swing Components Layer** — high-level components that developers interact with.
   

All Swing components inherit from **`JComponent`**, which in turn extends `java.awt.Container`.

## **Hierarchy of Swing Classes**

```
java.lang.Object  
   ↳ java.awt.Component  
        ↳ java.awt.Container  
             ↳ javax.swing.JComponent  
                  ↳ (All Swing GUI components)
```

Examples:

- `JButton`, `JLabel`, `JTextField`, `JCheckBox`, `JComboBox`, etc.
   

**Top-level containers** (like `JFrame`, `JDialog`, and `JApplet`) do **not** inherit from `JComponent` but hold them.

## **Swing Component Classes**

Swing components are **visual elements** that represent controls or interface elements of an application.

All Swing components start with the **prefix ‘J’** to differentiate them from their AWT counterparts.

| **Component**                    | **Description**                    | **Example**                     |
| -------------------------------- | ---------------------------------- | ------------------------------- |
| `JLabel`                         | Displays a text or image label.    | `new JLabel("Name:");`          |
| `JButton`                        | Clickable button.                  | `new JButton("Submit");`        |
| `JTextField`                     | Single-line text input field.      | `new JTextField(20);`           |
| `JTextArea`                      | Multi-line text input field.       | `new JTextArea(5, 20);`         |
| `JCheckBox`                      | Checkbox with on/off state.        | `new JCheckBox("Remember me");` |
| `JRadioButton`                   | Part of a radio button group.      | `new JRadioButton("Male");`     |
| `JComboBox`                      | Drop-down list.                    | `new JComboBox(items);`         |
| `JList`                          | Displays a list of items.          | `new JList(listData);`          |
| `JMenu`, `JMenuBar`, `JMenuItem` | Menu components.                   | —                               |
| `JTable`                         | Displays tabular data.             | —                               |
| `JTree`                          | Displays hierarchical data.        | —                               |
| `JSlider`                        | Allows value selection by sliding. | —                               |
| `JProgressBar`                   | Shows progress of a task.          | —                               |
| `JToolBar`                       | Contains buttons for quick access. | —                               |

These components extend from `JComponent`, gaining methods like:

- `setBackground(Color c)`
- `setForeground(Color c)`
- `setFont(Font f)`
- `setEnabled(boolean b)`
- `setToolTipText(String text)`
  
## **Container Classes**

A **container** is a special component that can **hold and organize other components**.  
It defines how child components are arranged using **layout managers**.

### **Types of Containers**

| **Container**      | **Description**                                             |
| ------------------ | ----------------------------------------------------------- |
| **JPanel**         | A simple container for grouping components.                 |
| **JFrame**         | A top-level window with a title bar, menu bar, and borders. |
| **JDialog**        | Used for popup or dialog windows.                           |
| **JApplet**        | Swing version of Applet for browser-based GUI.              |
| **JInternalFrame** | Used for MDI (Multiple Document Interface) applications.    |

## **Example: Simple Swing Program**

```java
import javax.swing.*;

public class SwingExample {
    public static void main(String[] args) {
        JFrame frame = new JFrame("Swing Demo");

        JLabel label = new JLabel("Enter your name:");
        JTextField textField = new JTextField(15);
        JButton button = new JButton("Submit");

        JPanel panel = new JPanel();   // Container
        panel.add(label);
        panel.add(textField);
        panel.add(button);

        frame.add(panel);
        frame.setSize(300, 150);
        frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        frame.setVisible(true);
    }
}
```

### **Explanation**

- `JFrame` acts as the **main window container**.
- `JPanel` is used to **group** components.
- `JLabel`, `JTextField`, and `JButton` are **Swing components** added to the panel.
- The frame displays the panel using the **FlowLayout** by default.
  

## **Component vs Container**

| **Aspect**      | **Component**                                      | **Container**                         |
| --------------- | -------------------------------------------------- | ------------------------------------- |
| **Purpose**     | Represents a GUI element (like a button or label). | Holds and organizes other components. |
| **Inheritance** | Inherits from `Component` or `JComponent`.         | Inherits from `Container`.            |
| **Example**     | `JButton`, `JTextField`, `JLabel`                  | `JPanel`, `JFrame`, `JDialog`         |
| **Containment** | Cannot contain other components.                   | Can contain one or more components.   |

## **Advantages of Swing Components**

- **Lightweight and faster** rendering.
- **Consistent look** across platforms.
- **Customizable UI** through pluggable look-and-feel.
- **Supports drag and drop**, tooltips, icons, and shortcuts.
- **Thread-safe GUI updates** using `SwingUtilities.invokeLater()`.

--- 
--- 
