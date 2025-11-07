## Unit 05: ADO.NET Architecture:

Using server explorer window
Connection class
Command class
Direct Command execution against database
Using Parameters in command
Performing CRUD operations 
Connected Vs disconnected Architecture
Data reader class
The dataset and dataset Architecture 
Comparison ADO & ADO.NET on disconnected Data architecture
Implementing Disconnected Data Architecture
Performing CRUD operations in disconnected architecture
Entity Framework introduction.

# .NET Data Providers**

In ADO.NET, a **.NET Data Provider** is a collection of classes that enable data access and manipulation from various data sources. These providers are optimized for specific databases and serve as the bridge between the application and the data source. They handle connections, commands, data retrieval, and transactions efficiently.

### Main Components of a .NET Data Provider

1. **Connection Object**

   * Establishes and manages the connection to the data source.
   * Example:

     * `SqlConnection` for SQL Server
     * `OleDbConnection` for OLE DB data sources
     * `OdbcConnection` for ODBC
     * `OracleConnection` for Oracle databases

2. **Command Object**

   * Represents a SQL query or stored procedure to execute against the database.
   * Provides methods like `ExecuteReader()`, `ExecuteScalar()`, and `ExecuteNonQuery()`.
   * Example: `SqlCommand`, `OleDbCommand`.

3. **DataReader Object**

   * Provides fast, forward-only, read-only access to data from the data source.
   * Example: `SqlDataReader`, `OleDbDataReader`.
   * Used for performance-critical operations where only reading data is required.

4. **DataAdapter Object**

   * Acts as a bridge between the DataSet and the data source.
   * Used to fill DataSets and update data sources based on changes made in the DataSet.
   * Example: `SqlDataAdapter`, `OleDbDataAdapter`.

5. **DataSet (Disconnected Data Access)**

   * Represents an in-memory cache of data.
   * Works independently of the data source.
   * Can contain multiple tables and relationships.

### Types of .NET Data Providers

1. **SQL Server Data Provider** (`System.Data.SqlClient`)

   * Optimized for Microsoft SQL Server.
   * Offers best performance for SQL Server-based applications.

2. **OLE DB Data Provider** (`System.Data.OleDb`)

   * Provides access to any OLE DB-compatible data source.
   * Used for older databases and Excel connections.

3. **ODBC Data Provider** (`System.Data.Odbc`)

   * Allows connection to any ODBC-compliant data source.

4. **Oracle Data Provider** (`System.Data.OracleClient`)

   * Used to connect to Oracle databases.

5. **.NET Data Provider for Entity Framework** (`System.Data.EntityClient`)

   * Used with Entity Framework for object-relational mapping (ORM).

### Working of a Data Provider

1. Create a connection using the **Connection** object.
2. Define SQL queries using the **Command** object.
3. Execute queries and retrieve data using **DataReader** or **DataAdapter**.
4. Optionally store and manipulate data using a **DataSet** (for disconnected operations).
5. Close the connection.
### Example

```csharp
using System;
using System.Data;
using System.Data.SqlClient;

class Example
{
    static void Main()
    {
        SqlConnection conn = new SqlConnection("Data Source=Server;Initial Catalog=DB;Integrated Security=True");
        SqlCommand cmd = new SqlCommand("SELECT * FROM Employees", conn);

        conn.Open();
        SqlDataReader reader = cmd.ExecuteReader();

        while (reader.Read())
        {
            Console.WriteLine(reader["Name"]);
        }

        reader.Close();
        conn.Close();
    }
}
```

--- 
# Database Connectivity

**Database Connectivity** is the mechanism through which a .NET application connects to a data source using a connection string, sends SQL commands, retrieves results, and manages transactions. It allows an application to interact with databases in both connected and disconnected modes.

ADO.NET uses data providers to connect and communicate with the database efficiently, ensuring secure and managed access to data.

---

### Steps for Database Connectivity in ADO.NET

1. **Establish a Connection**

   * Use a `Connection` object (e.g., `SqlConnection`) to connect to the database.
   * The connection requires a **connection string** that includes the server name, database name, and authentication details.

2. **Create a Command**

   * Use a `Command` object (e.g., `SqlCommand`) to define the SQL query or stored procedure to be executed.

3. **Execute the Command**

   * The command can be executed in different ways depending on the type of query:

     * `ExecuteReader()` → retrieves data using a `DataReader` (read-only, forward-only).
     * `ExecuteScalar()` → returns a single value (like COUNT or MAX).
     * `ExecuteNonQuery()` → executes insert, update, or delete statements.

4. **Process the Results**

   * Retrieve and display the data returned by the query using `DataReader` or fill a `DataSet` using a `DataAdapter`.

5. **Close the Connection**

   * Always close the connection to free up resources using the `Close()` or `Dispose()` method.

