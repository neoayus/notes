# PHP Advanced Features: Form Handling, GET and POST Methods, Overview of Cookies and Sessions Management

## **1. Form Handling in PHP**

Form handling in PHP allows the collection and processing of data submitted by users through HTML forms. PHP handles form submissions in a simple, secure, and efficient way.

### **How Forms Work in PHP:**

- HTML forms collect user input and send the data to the server.
- PHP processes this data and returns the output to the browser.

### **Form Structure** (HTML):

```html
<form method="post" action="submit.php">
  <label for="name">Name:</label>
  <input type="text" id="name" name="name" required>
  <br>
  <label for="email">Email:</label>
  <input type="email" id="email" name="email" required>
  <br>
  <input type="submit" value="Submit">
</form>
```

- **`method="post"`**: Specifies the HTTP method used to send data. It can be `GET` or `POST`.
- **`action="submit.php"`**: The PHP file that will process the submitted data.

### **Accessing Form Data in PHP:**

+ **`$_GET`** and **`$_POST`** are superglobals in PHP used to access data sent to the server via **GET** and **POST** HTTP methods, respectively.

- **`$_POST`**: Used to collect form data after submitting the form using the `POST` method.
- **`$_GET`**: Used to collect form data after submitting the form using the `GET` method.

**Example of form handling using PHP:**

```php
<?php
  if ($_SERVER["REQUEST_METHOD"] == "POST") {
    $name = $_POST['name'];
    $email = $_POST['email'];
    
    echo "Name: " . $name . "<br>";
    echo "Email: " . $email;
  }
?>
```
here, the form data is accessed using the `$_POST` superglobal array, which holds the submitted values.

---

## **2. GET and POST Methods in PHP**

PHP supports two primary methods for collecting form data: **GET** and **POST**. These methods differ in how they send data to the server.

### **GET Method:**

- The **`GET`** method sends data through the URL.
- It is less secure because data is visible in the browser’s address bar.
- Typically used for retrieving data (not modifying).

**Example:**

```html
<form method="get" action="submit.php">
  <input type="text" name="username">
  <input type="submit">
</form>
```

Accessing the data:

```php
<?php
  $username = $_GET['username'];
  echo "Username: " . $username;
?>
```

### **POST Method:**

- The **`POST`** method sends data through the HTTP request body, meaning it is not visible in the URL and is more secure.
- Typically used for sending sensitive or large amounts of data (like passwords).

**Example:**

```html
<form method="post" action="submit.php">
  <input type="password" name="password">
  <input type="submit">
</form>
```

Accessing the data:

```php
<?php
  $password = $_POST['password'];
  echo "Password: " . $password;
?>
```

### **Differences Between GET and POST**:

| Feature         | GET                              | POST                            |
| --------------- | -------------------------------- | ------------------------------- |
| Data Visibility | Visible in URL (in query string) | Hidden in HTTP request body     |
| Data Length     | Limited (depends on URL length)  | No limit (can send large data)  |
| Security        | Less secure (data is exposed)    | More secure (data is hidden)    |
| Usage           | Retrieving data                  | Sending sensitive or large data |
## **3. Overview of Cookies in PHP**

**Cookies** are small pieces of data stored on the client’s browser. PHP can set and retrieve cookies to store user preferences or session information.

### **Setting a Cookie**:

You can use the **`setcookie()`** function to send a cookie to the browser.

**Syntax**:
```php
setcookie(name, value, expire, path, domain, secure, httponly);
```

- **`name`**: The name of the cookie.
- **`value`**: The value of the cookie.
- **`expire`**: The expiration time (in seconds).
- **`path`**: The path within the domain where the cookie is available.
- **`secure`**: Whether the cookie should only be sent over HTTPS.
- **`httponly`**: Whether the cookie is accessible via JavaScript (set to true for security).

**Example of setting a cookie**:

```php
<?php
  setcookie("user", "JohnDoe", time() + 3600, "/");
  echo "Cookie 'user' set for 1 hour.";
?>
	```

### **Retrieving a Cookie**:

Use the **`$_COOKIE`** super global to access the value of a cookie.

```php
<?php
  if(isset($_COOKIE['user'])) {
    echo "Welcome back, " . $_COOKIE['user'];
  } else {
    echo "Welcome, new user!";
  }
?>
```

### **Deleting a Cookie**:

To delete a cookie, you must set its expiration date to a past time.
```php
<?php
  setcookie("user", "", time() - 3600, "/");  // Delete the cookie
  echo "Cookie 'user' deleted.";
?>
```

---

## **4. Overview of Sessions in PHP**

**Sessions** store user data on the server and are used to maintain state between different page requests.

### **Starting a Session**:

To use sessions in PHP, you need to call **`session_start()`** at the beginning of each page that will access session data.

```php
<?php
  session_start();  // Start the session
  $_SESSION['username'] = 'JohnDoe';  // Store data in session
?>
```

### **Accessing Session Data**:

You can access session data using the **`$_SESSION`** superglobal.

```php
<?php
  session_start();
  echo "Welcome, " . $_SESSION['username'];  // Outputs "Welcome, JohnDoe"
?>
```

### **Destroying a Session**:

To completely remove a session and its data, use **`session_destroy()`**.

**Example**:

