Sure, here's your example converted into a GitHub Markdown (.md) file format with a table of contents:

```markdown
# Example: User Authentication and Authorization in ASP.NET Core

## Table of Contents
- [Authentication](#authentication)
- [Authorization](#authorization)
- [Applying Authorization to Controllers and Actions](#applying-authorization-to-controllers-and-actions)
- [Checking User Roles in Views](#checking-user-roles-in-views)

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
```

Just copy and paste this content into a .md file on GitHub or any Markdown editor to see the formatted output.