---

### Example of Database Connectivity in C#

```csharp
using System;
using System.Data;
using System.Data.SqlClient;

class DatabaseExample
{
    static void Main()
    {
        // Step 1: Create connection string
        string connectionString = "Data Source=ServerName;Initial Catalog=EmployeeDB;Integrated Security=True";

        // Step 2: Establish connection
        SqlConnection connection = new SqlConnection(connectionString);

        // Step 3: Create command
        SqlCommand command = new SqlCommand("SELECT * FROM Employees", connection);

        // Step 4: Open connection
        connection.Open();

        // Step 5: Execute command and read data
        SqlDataReader reader = command.ExecuteReader();

        while (reader.Read())
        {
            Console.WriteLine(reader["EmployeeName"] + " - " + reader["Department"]);
        }

        // Step 6: Close reader and connection
        reader.Close();
        connection.Close();
    }
}
```

### Explanation of Code

1. **Connection String:** Specifies where and how to connect to the database.
2. **SqlConnection:** Manages the connection to SQL Server.
3. **SqlCommand:** Executes SQL queries or stored procedures.
4. **SqlDataReader:** Reads data row by row in a connected mode.
5. **Close():** Closes the active connection to avoid resource leaks.

### Connection String Example

```plaintext
Data Source=ServerName;Initial Catalog=DatabaseName;User ID=UserName;Password=Password;
```

* **Data Source:** Database server name or IP address.
* **Initial Catalog:** Database name.
* **User ID / Password:** Authentication credentials.
* **Integrated Security=True:** Uses Windows Authentication.

### Types of Data Access

1. **Connected Mode:**

   * Uses `DataReader`.
   * Maintains an active connection to the database.
   * Fast and memory-efficient.

2. **Disconnected Mode:**

   * Uses `DataSet` and `DataAdapter`.
   * Data is retrieved, stored locally, and the connection is closed.
   * Suitable for offline or batch operations.

### Best Practices

* Always close connections after use.
* Use **`using`** blocks to ensure automatic disposal of objects.
* Handle exceptions using **try-catch-finally**.
* Use **parameterized queries** to prevent SQL injection.
* Avoid keeping connections open unnecessarily.

### Example Using Parameterized Query

```csharp
SqlCommand cmd = new SqlCommand("SELECT * FROM Employees WHERE Department = @dept", connection);
cmd.Parameters.AddWithValue("@dept", "HR");
```


# Architectures in .NET

The architecture of .NET provides the structural foundation for developing, running, and managing applications. It defines how various components interact with each other — from the source code written by the developer to the execution of that code in the runtime environment.

### Overview of .NET Architecture

The .NET architecture is built around the **Common Language Runtime (CLR)** and the **.NET Framework Class Library (FCL)**, supported by development tools like **Visual Studio**.

It follows a **multi-layered architecture**, where each layer has a distinct responsibility:

1. **Language Layer**
2. **Library Layer (Base Class Library)**
3. **Runtime Layer (CLR)**
4. **Application Layer**

### 1. Language Layer

* .NET supports multiple programming languages such as **C#**, **VB.NET**, and **F#**.
* All these languages are compiled into a common intermediate language (**CIL** or **MSIL**).
* The **Common Language Specification (CLS)** ensures that all .NET languages can interact seamlessly.

**Purpose:**
To provide language independence and enable developers to choose the language they prefer without compatibility issues.

### 2. Library Layer (Framework Class Library - FCL)

* The **FCL** (also called the Base Class Library or BCL) is a comprehensive collection of reusable classes, interfaces, and value types.
* It provides APIs for file I/O, database access, XML manipulation, networking, collections, and user interfaces.
* Organized into namespaces such as `System`, `System.Data`, `System.IO`, `System.Net`, and others.

**Purpose:**
To reduce development effort by providing prebuilt and tested components.

### 3. Runtime Layer (Common Language Runtime - CLR)

* The **CLR** is the core execution engine of the .NET Framework.
* It manages the execution of .NET programs, providing services like:

  * **Memory management and garbage collection**
  * **Type safety**
  * **Exception handling**
  * **Security enforcement**
  * **Just-In-Time (JIT) compilation**
* It converts Intermediate Language (IL) code into machine code specific to the target system.

**Purpose:**
To ensure managed execution, performance optimization, and system security.

### 4. Application Layer

* This is where developers create the actual software applications using the .NET infrastructure.
* It includes various application models such as:

  * **Windows Forms** (desktop applications)
  * **ASP.NET / ASP.NET Core** (web applications)
  * **WPF (Windows Presentation Foundation)** (rich desktop apps)
  * **UWP (Universal Windows Platform)** (modern Windows apps)
  * **Xamarin / MAUI** (mobile applications)

