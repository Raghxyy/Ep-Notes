# Enterprise Programming

- **Pre-requisites:** HTML, CSS, JS, XML, Bootstrap
- **Outcome:**
  1. Build web application
  2. RedHat certification

## CO-1 JDBC (Java Database Connectivity)

### Introduction

- JDBC stands for Java Database Connectivity.
- JDBC is a Java API which allows Java applications to interact with Database.

- Note:
  - Java API: Java API consists of many packages where every package consists of many classes and interfaces which helps Java application to interact with database.
  - Package -> java.sql.\*;

### Why JDBC?

- JDBC is a fundamental tool for all java developers to interact with database.
- The reasons why JDBC is popular and most widely used are:

  1.  Its platform independent
  2.  Versatility :- It states that JDBC is used to connect with several databases and not just a single one.

  ```
           with help of ODBC Drivers
  Java app -------------------------  Database (Oracle, MySQL)

           with help of JDBC Drivers
  Java app ------------------------- Any Database

  ```

- Note:
  - Use-cases where JDBC is used nowadays:
    1. Web applications
    2. Enterprise application
    3. Desktop applications

### JDBC Drivers

- JDBC Drivers are critical components that enables java app to communicate/ interact with database.
- There are 4 types of JDBC drivers:
  1. **Type-1 Driver**
     - It is a.k.a. "ODBC-JDBC Drivers"
     - It is useful to connect databases where only ODBC drivers are available
  2. **Type-2 Driver**
     - It is a.k.a. "Native API Drivers"
     - It is suitable for applications where performance is critical.
  3. **Type-3 Driver**
     - It is a.k.a. "Network Protocol Drivers"
     - It is suitable for Network environment where the client doesn't know the requirements of the database.
  4. **Type-4 Driver**
     - It is a.k.a. "Thin Drivers"
     - It is commonly used in all modern applications nowadays due to following reasons:
       1. Performance
       2. Efficiency
       3. Platform independent
       4. Ease of use

### JDBC steps to connect to a databse

_There are 7 steps to connect a java application with a database using JDBC drivers._

1. Import the package `java.sql.*`
2. Load Drivers (Type-4)
3. Connection establishment
4. Create Statement
5. Create an object of interface `java.sql.ResultSet`
6. Execute Queries
7. Close connection.

- Example:

  1. Importing the package:
     `import java.sql.*`
  2. Load drivers using
     - Using Driver (`interface`) object
     ```
     Driver drv = new <driverclass-path>;
     DriverManager.registerDriver(drv);
     ```
     - Using `Class.forName()` method: `forName("<driverclass-path>")`
  3. Connection Establishement

  ```
  Connection conn = DriverManager.getConnection("database-path","username","password");
  ```

  4. Create statement

  ```
  Statement st = conn.createStatement();
  ```

  5. Create an object of ResultSet

  ```
  ResultSet rs = st.executeQuery("<only SELECT queries>");
  ```

  6. Execute Queries

  ```
  st.executeUpdate("<Any query other than SELECT>")
  ```

  7. Close connection `conn.close()`

- Note:
  - To connect to a oracle database:
    - DriverClassPath: `oracle.jdbc.driver.OracleDriver`
    - ConnectionURL: `jdbc:oracle:thin:@localhost:1521:xe`
    - username: `<username>`
    - password: `<passsword`
  - To connect to a MySQL database:
    - DriverClassPath: `com.mysql.jdbc.Driver`
    - ConnectionURL: `jdbc:mysql://localhost:3306/<databaseName>`
    - username: `<username>`
    - password: `<password>`

### JDBC Classes

1. DriverManager

   - It acts as an interface between user and database.
   - The methods in this class are

     1. registerDriver()
        - To load the drivers
        - Ex: `Driver drv = new driverclass-path(); DriverManager.registerDriver(drv);`
     2. deregisterDriver()

        - To unload the drivers which were recently loaded.
        - Ex: `DriverManager.deregisterDriver( );`

     3. getConnection()
        - To establish connection with a database
        - Ex: `Connection conn = DriverManager.getConnection("jdbc:mysql://localhost:3306/<dbName>","uname","pwd");`

2. Blob
   - It is used to store and retrieve image in a database(table).
   - To store:
     - className: `FileInputStream`
     - mathod: `setBinaryStream()`
   - To retrieve:
     - className: `FileOutputStream`
     - method: `getBytes()`
3. Clob
   - It is used to store and retrieve files in a database(table).
   - To store:
     - className: `FileReader`
     - method: `setCharacterStream()`
   - To retrieve:
     - className: `FileWriter`
     - method: `getCharacterStream()`

### JDBC Interfaces

1. Driver
   - It helps us to define the drivers that we want to load.
   - Ex: `Driver drv = new driverclass-path`
2. Connection
   - It acts as a session between java application and database.
   - Ex: `Connection conn = DriverManager.getConnection("url","uname","pwd"); conn.close()`
   - **Methods:**
     1. `createStatement()` : `Statement st = conn.createStatement();`
     2. `setAutoCommit()` : `st.setAutoCommit();`
     3. `commit()` : `st.commit();`
     4. `rollback()` : `st.rollback()`
     5. `close()`: `conn.close();`