```php
<?php
  session_start();
  session_unset();  // Remove all session variables
  session_destroy();  // Destroy the session
  echo "Session destroyed.";
?>
```

### **Session vs. Cookie**:

| Feature      | Session                                     | Cookie                                   |
| ------------ | ------------------------------------------- | ---------------------------------------- |
| Data Storage | Server-side                                 | Client-side (in browser)                 |
| Expiry       | Ends when the session ends (browser closed) | Can be set with an expiration time       |
| Security     | More secure (data not exposed to user)      | Less secure (data stored in the browser) |

# Data Handling in PHP using MySQL Database

## **1. Overview of Handling MySQL Database in PHP**

### **What is MySQL?**

- **MySQL** is a popular open-source relational database management system (RDBMS) used for storing and managing data in web applications.
- PHP provides built-in functions to interact with MySQL.

---

### **Connecting PHP to MySQL**

PHP can connect to a MySQL database using:

1. **MySQLi (MySQL Improved)**: A procedural and object-oriented extension.
2. **PDO (PHP Data Objects)**: A more flexible and secure method.

#### **MySQLi Connection (Procedural):**

```php
<?php
  $servername = "localhost";
  $username = "root";
  $password = "";
  $dbname = "my_database";

  // Create a connection
  $conn = mysqli_connect($servername, $username, $password, $dbname);

  // Check connection
  if (!$conn) {
    die("Connection failed: " . mysqli_connect_error());
  }
  echo "Connected successfully";
?>
```

### **Basic SQL Commands in PHP**

PHP uses SQL queries to interact with a MySQL database. Common operations include:

1. **Creating a Database:**

```php
<?php
  $sql = "CREATE DATABASE my_database";
  if (mysqli_query($conn, $sql)) {
    echo "Database created successfully";
  } else {
    echo "Error creating database: " . mysqli_error($conn);
  }
?>
```

2. **Creating a Table:**

```php
<?php
  $sql = "CREATE TABLE users (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(50),
    email VARCHAR(50),
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
  )";
  if (mysqli_query($conn, $sql)) {
    echo "Table created successfully";
  } else {
    echo "Error creating table: " . mysqli_error($conn);
  }
?>
```

---

## **2. Storing Data in MySQL Database Using PHP**

### **Using XHTML Forms to Collect User Data**

Forms provide a user-friendly interface for submitting data to the server.

**HTML Form:**

```html
<form method="post" action="store_data.php">
  <label for="name">Name:</label>
  <input type="text" id="name" name="name" required>
  <br>
  <label for="email">Email:</label>
  <input type="email" id="email" name="email" required>
  <br>
  <input type="submit" value="Submit">
</form>
```

### **Inserting Data into MySQL Database**

The submitted form data is processed using PHP and inserted into the database.

**store_data.php:**

```php
<?php
  $conn = mysqli_connect("localhost", "root", "", "my_database");

  if ($_SERVER["REQUEST_METHOD"] == "POST") {
    $name = $_POST['name'];
    $email = $_POST['email'];

    $sql = "INSERT INTO users (name, email) VALUES ('$name', '$email')";

    if (mysqli_query($conn, $sql)) {
      echo "Data stored successfully";
    } else {
      echo "Error: " . $sql . "<br>" . mysqli_error($conn);
    }
  }
?>
```

---

## **3. Retrieving Data from MySQL Database Using PHP**

### **Querying Data**

Data can be fetched using SQL `SELECT` queries and displayed on the webpage.

**Example:**

```php
<?php
  $conn = mysqli_connect("localhost", "root", "", "my_database");

  $sql = "SELECT id, name, email FROM users";
  $result = mysqli_query($conn, $sql);

  if (mysqli_num_rows($result) > 0) {
    while ($row = mysqli_fetch_assoc($result)) {
      echo "ID: " . $row["id"] . " - Name: " . $row["name"] . " - Email: " . $row["email"] . "<br>";
    }
  } else {
    echo "No records found";
  }
?>
```

---

## **4. Integration of PHP, MySQL, and XHTML Forms**

### **Use Case: User Registration System**

Below is a step-by-step example of a complete user registration process using XHTML forms, PHP, and MySQL.

#### **HTML Form (user_registration.html):**

```html
<form method="post" action="register_user.php">
  <label for="username">Username:</label>
  <input type="text" id="username" name="username" required>
  <br>
  <label for="password">Password:</label>
  <input type="password" id="password" name="password" required>
  <br>
  <label for="email">Email:</label>
  <input type="email" id="email" name="email" required>
  <br>
  <input type="submit" value="Register">
</form>
```

#### **PHP Script (register_user.php):**

```php
<?php
  $conn = mysqli_connect("localhost", "root", "", "my_database");

  if ($_SERVER["REQUEST_METHOD"] == "POST") {
    $username = $_POST['username'];
    $password = password_hash($_POST['password'], PASSWORD_BCRYPT);  // Encrypting the password
    $email = $_POST['email'];

    $sql = "INSERT INTO users (name, email, password) VALUES ('$username', '$email', '$password')";

    if (mysqli_query($conn, $sql)) {
      echo "Registration successful!";
    } else {
      echo "Error: " . $sql . "<br>" . mysqli_error($conn);
    }
  }
?>
```