**Purpose:**
To provide a flexible environment for developing different types of applications on top of the .NET platform.

### Advantages of .NET Architecture

* **Language interoperability** — code written in different .NET languages can work together.
* **Improved performance** — JIT compilation and optimization.
* **Security** — code access security and type safety.
* **Memory management** — automatic garbage collection.
* **Scalability** — supports large enterprise-level applications.
* **Rich library support** — extensive prebuilt functionality.


--- 

# Elements of .NET Data Providers

The **elements of a .NET Data Provider** are the key components that handle data access logic. They provide functionality for connecting to a data source, executing SQL commands, reading results, and updating data.

### Main Elements of a .NET Data Provider

1. **Connection Object**

   * Responsible for establishing and managing the connection to the database.
   * Uses a connection string containing database details (server name, database name, credentials).
   * Opens and closes the connection as required.

   **Common classes:**

   * `SqlConnection` (for SQL Server)
   * `OleDbConnection` (for OLE DB data sources)
   * `OdbcConnection` (for ODBC data sources)
   * `OracleConnection` (for Oracle databases)

   **Example:**

   ```csharp
   SqlConnection conn = new SqlConnection("Data Source=Server;Initial Catalog=DB;Integrated Security=True");
   conn.Open();
   conn.Close();
   ```

---

2. **Command Object**

   * Represents a SQL query or stored procedure to be executed against the data source.
   * Executes commands and returns results depending on the query type.
   * Supports parameterized queries to prevent SQL injection.

   **Common classes:**

   * `SqlCommand`, `OleDbCommand`, `OdbcCommand`, `OracleCommand`

   **Key methods:**

   * `ExecuteReader()` — retrieves data using a DataReader.
   * `ExecuteScalar()` — retrieves a single value.
   * `ExecuteNonQuery()` — executes DML commands (INSERT, UPDATE, DELETE).

   **Example:**

   ```csharp
   SqlCommand cmd = new SqlCommand("SELECT * FROM Employees", conn);
   SqlDataReader reader = cmd.ExecuteReader();
   ```

---

3. **DataReader Object**

   * Provides fast, forward-only, read-only access to data from a database.
   * Works in **connected mode**, meaning the connection must remain open while reading.
   * Suitable for reading large amounts of data efficiently.

   **Common classes:**

   * `SqlDataReader`, `OleDbDataReader`, `OdbcDataReader`, `OracleDataReader`

   **Example:**

   ```csharp
   while (reader.Read())
   {
       Console.WriteLine(reader["EmployeeName"]);
   }
   reader.Close();
   ```

---

4. **DataAdapter Object**

   * Acts as a **bridge between the DataSet (disconnected data) and the database**.
   * Retrieves data from the database and fills the DataSet.
   * Can also update changes made in the DataSet back to the database.
   * Supports four main SQL commands: `SelectCommand`, `InsertCommand`, `UpdateCommand`, `DeleteCommand`.

   **Common classes:**

   * `SqlDataAdapter`, `OleDbDataAdapter`, `OdbcDataAdapter`, `OracleDataAdapter`

   **Example:**

   ```csharp
   SqlDataAdapter adapter = new SqlDataAdapter("SELECT * FROM Employees", conn);
   DataSet ds = new DataSet();
   adapter.Fill(ds, "Employees");
   ```

---

5. **DataSet Object**

   * Represents an **in-memory cache** of data that can contain multiple tables and relationships.
   * Works in **disconnected mode**, meaning the database connection can be closed after data retrieval.
   * Allows local data manipulation without affecting the actual database until explicitly updated.

   **Namespace:** `System.Data`

   **Example:**

   ```csharp
   foreach (DataRow row in ds.Tables["Employees"].Rows)
   {
       Console.WriteLine(row["EmployeeName"]);
   }
   ```

---
### Example Workflow

1. Create a **Connection** to the database.
2. Define and execute a **Command**.
3. Retrieve results using a **DataReader** or fill a **DataSet** via a **DataAdapter**.
4. Optionally modify data in the **DataSet** and update back to the database.
5. Close the **Connection**.

--- 

# Introduction to SQL Server

**SQL Server** is a **Relational Database Management System (RDBMS)** developed by **Microsoft**.
It is designed to store, manage, and retrieve data efficiently and securely for applications ranging from small desktop programs to large-scale enterprise systems.

SQL Server supports **Structured Query Language (SQL)** as its primary query language and integrates seamlessly with the **.NET Framework** and **ADO.NET** for data-driven applications.

### Features of SQL Server

1. **Relational Database Model**
   * Data is stored in tables (rows and columns).
   * Relationships between tables are established using keys (primary and foreign keys).

2. **High Performance and Scalability**
   * Optimized query execution engine.
   * Supports indexing, partitioning, and caching for faster data access.