3. Statement
   - It provides methods to execute queries on a database.
   - **Methods:**
     1. `executeQuery()` : only for `SELECT` queries.
        - `ResultSet rs = st.executeQuery(selectQuery)`
     2. `executeUpdate()` : for queries other than `SELECT`
        - `st.executeUpdate(query)`
4. PreparedStatement
   - It is a sub interface of `Statement` interface.
   - **Methods:**
     1. `setInt()`
     2. `setString()`
     3. `setFloat()`
     4. `setDouble()`
     5. All other methods from `Statement` interface.

- Example:
  ```java
  PreparedStatement ps = conn.prepareStatement("query(?, ?, ..., ?)");
  ps.setInt(columnNumber, someInt);
  ps.setString(columnNumber, someString);
  ps.setFloat(columnNumber, someFloatValue);
  ps.setDouble(columnNumber, someDouble);
  ```

5. ResultSet

   - It is used to retrieve data from a database after executing a query.
   - It represents a set of rows returned by a database query and maintains a cursor pointing out to the current row.
   - **Methods:**

     1. `next()`
     2. `previous()`
     3. `first()`
     4. `last()`
     5. `getInt()`
     6. `getFloat()`
     7. `getDouble()`

   - Ex:

   ```
   ResultSet rs = stmt.executeQuery("SELECT * FROM db;");
   rs.next();
   rs.previous();
   rs.first();
   rs.last();
   rs.getInt(cloumnNumber);
   rs.getFloat(cloumnNumber);
   rs.getDouble(cloumnNumber);
   ```

6. ResultSetMetaData
   - MetaData refers to data within existing data i.e., we can get further info or data from existing/ available data.
   - `ResultSetMetaData rsmd = rs.getMetaData();`
   - **Methods:**
     1. `getColumnCount()` : `rsmd.getColumnCount()`
     2. `getColumnName()` : `rsmd.getColumnName()`
     3. `getColumnTypeName()` : `rsmd.getColumnTypeName()`
     4. `getTableName()` : `rsmd.getTableName()`
7. DatabaseMetaData
   - It provides more information about the database.
   - `DatabaseMetaData dbmd = conn.getMetaData();`
   - **Methods:**
     1. `getDriverName()` : `dbmd.getDriverName()`
     2. `getDriverVersion()` : `dbmd.getDriverVersion()`
     3. `getDatabaseProductName()` : `dbmd.getDatabaseProductName()`
     4. `getDatabaseProductVersion()` : `dbmd.getDatabaseProductVersion()`\*\*\*\*
8. Callable

   - It is used to call functions or stored procedures.
   - **Methods:**
     1. `call()`
   - **Create procedure**

   ```
   CREATE OR REPLACE PROCEDURE procedure_name
   IS
   BEGIN
   QUERY;
   END procedure_name;

   ex:
   CREATE OR REPLACE PROCEDURE insertData(id IN NUMBER,name IN VARCHAR)
   IS
   INSERT INTO table_name VALUES(id,name);
   END insertData;
   ```

- Note

```

```

### JDBC Examples (Min. 10)

1. Driver object, Oracle Database

```
import java.sql.*;
class DBConnect{

  public static void main(String[] args){
    Driver drv = new oracle.jdbc.driver.OracleDriver;
    DriverManager.registerDriver(drv);

    Connection conn = DriverManager.getConnection("jdbc:oracle:thin:@localhost:1521:xe","system","gowtham");

    if(conn) System.out.println("Connection successful");
    else System.out.println("Connection failed");

    conn.close();
  }
}
```

2. Class.forName(), Oracle Database

```
import java.sql.*;
class DBConnect{
  public static void main(String[] args){

    Class.forName(oracle.jdbc.driver.OracleDriver)

    Connection conn = DriverManager.getConnection("jdbc:oracle:thin:@localhost:1521:xe","system","gowtham");

    if(conn) System.out.println("Connection successful");
    else System.out.println("Connection failed");

    conn.close();
  }
}
```

3. Driver object, MySQL Database

```
import java.sql.*;
class DBConnect{
  public static void main(String[] args){

    Driver drv = new com.mysql.cj.jdbc.Driver();
    DriverManager.registerDriver(drv);

    Connection conn = DriverManager.getConnection("jdbc:mysql://localhost:3306:<dbName>","root","gowtham");

    if(conn) System.out.println("Connection successful");
    else System.out.println("Connection failed");

    conn.close();
  }
}
```

4. Class.forName(), MySQL Database

```
import java.sql.*;
class DBConnect{
  public static void main(String[] args){

    Class.forName("com.mysql.jdbc.Driver");

    Connection conn = DriverManager.getConnection("jdbc:mysql://localhost:3306:<dbName>","root","gowtham");

    if(conn) System.out.println("Connection successful");
    else System.out.println("Connection failed");

    conn.close();
  }
}
```

5. Demonstrate DriverManager class
6. To store an image in database
7. To retrieve image from database
8. To store a file in database
9. To retreive file from database

### JDBC CRUD\*
