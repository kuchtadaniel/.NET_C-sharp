# Comprehensive Guide to Using Dapper with .NET C#

Dapper is a lightweight Object-Relational Mapping (ORM) library for .NET, designed to make database interactions faster and more efficient while maintaining simplicity. This guide provides a step-by-step tutorial to learn everything about using Dapper with .NET C# for database access.

## Table of Contents
1. [Introduction to Dapper](#introduction-to-dapper)
2. [Setting Up Your Project](#setting-up-your-project)
3. [Basic CRUD Operations](#basic-crud-operations)
4. [Methods Basic CRUD Operations](#methods)
5. [Advanced Querying](#advanced-querying)
6. [Mapping Relationships](#mapping-relationships)
7. [Transactions and Bulk Operations](#transactions-and-bulk-operations)
8. [Performance Optimization](#performance-optimization)
9. [Handling Stored Procedures](#handling-stored-procedures)
10. [Async Programming with Dapper](#async-programming-with-dapper)
11. [Best Practices and Tips](#best-practices-and-tips)
12. [Additional Resources](#additional-resources)

 **[](#table-of-contents)**


1. ## Introduction to Dapper
Dapper is a micro-ORM that works with various database providers. It is well-known for its performance due to its lightweight design and raw SQL execution capabilities. It simplifies the process of querying a database while providing control over the SQL statements being executed.
 **[⬆ Back to Top](#table-of-contents)**
 
2. ## Setting Up Your Project
- Create a new .NET C# project in your preferred development environment.
- Install the Dapper package using NuGet Package Manager:
  ```bash
  Install-Package Dapper
  ```
 **[⬆ Back to Top](#table-of-contents)**
 
3. ## Basic CRUD Operations
##### 3.1 Connecting to the Database
```csharp
using System.Data.SqlClient;
using Dapper;

string connectionString = "your_connection_string_here";
SqlConnection connection = new SqlConnection(connectionString);
```

##### 3.2 Inserting Data
```csharp
var newProduct = new Product { Name = "Sample Product", Price = 9.99 };
string insertQuery = "INSERT INTO Products (Name, Price) VALUES (@Name, @Price)";
connection.Execute(insertQuery, newProduct);
```

##### 3.3 Querying Data
```csharp
string selectQuery = "SELECT * FROM Products";
List<Product> products = connection.Query<Product>(selectQuery).ToList();
//OR
IEnumerable<Product> expensiveProducts = connection.Query<Product>(query, new { Price = 10 });
```
By changing the variable type to IEnumerable<Product>, you are using a more general type that represents a sequence of Product objects. This allows for more flexibility, as you're not tied to a specific collection type like List. Keep in mind that IEnumerable is a base interface for various collections, so it might not have all the methods available that you'd find in more specific collection types like List.


##### 3.4 Updating Data
```csharp
string updateQuery = "UPDATE Products SET Price = @Price WHERE Id = @Id";
connection.Execute(updateQuery, new { Price = 14.99, Id = 1 });
```

##### 3.5 Deleting Data
```csharp
string deleteQuery = "DELETE FROM Products WHERE Id = @Id";
connection.Execute(deleteQuery, new { Id = 1 });
```
 **[⬆ Back to Top](#table-of-contents)**

4. ## Methods

##### Dapper Extension Methods

Dapper provides a set of extension methods that can be used to perform various database operations, including fetching data, inserting records, updating records, and deleting records. These extension methods extend the `IDbConnection` interface and are commonly used when working with Dapper.

##### Execute

- `Execute`: Executes a command one or multiple times.

##### ExecuteReader

- `ExecuteReader`: Executes a command and returns a data reader.

##### ExecuteScalar

- `ExecuteScalar`: Executes a command and returns a scalar value.

##### Query

- `Query`: Used to fetch data from the database.

##### QueryFirst

- `QueryFirst`: Executes a query and maps the first result.

##### QueryFirstOrDefault

- `QueryFirstOrDefault`: Executes a query and maps the first result, or a default value if the sequence contains no elements.

##### QuerySingle

- `QuerySingle`: Executes a query and maps the first result, throwing an exception if there is not exactly one element in the sequence.

##### QuerySingleOrDefault

- `QuerySingleOrDefault`: Executes a query and maps the first result, or a default value if the sequence is empty; throws an exception if there is more than one element in the sequence.

##### QueryMultiple

- `QueryMultiple`: Executes multiple queries within the same command and maps results.

```csharp
string sqlOrderDetails = "SELECT TOP 5 * FROM OrderDetails;";
string sqlOrderDetail = "SELECT * FROM OrderDetails WHERE OrderDetailID = @OrderDetailID;";
string sqlCustomerInsert = "INSERT INTO Customers (CustomerName) Values (@CustomerName);";

using (var connection = new SqlConnection(FiddleHelper.GetConnectionStringSqlServerW3Schools()))
{
    var orderDetails = connection.Query<OrderDetail>(sqlOrderDetails).ToList();
    var orderDetail = connection.QueryFirstOrDefault<OrderDetail>(sqlOrderDetail, new { OrderDetailID = 1 });
    var affectedRows = connection.Execute(sqlCustomerInsert, new { CustomerName = "Mark" });

    Console.WriteLine(orderDetails.Count);
    Console.WriteLine(affectedRows);

    FiddleHelper.WriteTable(orderDetails);
    FiddleHelper.WriteTable(new List<OrderDetail>() { orderDetail });
}
```
  
 
5. ## Advanced Querying
##### 4.1 Parameterized Queries
Dapper supports various parameter types for execute and query methods. These parameter types allow you to pass values to your SQL queries in a safe and parameterized way.

##### Anonymous Parameters
Used for simple queries where you don't need to create a separate class to represent your data.
##### Dynamic Parameters
Useful when you need to create a dynamic list of parameters or when you need to dynamically change parameter values.
##### List Parameters
Allows you to specify multiple parameters on an IN clause by using a list.
##### String Parameters
Useful when working with SQL Server stored procedures that accept varchar input parameters.
```csharp

// Anonymous
var affectedRows = connection.Execute(sql,
                    new { Kind = InvoiceKind.WebInvoice, Code = "Single_Insert_1" },
                    commandType: CommandType.StoredProcedure);

// Dynamic
DynamicParameters parameter = new DynamicParameters();
parameter.Add("@Kind", InvoiceKind.WebInvoice, DbType.Int32, ParameterDirection.Input);
parameter.Add("@Code", "Many_Insert_0", DbType.String, ParameterDirection.Input);
parameter.Add("@RowCount", dbType: DbType.Int32, direction: ParameterDirection.ReturnValue);

connection.Execute(sql,
    parameter,
    commandType: CommandType.StoredProcedure);

int rowCount = parameter.Get<int>("@RowCount");

// List
connection.Query<Invoice>(sql, new { Kind = new[] { InvoiceKind.StoreInvoice, InvoiceKind.WebInvoice } }).ToList();

// String
connection.Query<Invoice>(sql, new { Code = new DbString { Value = "Invoice_1", IsFixedLength = false, Length = 9, IsAnsi = true } }).ToList();
Result Mapping

##### 4.2 Query Multiple Result Sets
```csharp
string multiQuery = "SELECT * FROM Customers; SELECT * FROM Orders;";
using (var multiResult = connection.QueryMultiple(multiQuery))
{
    List<Customer> customers = multiResult.Read<Customer>().ToList();
    List<Order> orders = multiResult.Read<Order>().ToList();
}
```
 **[⬆ Back to Top](#table-of-contents)**
 
6. ## Mapping Relationships
Dapper supports one-to-one and one-to-many relationships using the `Query` and `Query` methods respectively.
Result Mapping
Dapper provides various ways to map query results to objects.

##### Anonymous Mapping
Allows you to store the results of a SQL query in an anonymous type.
##### Strongly Typed Mapping
Allows you to store the results of a SQL query in a strongly typed manner.
##### Multi-Mapping
Maps the result to a strongly typed list with relations.
##### Multi-Result
Executes multiple queries within the same command and maps results.
##### Multi-Type
Executes a query and maps the result to a list of different types.
```csharp

string sqlOrderDetails = "SELECT TOP 10 * FROM OrderDetails;";

using (var connection = new SqlConnection(FiddleHelper.GetConnectionStringSqlServerW3Schools()))
{
    var anonymousList = connection.Query(sqlOrderDetails).ToList();
    var orderDetails = connection.Query<OrderDetail>(sqlOrderDetails).ToList();

    Console.WriteLine(anonymousList.Count);
    Console.WriteLine(orderDetails.Count);

    FiddleHelper.WriteTable(orderDetails);
    FiddleHelper.WriteTable(connection.Query(sqlOrderDetails).FirstOrDefault());
}
```


7. ## Transactions and Bulk Operations
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
 **[⬆ Back to Top](#table-of-contents)**
 
8. ## Performance Optimization
- Use async methods for asynchronous database operations.
- Enable query caching for frequently used queries.
- Pay attention to the performance impact of loading related entities.
 **[⬆ Back to Top](#table-of-contents)**
  
9. ## Handling Stored Procedures
```csharp
string spName = "InsertProduct";
var parameters = new { Name = "New Product", Price = 19.99 };
connection.Execute(spName, parameters, commandType: CommandType.StoredProcedure);
```
This would be the sample stored procedure
```sql
CREATE PROCEDURE InsertProduct
    @Name NVARCHAR(255),
    @Price DECIMAL(18, 2)
AS
BEGIN
    INSERT INTO Products (Name, Price)
    VALUES (@Name, @Price)
END
```
When you execute the code you provided, Dapper will pass the values "New Product" and 19.99 to the stored procedure's parameters, and the stored procedure will insert a new row into the "Products" table with the provided values.

 **[⬆ Back to Top](#table-of-contents)**
 
10. ## Async Programming with Dapper
Dapper provides async methods to perform database operations asynchronously. Use `ExecuteAsync`, `QueryAsync`, and `QueryMultipleAsync` for asynchronous programming.

 **[⬆ Back to Top](#table-of-contents)**
 
11. ## Best Practices and Tips
- Keep your SQL queries maintainable and organized.
- Use parameterized queries to prevent SQL injection.
- Consider separating database access logic from business logic using repositories or services.
  
 **[⬆ Back to Top](#table-of-contents)**
  
12. ## Additional Resources
- Dapper GitHub Repository: [https://github.com/DapperLib/Dapper](https://github.com/DapperLib/Dapper)
- Dapper Documentation: [https://dapper-tutorial.net/dapper](https://dapper-tutorial.net/dapper)
- Dapper Performance Comparison: [https://dapper-tutorial.net/performance](https://dapper-tutorial.net/performance)
- 
 **[⬆ Back to Top](#table-of-contents)**
  
This comprehensive guide covers the basics of Dapper and provides insights into advanced topics. Remember that practice is key to mastering any technology, so make sure to experiment with various scenarios and use cases to solidify your understanding of Dapper in .NET C#. Happy coding!
```