3. **Security Features**
   * Includes authentication, authorization, encryption, and role-based access control.

4. **Data Integrity**
   * Enforces constraints (primary key, foreign key, unique, check, and default) to maintain data accuracy.

5. **Stored Procedures and Triggers**
   * Supports programmable logic within the database for automation and consistency.

6. **Transaction Management**
   * Supports ACID properties (Atomicity, Consistency, Isolation, Durability).
   * Enables rollback and commit operations to ensure data reliability.

7. **Integration with .NET**
   * ADO.NET provides direct connectivity and command execution against SQL Server databases.

8. **Backup and Recovery**
   * Includes robust tools for database backup, restore, and disaster recovery.

9. **Management Tools**
   * SQL Server Management Studio (SSMS) provides a graphical interface for database creation, query execution, and server management.

### SQL Server Architecture

SQL Server consists of several key components that work together to manage data:

1. **Database Engine**
   * Core service that handles data storage, processing, and security.
   * Includes the **Relational Engine** (query processing) and **Storage Engine** (data access and management).

2. **SQL Server Agent**
   * Automates administrative tasks such as backups, jobs, and scheduled scripts.

3. **SQL Server Management Studio (SSMS)**
   * Graphical interface for writing queries, managing databases, and configuring servers.

4. **SQL Server Services**
   * Includes the **SQL Server Service**, **SQL Browser**, and **SQL Agent Service**, each responsible for different operational roles.

5. **Transaction Log**
   * Maintains a record of all changes for recovery and rollback purposes.

6. **Master, Model, and Temp Databases**

   * **Master:** Contains system-level information (logins, configurations).
   * **Model:** Template for creating new databases.
   * **TempDB:** Temporary workspace for query execution and sorting operations.

### Connecting SQL Server with .NET

To connect a .NET application with SQL Server, ADO.NET provides classes under the `System.Data.SqlClient` namespace.

**Example:**

```csharp
using System;
using System.Data.SqlClient;

class Program
{
    static void Main()
    {
        string connectionString = "Data Source=ServerName;Initial Catalog=EmployeeDB;Integrated Security=True";
        SqlConnection conn = new SqlConnection(connectionString);

        SqlCommand cmd = new SqlCommand("SELECT * FROM Employees", conn);
        conn.Open();

        SqlDataReader reader = cmd.ExecuteReader();
        while (reader.Read())
        {
            Console.WriteLine(reader["EmpName"]);
        }

        reader.Close();
        conn.Close();
    }
}
```

### Advantages of SQL Server

* Strong integration with .NET and Windows ecosystem.
* High security and data protection mechanisms.
* Reliable transaction support and recovery features.
* Supports distributed and cloud-based databases.
* Scalable for large enterprise applications.


--- 
# Namespaces in ADO.NET

ADO.NET (ActiveX Data Objects for .NET) is a **data access technology** provided by Microsoft as part of the .NET Framework.
It allows .NET applications to **connect to databases**, **retrieve**, **manipulate**, and **update** data in a **disconnected** and **scalable** manner.

To achieve this, ADO.NET provides a **set of namespaces**, each containing **classes, interfaces, and enumerations** that handle different aspects of database interaction such as connection management, data retrieval, command execution, and transaction handling.

### Key Namespaces in ADO.NET

#### 1. **System.Data**

* The **base namespace** for all ADO.NET classes.
* Contains common classes used across different data providers.
* Defines core components like `DataSet`, `DataTable`, `DataRow`, and `DataRelation`.

**Common Classes:**

| Class          | Description                                                                          |
| -------------- | ------------------------------------------------------------------------------------ |
| `DataSet`      | In-memory representation of data that can contain multiple tables and relationships. |
| `DataTable`    | Represents a single table of data.                                                   |
| `DataRow`      | Represents a single row within a DataTable.                                          |
| `DataColumn`   | Defines the schema of a column in a table.                                           |
| `DataRelation` | Defines a parent-child relationship between two tables.                              |
| `Constraint`   | Defines rules for maintaining data integrity.                                        |

**Example:**

```csharp
using System.Data;

DataSet ds = new DataSet("EmployeeDB");
DataTable dt = new DataTable("Employees");
ds.Tables.Add(dt);
```

#### 2. **System.Data.SqlClient**

* Used specifically for **Microsoft SQL Server**.
* Contains optimized classes for connecting and executing SQL commands on SQL Server databases.

**Common Classes:**

| Class            | Description                                                     |
| ---------------- | --------------------------------------------------------------- |
| `SqlConnection`  | Establishes a connection to a SQL Server database.              |
| `SqlCommand`     | Executes SQL queries or stored procedures.                      |
| `SqlDataReader`  | Provides forward-only, read-only access to data.                |
| `SqlDataAdapter` | Acts as a bridge between a DataSet and the database.            |
| `SqlParameter`   | Represents parameters used in SQL queries or stored procedures. |

