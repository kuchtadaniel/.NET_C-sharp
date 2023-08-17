
# Example: User Authentication and Authorization in ASP.NET Core

## Table of Contents
- [Authentication](#authentication)
- [JSON](#json)
- [.NET Web API](#.net-web-api)
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

 # .NET Web API

## Basics

### What is .NET Web API?
.NET Web API is a framework for building HTTP services that can be consumed by various clients, such as web applications and mobile apps.

### Advantages of .NET Web API
- Allows creating RESTful APIs.
- Supports various formats like JSON and XML for data exchange.
- Built-in support for content negotiation.

### Key Components
- Controllers: Handle incoming HTTP requests and generate responses.
- Routes: Define how URLs map to controller actions.
- Models: Represent data structures used by the API.

## Creating a Basic Web API

### Create a Controller
- Add a new controller class that inherits from `ApiController`.
- Define action methods to handle HTTP requests (GET, POST, PUT, DELETE).

### Routing
- Configure routes in `WebApiConfig` to map URLs to controller actions.
- Use attributes like `[Route]`, `[HttpGet]`, etc., to define routes on action methods.

## Request and Response Formats

### Input Binding
- Automatically bind request data to action parameters using attributes like `[FromBody]` and `[FromUri]`.

### Output Formatting
- Response data is automatically serialized to requested format (JSON, XML) based on client's request.

## Error Handling

### Exception Filters
- Use exception filters to handle exceptions and return meaningful error responses.

## Content Negotiation

### Content-Type Headers
- Clients can request specific response content types using the `Accept` header.

## Authentication and Authorization

### Authentication
- Implement authentication using attributes like `[Authorize]`.
- Use token-based authentication or other authentication methods.

### Authorization
- Control access to actions using `[Authorize]` with roles or policies.

## Versioning

### API Versioning
- Handle API versioning using attributes like `[ApiVersion]`.

## Dependency Injection

### DI in Web API
- Use dependency injection for services within controllers.

## Testing

### Unit Testing
- Write unit tests for controllers and actions.
- Use testing frameworks like MSTest or NUnit.

## Best Practices

### Separation of Concerns
- Keep controllers lightweight; delegate business logic to services.

### Use RESTful Practices
- Follow REST principles like resource naming and HTTP methods.

### Documentation
- Document your API using tools like Swagger.

## Conclusion

This worksheet covers the basics of .NET Web API, including creating controllers, handling requests, formatting responses, and more. Use this as a quick reference during your interview preparation!


 **[⬆ Back to Top](#table-of-contents)**
