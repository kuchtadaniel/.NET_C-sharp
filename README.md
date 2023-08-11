# Comprehensive Guide to Using Dapper with .NET C#

Dapper is a lightweight Object-Relational Mapping (ORM) library for .NET, designed to make database interactions faster and more efficient while maintaining simplicity. This guide provides a step-by-step tutorial to learn everything about using Dapper with .NET C# for database access.

## Table of Contents
1. [Introduction to Dapper](#introduction-to-dapper)
2. [Setting Up Your Project](#setting-up-your-project)
3. [Basic CRUD Operations](#basic-crud-operations)
4. [Advanced Querying](#advanced-querying)
5. [Mapping Relationships](#mapping-relationships)
6. [Transactions and Bulk Operations](#transactions-and-bulk-operations)
7. [Performance Optimization](#performance-optimization)
8. [Handling Stored Procedures](#handling-stored-procedures)
9. [Async Programming with Dapper](#async-programming-with-dapper)
10. [Best Practices and Tips](#best-practices-and-tips)
11. [Additional Resources](#additional-resources)

## 1. Introduction to Dapper
Dapper is a micro-ORM that works with various database providers. It is well-known for its performance due to its lightweight design and raw SQL execution capabilities. It simplifies the process of querying a database while providing control over the SQL statements being executed.

### 2. Setting Up Your Project
- Create a new .NET C# project in your preferred development environment.
- Install the Dapper package using NuGet Package Manager:
  ```bash
  Install-Package Dapper
  ```

## 3. Basic CRUD Operations
### 3.1 Connecting to the Database

using System.Data.SqlClient;
using Dapper;

string connectionString = "your_connection_string_here";
SqlConnection connection = new SqlConnection(connectionString);


### 3.2 Inserting Data
```csharp
var newProduct = new Product { Name = "Sample Product", Price = 9.99 };
string insertQuery = "INSERT INTO Products (Name, Price) VALUES (@Name, @Price)";
connection.Execute(insertQuery, newProduct);
```

### 3.3 Querying Data

string selectQuery = "SELECT * FROM Products";
List<Product> products = connection.Query<Product>(selectQuery).ToList();

 **[⬆ Back to Top](#table-of-contents)**

### 3.4 Updating Data
```csharp
string updateQuery = "UPDATE Products SET Price = @Price WHERE Id = @Id";
connection.Execute(updateQuery, new { Price = 14.99, Id = 1 });
```

### 3.5 Deleting Data
```csharp
string deleteQuery = "DELETE FROM Products WHERE Id = @Id";
connection.Execute(deleteQuery, new { Id = 1 });
```

## 4. Advanced Querying
### 4.1 Parameterized Queries
```csharp
string query = "SELECT * FROM Products WHERE Price > @Price";
List<Product> expensiveProducts = connection.Query<Product>(query, new { Price = 10 }).ToList();
```

### 4.2 Query Multiple Result Sets
```csharp
string multiQuery = "SELECT * FROM Customers; SELECT * FROM Orders;";
using (var multiResult = connection.QueryMultiple(multiQuery))
{
    List<Customer> customers = multiResult.Read<Customer>().ToList();
    List<Order> orders = multiResult.Read<Order>().ToList();
}
```

## 5. Mapping Relationships
Dapper supports one-to-one and one-to-many relationships using the `Query` and `Query` methods respectively.

## 6. Transactions and Bulk Operations
```csharp
using (var transaction = connection.BeginTransaction())
{
    try
    {
        // Perform multiple operations here
        transaction.Commit();
    }
    catch
    {
        transaction.Rollback();
    }
}
```

## 7. Performance Optimization
- Use async methods for asynchronous database operations.
- Enable query caching for frequently used queries.
- Pay attention to the performance impact of loading related entities.

## 8. Handling Stored Procedures
```csharp
string spName = "InsertProduct";
var parameters = new { Name = "New Product", Price = 19.99 };
connection.Execute(spName, parameters, commandType: CommandType.StoredProcedure);
```

## 9. Async Programming with Dapper
Dapper provides async methods to perform database operations asynchronously. Use `ExecuteAsync`, `QueryAsync`, and `QueryMultipleAsync` for asynchronous programming.

## 10. Best Practices and Tips
- Keep your SQL queries maintainable and organized.
- Use parameterized queries to prevent SQL injection.
- Consider separating database access logic from business logic using repositories or services.

## 11. Additional Resources
- Dapper GitHub Repository: [https://github.com/DapperLib/Dapper](https://github.com/DapperLib/Dapper)
- Dapper Documentation: [https://dapper-tutorial.net/dapper](https://dapper-tutorial.net/dapper)
- Dapper Performance Comparison: [https://dapper-tutorial.net/performance](https://dapper-tutorial.net/performance)

This comprehensive guide covers the basics of Dapper and provides insights into advanced topics. Remember that practice is key to mastering any technology, so make sure to experiment with various scenarios and use cases to solidify your understanding of Dapper in .NET C#. Happy coding!
```

You can copy and paste this content into your `README.md` file on GitHub. Make sure to replace placeholders like `your_connection_string_here` with your actual database connection string, and adapt the code examples as needed for your project.