**Example:**

```csharp
using System.Data.SqlClient;

SqlConnection conn = new SqlConnection("Data Source=Server;Initial Catalog=DB;Integrated Security=True");
conn.Open();
SqlCommand cmd = new SqlCommand("SELECT * FROM Employees", conn);
SqlDataReader reader = cmd.ExecuteReader();
conn.Close();
```

#### 3. **System.Data.OleDb**

* Used for connecting to **OLE DB data sources** (e.g., Access, Excel, or older databases).
* Provider-independent approach for databases that support OLE DB drivers.

**Common Classes:**

| Class              | Description                                                       |
| ------------------ | ----------------------------------------------------------------- |
| `OleDbConnection`  | Manages connection to an OLE DB data source.                      |
| `OleDbCommand`     | Executes SQL statements or stored procedures.                     |
| `OleDbDataReader`  | Reads data from an OLE DB data source.                            |
| `OleDbDataAdapter` | Facilitates data transfer between an OLE DB source and a DataSet. |

**Example:**

```csharp
using System.Data.OleDb;

OleDbConnection conn = new OleDbConnection("Provider=Microsoft.ACE.OLEDB.12.0;Data Source=Database.accdb;");
conn.Open();
OleDbCommand cmd = new OleDbCommand("SELECT * FROM Students", conn);
OleDbDataReader reader = cmd.ExecuteReader();
conn.Close();
```

#### 4. **System.Data.Odbc**

* Used to connect to databases via **ODBC (Open Database Connectivity)** drivers.
* Useful for accessing non-SQL Server databases such as MySQL, Oracle, or PostgreSQL.

**Common Classes:**

| Class             | Description                                      |
| ----------------- | ------------------------------------------------ |
| `OdbcConnection`  | Manages connection to an ODBC data source.       |
| `OdbcCommand`     | Executes SQL queries via ODBC.                   |
| `OdbcDataReader`  | Reads data returned from an ODBC command.        |
| `OdbcDataAdapter` | Transfers data between a database and a DataSet. |

**Example:**

```csharp
using System.Data.Odbc;

OdbcConnection conn = new OdbcConnection("DSN=MySQLDataSource;UID=root;PWD=password;");
conn.Open();
OdbcCommand cmd = new OdbcCommand("SELECT * FROM Products", conn);
OdbcDataReader reader = cmd.ExecuteReader();
conn.Close();
```

#### 5. **System.Data.Common**

* Provides **base classes and interfaces** for creating **provider-independent** ADO.NET code.
* Helps in writing generic database code that can work with any data provider (SQL, OLEDB, ODBC, etc.).

**Common Classes:**

| Class               | Description                                           |
| ------------------- | ----------------------------------------------------- |
| `DbConnection`      | Abstract base class for all connection objects.       |
| `DbCommand`         | Abstract class for all database commands.             |
| `DbDataReader`      | Provides a generic way to read data.                  |
| `DbDataAdapter`     | Provides a base adapter for data transfer.            |
| `DbProviderFactory` | Used to create provider-specific objects dynamically. |

**Example:**

```csharp
using System.Data.Common;

DbProviderFactory factory = DbProviderFactories.GetFactory("System.Data.SqlClient");
using (DbConnection conn = factory.CreateConnection())
{
    conn.ConnectionString = "Data Source=Server;Initial Catalog=DB;Integrated Security=True";
    conn.Open();
}
```

#### 6. **System.Data.DataSetExtensions**

* Provides **LINQ to DataSet** features.
* Enables querying `DataSet` or `DataTable` objects using **LINQ (Language Integrated Query)**.

**Example:**

```csharp
using System.Data;
using System.Data.DataSetExtensions;
using System.Linq;

var result = from row in dataTable.AsEnumerable()
             where row.Field<int>("Salary") > 50000
             select row;
```

#### 7. **System.Data.Entity** *(for Entity Framework)*

* Used when working with **Entity Framework (EF)**, an ORM (Object Relational Mapper).
* Simplifies data access by mapping database tables to .NET objects.

----
----
----
----
----
----
----
----
----
----
----

``` 
IMPORTANT NOTES ONLI: 
```


# Connection Class — How to Connect a .NET Application to a Database

In ADO.NET, the **Connection class** is the foundational component used to **establish a link between a .NET application and a data source** (such as SQL Server, Oracle, MySQL, or Access).  
Without a valid connection, no database operations—like querying, updating, or inserting—can be performed.

Each database provider (like SQL Server or OLE DB) has its **own Connection class** inside its respective namespace.

### Purpose of the Connection Class

The **Connection class**:

