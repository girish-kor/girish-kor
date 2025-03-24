# JDBC Core Concepts - The 20% That Delivers 80% Understanding

## 1. What is JDBC?

JDBC (Java Database Connectivity) is a Java API that enables Java applications to interact with relational databases. It provides methods for querying and updating data, serving as a bridge between Java applications and databases.

## 2. JDBC Architecture

JDBC consists of two main components:
- **JDBC API**: Provides interfaces and classes for connecting to databases
- **JDBC Driver Manager**: Manages database-specific drivers that implement the JDBC interfaces

## 3. Key JDBC Components

```java
// The four core interfaces of JDBC
Connection      // Represents a connection to a database
Statement       // Used to execute SQL queries
ResultSet       // Contains data retrieved from a database
DriverManager   // Manages database drivers
```

## 4. Basic JDBC Workflow

Every JDBC application follows this general pattern:

```java
// 1. Register the JDBC driver
Class.forName("com.mysql.jdbc.Driver");

// 2. Open a connection
Connection conn = DriverManager.getConnection(
    "jdbc:mysql://localhost:3306/myDB", "username", "password");

// 3. Execute a query
Statement stmt = conn.createStatement();
ResultSet rs = stmt.executeQuery("SELECT * FROM employees");

// 4. Process the results
while(rs.next()) {
    String name = rs.getString("name");
    int age = rs.getInt("age");
    // Process data...
}

// 5. Clean up
rs.close();
stmt.close();
conn.close();
```

## 5. Connection URLs

JDBC uses a URL format to specify the database connection:

```
jdbc:[subprotocol]:[subname]

Common examples:
jdbc:mysql://hostname:port/database
jdbc:oracle:thin:@hostname:port:SID
jdbc:postgresql://hostname:port/database
jdbc:sqlserver://hostname:port;databaseName=database
```

## 6. Types of Statements

JDBC provides three types of statements:

```java
// 1. Statement: For simple SQL queries without parameters
Statement stmt = conn.createStatement();
ResultSet rs = stmt.executeQuery("SELECT * FROM employees");

// 2. PreparedStatement: For precompiled SQL with parameters
PreparedStatement pstmt = conn.prepareStatement("SELECT * FROM employees WHERE dept = ?");
pstmt.setString(1, "Engineering");
ResultSet rs = pstmt.executeQuery();

// 3. CallableStatement: For stored procedures
CallableStatement cstmt = conn.prepareCall("{call PROCEDURE_NAME(?, ?)}");
cstmt.setString(1, "param1");
cstmt.registerOutParameter(2, java.sql.Types.INTEGER);
cstmt.execute();
int result = cstmt.getInt(2);
```

## 7. ResultSet Processing

```java
ResultSet rs = stmt.executeQuery("SELECT * FROM employees");

// Loop through results
while(rs.next()) {
    // Access columns by name or index (1-based)
    int id = rs.getInt("id");  // or rs.getInt(1)
    String name = rs.getString("name");  // or rs.getString(2)
    
    // Check for NULL values
    String email = rs.getString("email");
    if(rs.wasNull()) {
        email = "Not available";
    }
}
```

## 8. Transaction Management

JDBC supports database transactions:

```java
try {
    // Start transaction
    conn.setAutoCommit(false);
    
    // Execute statements
    stmt1.executeUpdate("UPDATE accounts SET balance = balance - 100 WHERE id = 1");
    stmt2.executeUpdate("UPDATE accounts SET balance = balance + 100 WHERE id = 2");
    
    // Commit transaction
    conn.commit();
} catch(SQLException e) {
    // Rollback transaction on error
    conn.rollback();
    e.printStackTrace();
} finally {
    // Restore default behavior
    conn.setAutoCommit(true);
}
```

## 9. Exception Handling

JDBC operations can throw SQLException:

```java
try {
    // JDBC operations
    Statement stmt = conn.createStatement();
    ResultSet rs = stmt.executeQuery("SELECT * FROM employees");
    // Process results...
} catch(SQLException e) {
    // Handle specific SQLException
    System.out.println("SQL State: " + e.getSQLState());
    System.out.println("Error Code: " + e.getErrorCode());
    System.out.println("Message: " + e.getMessage());
    e.printStackTrace();
} finally {
    // Close resources in finally block
    try {
        if(rs != null) rs.close();
        if(stmt != null) stmt.close();
        if(conn != null) conn.close();
    } catch(SQLException e) {
        e.printStackTrace();
    }
}
```

## 10. Connection Pooling

For production applications, use connection pooling to improve performance:

```java
// Using a connection pool (example with Apache DBCP)
BasicDataSource dataSource = new BasicDataSource();
dataSource.setDriverClassName("com.mysql.jdbc.Driver");
dataSource.setUrl("jdbc:mysql://localhost:3306/myDB");
dataSource.setUsername("username");
dataSource.setPassword("password");
dataSource.setInitialSize(5);  // Initial connections in pool
dataSource.setMaxTotal(10);    // Maximum connections in pool

// Get connection from pool
Connection conn = dataSource.getConnection();
// Use connection...
// Return to pool
conn.close();  // Doesn't actually close, but returns to pool
```

## Bonus: Best Practices

1. Always close JDBC resources (ResultSet, Statement, Connection) in finally blocks
2. Use PreparedStatement instead of Statement for security (prevents SQL injection)
3. Implement connection pooling for performance
4. Use batch processing for multiple similar operations
5. Set appropriate transaction isolation levels based on your requirements
6. Use metadata to get information about database structure
7. Properly handle NULL values with wasNull() method
8. Consider using an ORM (Object-Relational Mapping) like Hibernate for complex applications
