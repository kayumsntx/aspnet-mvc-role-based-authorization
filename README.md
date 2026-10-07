# MVC Authentication & Authorization

A simple **ASP.NET MVC 5 Authentication and Authorization** web application built with **C#**, **Entity Framework 6**, **SQL Server LocalDB**, and **Forms Authentication**.

This project demonstrates how to implement a basic login system, user authentication, role management, and database integration in an ASP.NET MVC application.

## 🚀 Features

* User Login
* User Logout
* Forms Authentication
* Username & Password Validation
* Role Management
* User & Role Relationship
* Entity Framework 6
* SQL Server LocalDB
* MVC Architecture
* Razor Views
* Bootstrap UI
* Anti-Forgery Token
* Entity Framework Code First

## 🛠️ Technologies Used

* **C#**
* **ASP.NET MVC 5**
* **.NET Framework 4.7.2**
* **Entity Framework 6.5.2**
* **SQL Server LocalDB**
* **Razor View Engine**
* **Bootstrap 5**
* **jQuery**
* **Visual Studio 2022**

## 📂 Project Structure

```text
MVCAuthAndAuth
│
├── App_Start
│   └── RouteConfig.cs
│
├── Controllers
│   ├── AccountController.cs
│   └── HomeController.cs
│
├── Models
│   ├── AppDbContext.cs
│   ├── tbl_User.cs
│   └── tbl_Role.cs
│
├── Views
│   ├── Account
│   │   └── Login.cshtml
│   │
│   ├── Home
│   │   └── Index.cshtml
│   │
│   └── Shared
│       ├── _Layout.cshtml
│       └── Error.cshtml
│
├── Content
├── Scripts
├── Properties
├── packages.config
├── Web.config
├── Global.asax
└── MVCAuthAndAuth.csproj
```

## 🔐 Authentication

The application uses **Forms Authentication** provided by ASP.NET MVC.

The authentication flow is:

```text
User
  │
  ▼
Login Page
  │
  ▼
Username & Password Validation
  │
  ├── Invalid → Login Error
  │
  └── Valid
       │
       ▼
Forms Authentication Cookie
       │
       ▼
Home Page
```

Authentication is configured in `Web.config`:

```xml
<authentication mode="Forms">
    <forms loginUrl="Account/Login">
    </forms>
</authentication>
```

## 👤 User Model

The application contains a user model with:

* User ID
* Username
* Password
* Role ID
* Role relationship

Example:

```csharp
public class tbl_User
{
    public int Id { get; set; }
    public string UserName { get; set; }
    public string Password { get; set; }
    public int RoleId { get; set; }
    public tbl_Role Tbl_Role { get; set; }
}
```

## 👥 Role Model

Roles are represented using the `tbl_Role` entity.

```csharp
public class tbl_Role
{
    public int Id { get; set; }
    public string RoleName { get; set; }
}
```

The relationship allows users to be associated with a specific role.

## 🗄️ Database

The project uses **Entity Framework 6 Code First** with SQL Server LocalDB.

Database context:

```csharp
public class AppDbContext : DbContext
{
    public AppDbContext() : base("name=AppDbContext")
    {
    }

    public DbSet<tbl_User> tbl_Users { get; set; }
    public DbSet<tbl_Role> tbl_Roles { get; set; }
}
```

### Database Connection

The connection string is configured in:

```text
Web.config
```

Current development configuration uses:

```text
(LocalDB)\MSSQLLocalDB
```

and the database name:

```text
Auth70Db
```

> For another environment, update the connection string in `Web.config`.

## ▶️ Getting Started

### Prerequisites

Make sure you have:

* Visual Studio 2019 or 2022
* .NET Framework 4.7.2 Developer Pack
* SQL Server LocalDB
* IIS Express
* NuGet Package Manager

### 1. Clone the Repository

```bash
git clone https://github.com/yourusername/MVCAuthAndAuth.git
```

### 2. Open the Solution

Open:

```text
MVCAuthAndAuth.sln
```

with Visual Studio.

### 3. Restore NuGet Packages

Visual Studio should restore the required packages automatically.

The project uses packages including:

* EntityFramework 6.5.2
* Microsoft.AspNet.Mvc 5.2.9
* Microsoft.AspNet.Razor 3.2.9
* Microsoft.AspNet.WebPages 3.2.9
* Bootstrap 5.3.8

### 4. Configure the Database

Check the connection string in:

```text
Web.config
```

Example:

```xml
<connectionStrings>
    <add name="AppDbContext"
         connectionString="data source=(LocalDB)\MSSQLLocalDB; Initial Catalog=Auth70Db; Trusted_Connection=true"
         providerName="System.Data.SqlClient" />
</connectionStrings>
```

### 5. Run the Application

Press:

```text
Ctrl + F5
```

or use:

```text
IIS Express
```

from Visual Studio.

## 🔑 Login Flow

The login process is handled by:

```text
Controllers/AccountController.cs
```

The application checks the submitted username and password against the database.

If the credentials are valid:

```csharp
FormsAuthentication.SetAuthCookie(user.UserName, false);
```

The user is then redirected to the Home page.

To log out:

```csharp
FormsAuthentication.SignOut();
```

## 📊 Application Architecture

The project follows the traditional **ASP.NET MVC architecture**:

```text
        Browser
           │
           ▼
       Controller
           │
     ┌─────┴─────┐
     ▼           ▼
   Model       View
     │           │
     ▼           ▼
Entity Framework  Razor
     │
     ▼
 SQL Server
```

### MVC Components

**Model**

Handles application data and database entities.

```text
Models/
```

**View**

Provides the user interface using Razor.

```text
Views/
```

**Controller**

Handles HTTP requests and application logic.

```text
Controllers/
```

## 📚 Learning Objectives

This project was created to practice:

* ASP.NET MVC 5
* MVC Architecture
* C#
* Entity Framework 6
* Code First
* SQL Server
* Database Relationships
* Forms Authentication
* Login/Logout functionality
* Razor Views
* Bootstrap
* Model Binding
* Anti-Forgery Tokens
* CRUD and database operations

## 🔮 Future Improvements

Possible improvements include:

* Password hashing instead of storing plain-text passwords
* User registration
* Role-based authorization
* Admin dashboard
* User management
* Role management UI
* Password reset
* Remember Me functionality
* User profile
* SQL Server production database
* Repository/Service Pattern
* Dependency Injection
* Improved validation
* Authentication error handling
* ASP.NET Identity migration

## ⚠️ Security Note

This project is primarily a **learning/demo project**.

The current implementation compares passwords directly against database values. For a production application, passwords should **never be stored as plain text**.

A production-ready application should use:

* ASP.NET Identity
* Password hashing
* Secure authentication cookies
* HTTPS
* Proper authorization
* Input validation
* Secure connection strings
* Secrets/environment configuration

## 📸 Screenshots

You can add screenshots to a `screenshots` folder:

```text
screenshots/
├── login.png
├── home.png
└── database.png
```

Then reference them in this README:

```markdown
![Login Page](screenshots/login.png)

![Home Page](screenshots/home.png)
```

## 👨‍💻 Author

**MD Kayum Hossain**

This project is part of my learning journey in **C#, ASP.NET MVC, Entity Framework, SQL Server, and Full Stack Web Development**.

---

⭐ If you find this project useful, consider giving the repository a star.