- Opens and maintains a session with the database.
- Manages connection state (open, closed, broken).
- Provides access to database properties such as connection string, timeout, and database name.
- Works with other ADO.NET objects (`Command`, `DataReader`, `Transaction`) to perform operations.

---

### Common Connection Classes

| Database                                  | Namespace                  | Connection Class   |
| ----------------------------------------- | -------------------------- | ------------------ |
| Microsoft SQL Server                      | `System.Data.SqlClient`    | `SqlConnection`    |
| OLE DB data sources (e.g., Access, Excel) | `System.Data.OleDb`        | `OleDbConnection`  |
| ODBC data sources                         | `System.Data.Odbc`         | `OdbcConnection`   |
| Oracle databases                          | `System.Data.OracleClient` | `OracleConnection` |

---

### Key Properties of the Connection Class

| Property              | Description                                                                                         |
| --------------------- | --------------------------------------------------------------------------------------------------- |
| **ConnectionString**  | Specifies the details needed to connect to the database (server, database name, credentials, etc.). |
| **State**             | Shows the current state of the connection (`Open`, `Closed`, `Connecting`, etc.).                   |
| **Database**          | The name of the database to which the connection is made.                                           |
| **DataSource**        | The name of the server or file used as a data source.                                               |
| **ConnectionTimeout** | Time (in seconds) to wait while trying to establish a connection before throwing an error.          |

---

### Key Methods

| Method                            | Description                                          |
| --------------------------------- | ---------------------------------------------------- |
| **Open()**                        | Opens the connection to the data source.             |
| **Close()**                       | Closes the connection to free resources.             |
| **Dispose()**                     | Releases all resources used by the connection.       |
| **ChangeDatabase(string dbName)** | Switches the active database on the same connection. |

---

### Steps to Connect a .NET Application to a Database

#### 1. Include the Required Namespace

Import the appropriate ADO.NET namespace depending on the database:

```csharp
using System.Data.SqlClient;   // For SQL Server
```

#### 2. Define the Connection String

A **connection string** specifies all the information required to connect to a database.

**Example (SQL Server):**

```csharp
string connectionString = "Data Source=SERVER_NAME;Initial Catalog=DatabaseName;Integrated Security=True";
```

- `Data Source` → Name of the SQL Server (or `localhost` for local server).
    
- `Initial Catalog` → Database name.
    
- `Integrated Security=True` → Uses Windows authentication (no need for username/password).
    

Alternatively, for SQL authentication:

```csharp
string connectionString = "Data Source=SERVER_NAME;Initial Catalog=DatabaseName;User ID=sa;Password=yourpassword";
```

#### 3. Create a Connection Object

```csharp
SqlConnection conn = new SqlConnection(connectionString);
```

#### 4. Open the Connection

```csharp
conn.Open();
Console.WriteLine("Connection Opened Successfully");
```

#### 5. Perform Database Operations

Execute queries or commands using `SqlCommand`, `SqlDataAdapter`, etc.

#### 6. Close the Connection

Always close the connection after use:

```csharp
conn.Close();
Console.WriteLine("Connection Closed");
```

### Complete Example

```csharp
using System;
using System.Data.SqlClient;

class DBConnectionExample
{
    static void Main()
    {
        string connectionString = "Data Source=localhost;Initial Catalog=EmployeeDB;Integrated Security=True";

        // Step 1: Create Connection
        SqlConnection conn = new SqlConnection(connectionString);

        try
        {
            // Step 2: Open Connection
            conn.Open();
            Console.WriteLine("Connected to the database successfully.");

            // Step 3: Use the Connection
            SqlCommand cmd = new SqlCommand("SELECT * FROM Employees", conn);
            SqlDataReader reader = cmd.ExecuteReader();

            while (reader.Read())
            {
                Console.WriteLine(reader["Name"]);
            }
            reader.Close();
        }
        catch (SqlException ex)
        {
            Console.WriteLine("Connection failed: " + ex.Message);
        }
        finally
        {
            // Step 4: Close Connection
            conn.Close();
        }
    }
}
```

### Best Practices

1. **Always Close Connections**  
   Connections consume system resources; close them using `Close()` or `Dispose()` when done.  

2. **Use Connection Pooling**  
   ADO.NET automatically manages connection pooling to reuse active connections, improving performance.
   
3. **Use Try-Catch Blocks**  
   Handle exceptions gracefully to avoid crashes when connections fail.
   
4. **Store Connection Strings Securely**  
   Keep them in `app.config` or `web.config` files, not hardcoded in the code.

# Command Class — Used for Executing SQL Commands

In ADO.NET, the **Command class** is used to **execute SQL statements, stored procedures, or functions** against a database.
It acts as a communication channel between the **application** and the **database**, sending commands and receiving results.

The Command object works **after establishing a connection** using the Connection class.

