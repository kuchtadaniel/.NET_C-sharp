
# Example: User Authentication and Authorization in ASP.NET Core

## Table of Contents
- [Authentication](#authentication)
- [JSON](#json)
- [Applying Authorization to Controllers and Actions](#applying-authorization-to-controllers-and-actions)
- [Checking User Roles in Views](#checking-user-roles-in-views)

  **[](#table-of-contents)**

## Authentication
Authentication is the process of verifying the identity of a user. In this example, we'll use a simple username-password authentication approach.

```csharp
// Startup.cs
public void ConfigureServices(IServiceCollection services)
{
    // Configure authentication services
    services.AddAuthentication("MyAuthScheme")
        .AddCookie("MyAuthScheme", options =>
        {
            options.LoginPath = "/Account/Login"; // Redirect to login page if not authenticated
        });
}
```

## Authorization
Authorization determines what actions or resources a user is allowed to access based on their role or permissions.

```csharp
// Startup.cs
public void ConfigureServices(IServiceCollection services)
{
    // ... (Authentication setup)

    // Configure authorization services
    services.AddAuthorization(options =>
    {
        options.AddPolicy("AdminOnly", policy =>
            policy.RequireRole("Admin")); // Example: Only users with "Admin" role can access
    });
}
```

## Applying Authorization to Controllers and Actions
Apply authorization rules to controllers or actions using attributes.

```csharp
// UserController.cs
[Authorize] // Requires authentication to access any action in this controller
public class UserController : Controller
{
    public IActionResult Profile()
    {
        return View();
    }

    [Authorize(Policy = "AdminOnly")] // Requires "Admin" role to access this action
    public IActionResult AdminPanel()
    {
        return View();
    }
}
```

## Checking User Roles in Views
In your Razor views, you can conditionally render content based on user roles.

```html
@using Microsoft.AspNetCore.Authorization

@if (User.Identity.IsAuthenticated)
{
    @if (User.IsInRole("Admin"))
    {
        <p>Welcome, Admin!</p>
    }
    else
    {
        <p>Welcome, User!</p>
    }
}
else
{
    <p>Please log in to access this content.</p>
}
```


 **[⬆ Back to Top](#table-of-contents)**
 
## JSON

**JSON (JavaScript Object Notation) in Brief:**

JSON is a lightweight format for sharing data between systems. It's easy for both humans and computers to grasp. Here's the lowdown:

- **Structure:** JSON uses key-value pairs, like a dictionary. Values can be strings, numbers, objects, arrays, booleans, or null.
- **Example:**
  ```json
  {
    "name": "John",
    "age": 30,
    "isStudent": false,
    "grades": [90, 85, 78]
  }
  ```
- **Advantages:** JSON is simple, lightweight, and well-supported in programming languages. It's perfect for web APIs and data sharing.
- **Usage:** It's used in web development for AJAX requests, configuration files, and more.
- **Parsing:** Languages provide tools to easily convert JSON to usable data. In JavaScript:
  ```javascript
  const jsonString = '{"name": "John", "age": 30}';
  const parsedData = JSON.parse(jsonString);
  console.log(parsedData.name); // Output: John
  ```
- **Security:** JSON itself doesn't handle security; applications need to ensure data safety.
- **Key Difference from XML:** JSON is lighter, simpler, and often preferred for modern applications.

In summary, JSON is a popular format for sharing and storing data in web development and beyond.

 **[⬆ Back to Top](#table-of-contents)**