| Provider   | Namespace                  | Command Class   |
| ---------- | -------------------------- | --------------- |
| SQL Server | `System.Data.SqlClient`    | `SqlCommand`    |
| OLE DB     | `System.Data.OleDb`        | `OleDbCommand`  |
| ODBC       | `System.Data.Odbc`         | `OdbcCommand`   |
| Oracle     | `System.Data.OracleClient` | `OracleCommand` |

### Key Properties of the Command Class

| Property           | Description                                                                     |
| ------------------ | ------------------------------------------------------------------------------- |
| **CommandText**    | Contains the SQL query or stored procedure name to execute.                     |
| **CommandType**    | Defines whether the command is a SQL text, stored procedure, or table name.     |
| **Connection**     | Specifies the active database connection to use.                                |
| **Parameters**     | Collection of parameters used with parameterized queries or stored procedures.  |
| **Transaction**    | Associates the command with a database transaction.                             |
| **CommandTimeout** | Maximum time (in seconds) to wait for the command to execute before timing out. |

---

### CommandType Enumeration

The **CommandType** property defines the type of command being executed.

| CommandType       | Description                                                  |
| ----------------- | ------------------------------------------------------------ |
| `Text`            | Used for raw SQL statements. (Default)                       |
| `StoredProcedure` | Used for executing stored procedures.                        |
| `TableDirect`     | Used to access an entire table directly (mainly for OLE DB). |

---

### Key Methods of Command Class

| Method                | Description                                                                                                                            |
| --------------------- | -------------------------------------------------------------------------------------------------------------------------------------- |
| **ExecuteReader()**   | Executes commands that return rows (e.g., `SELECT`). Returns a `DataReader`.                                                           |
| **ExecuteNonQuery()** | Executes commands that change data but do not return rows (e.g., `INSERT`, `UPDATE`, `DELETE`). Returns the number of rows affected.   |
| **ExecuteScalar()**   | Executes a query and returns a single value (first column of the first row). Useful for aggregate functions like `COUNT()` or `SUM()`. |
| **Prepare()**         | Prepares the command for repeated execution, improving performance.                                                                    |

---

### Steps to Use the Command Class

1. **Establish a Connection**

   ```csharp
   SqlConnection conn = new SqlConnection("Data Source=localhost;Initial Catalog=EmployeeDB;Integrated Security=True");
   ```

2. **Create a Command Object**

   ```csharp
   SqlCommand cmd = new SqlCommand();
   cmd.Connection = conn;
   cmd.CommandText = "SELECT * FROM Employees";
   cmd.CommandType = CommandType.Text;
   ```

3. **Open the Connection**

   ```csharp
   conn.Open();
   ```

4. **Execute the Command**
   Depending on the requirement:

   * For reading data → `ExecuteReader()`
   * For data modification → `ExecuteNonQuery()`
   * For a single value → `ExecuteScalar()`

5. **Close the Connection**

   ```csharp
   conn.Close();
   ```

---

### Examples

#### 1. Executing a SELECT Query (Using `ExecuteReader()`)

```csharp
using System;
using System.Data.SqlClient;

class SelectExample
{
    static void Main()
    {
        string cs = "Data Source=localhost;Initial Catalog=EmployeeDB;Integrated Security=True";
        using (SqlConnection conn = new SqlConnection(cs))
        {
            SqlCommand cmd = new SqlCommand("SELECT Name, Salary FROM Employees", conn);
            conn.Open();

            SqlDataReader reader = cmd.ExecuteReader();
            while (reader.Read())
            {
                Console.WriteLine(reader["Name"] + " - " + reader["Salary"]);
            }

            reader.Close();
        }
    }
}
```

# Performing CRUD Operations — Connected and Disconnected Versions


In ADO.NET, **CRUD** stands for the four basic operations performed on a database:

* **C** – Create (Insert)
* **R** – Read (Select)
* **U** – Update
* **D** – Delete

These operations can be performed in **two ways**:

1. **Connected Architecture** — Uses `Connection`, `Command`, and `DataReader` classes; keeps the connection **open** throughout.
2. **Disconnected Architecture** — Uses `DataSet` and `DataAdapter` classes; connection is **opened only briefly** and data is worked with **offline**.

---

## 1. Connected Architecture (Using `SqlCommand` and `SqlDataReader`)

In the **connected model**, the database connection remains **active** while commands are executed.
This approach is best for **real-time** and **read-only** operations.

### Key Classes

* `SqlConnection`
* `SqlCommand`
* `SqlDataReader`

### A. CREATE (INSERT)

```csharp
using System.Data.SqlClient;

string cs = "Data Source=localhost;Initial Catalog=EmployeeDB;Integrated Security=True";

using (SqlConnection conn = new SqlConnection(cs))
{
    string query = "INSERT INTO Employees(Name, Salary) VALUES(@Name, @Salary)";
    SqlCommand cmd = new SqlCommand(query, conn);
    cmd.Parameters.AddWithValue("@Name", "John");
    cmd.Parameters.AddWithValue("@Salary", 55000);

    conn.Open();
    int rows = cmd.ExecuteNonQuery();
    Console.WriteLine(rows + " row(s) inserted.");
}
```

### B. READ (SELECT)

```csharp
using System.Data.SqlClient;

string cs = "Data Source=localhost;Initial Catalog=EmployeeDB;Integrated Security=True";

using (SqlConnection conn = new SqlConnection(cs))
{
    SqlCommand cmd = new SqlCommand("SELECT * FROM Employees", conn);
    conn.Open();

    SqlDataReader reader = cmd.ExecuteReader();
    while (reader.Read())
    {
        Console.WriteLine(reader["Name"] + " - " + reader["Salary"]);
    }
    reader.Close();
}
```

### C. UPDATE

```csharp
using System.Data.SqlClient;

string cs = "Data Source=localhost;Initial Catalog=EmployeeDB;Integrated Security=True";

using (SqlConnection conn = new SqlConnection(cs))
{
    string query = "UPDATE Employees SET Salary = @Salary WHERE Name = @Name";
    SqlCommand cmd = new SqlCommand(query, conn);
    cmd.Parameters.AddWithValue("@Name", "John");
    cmd.Parameters.AddWithValue("@Salary", 60000);

    conn.Open();
    int rows = cmd.ExecuteNonQuery();
    Console.WriteLine(rows + " row(s) updated.");
}
```

### D. DELETE

```csharp
using System.Data.SqlClient;

string cs = "Data Source=localhost;Initial Catalog=EmployeeDB;Integrated Security=True";

using (SqlConnection conn = new SqlConnection(cs))
{
    SqlCommand cmd = new SqlCommand("DELETE FROM Employees WHERE Name=@Name", conn);
    cmd.Parameters.AddWithValue("@Name", "John");

    conn.Open();
    int rows = cmd.ExecuteNonQuery();
    Console.WriteLine(rows + " row(s) deleted.");
}
```

### Advantages of Connected Architecture

* Real-time interaction with the database.
* Less memory usage (no local caching).
* Faster for short-lived operations.

### Disadvantages

* Requires continuous network connection.
* Not suitable for large datasets or offline access.


### Advantages of Disconnected Architecture

* Reduces database load — connection stays open only briefly.
* Enables **offline manipulation** of data.
* Can handle **multiple tables and relationships** at once using `DataSet`.
* Useful in distributed applications (like web apps).

### Disadvantages

* Slightly higher memory usage.
* Data can become **out of sync** if the source changes after fetching.

--- 
# DataReader Class

The **`DataReader`** class in ADO.NET is used to **read data from a database in a forward-only, read-only manner**.
It belongs to the **connected architecture**, meaning the database connection remains **open** while reading data.

It provides a **fast and efficient** way to retrieve large volumes of data because it does **not cache** results in memory.

### Key Features of DataReader

* Provides **forward-only** and **read-only** access to data.
* Uses **connected architecture** — requires an active connection.
* Retrieves data **sequentially**, improving performance.
* Ideal for **reading large result sets quickly**.
* **Lightweight** compared to `DataSet` or `DataTable`.
* Data is accessed using **column names** or **ordinal indexes**.

### Important Classes

Depending on the database provider, ADO.NET provides different DataReader classes:

| Provider   | DataReader Class   | Namespace                  |
| ---------- | ------------------ | -------------------------- |
| SQL Server | `SqlDataReader`    | `System.Data.SqlClient`    |
| OLE DB     | `OleDbDataReader`  | `System.Data.OleDb`        |
| ODBC       | `OdbcDataReader`   | `System.Data.Odbc`         |
| Oracle     | `OracleDataReader` | `System.Data.OracleClient` |

### Syntax

```csharp
SqlDataReader reader = command.ExecuteReader();
```

---

### Example: Using `SqlDataReader` to Retrieve Data

```csharp
using System;
using System.Data.SqlClient;

class Program
{
    static void Main()
    {
        string cs = "Data Source=localhost;Initial Catalog=EmployeeDB;Integrated Security=True";

        using (SqlConnection conn = new SqlConnection(cs))
        {
            string query = "SELECT Id, Name, Salary FROM Employees";
            SqlCommand cmd = new SqlCommand(query, conn);

            conn.Open();
            SqlDataReader reader = cmd.ExecuteReader();

            while (reader.Read())
            {
                Console.WriteLine(reader["Id"] + " - " + reader["Name"] + " - " + reader["Salary"]);
            }

            reader.Close();
        }
    }
}
```

# i'd prolly not study this unit for exam : (

