# E-Commerce API

A modern, RESTful E-Commerce API built with ASP.NET Core 8.0 that provides comprehensive functionality for managing products, shopping carts, orders, and payments.

## 📋 Table of Contents

- [Features](#features)
- [Tech Stack](#tech-stack)
- [Project Structure](#project-structure)
- [Prerequisites](#prerequisites)
- [Installation](#installation)
- [Configuration](#configuration)
- [Database Setup](#database-setup)
- [Running the Application](#running-the-application)
- [API Endpoints](#api-endpoints)
- [Authentication](#authentication)
- [Contributing](#contributing)
- [License](#license)

## ✨ Features

- **User Management**: User registration, login, and profile management
- **Product Catalog**: Browse and search products by category
- **Shopping Cart**: Add/remove items, manage cart
- **Order Management**: Create orders, track order status
- **Payment Processing**: Secure payment handling and verification
- **JWT Authentication**: Secure API authentication using JWT tokens
- **Role-Based Access Control**: Support for different user roles
- **Database Migrations**: Automated schema updates
- **Comprehensive API Documentation**: Swagger/OpenAPI integration

## 🛠 Tech Stack

- **Framework**: ASP.NET Core 8.0
- **Language**: C#
- **Database**: SQL Server / Entity Framework Core
- **Authentication**: JWT (JSON Web Tokens)
- **API Documentation**: Swagger/OpenAPI
- **Architecture**: Clean Architecture with Layered Pattern

## 📁 Project Structure

```
E-Commerce-API/
├── E-Commerce.Domain/           # Domain entities and business logic
│   ├── Entities/               # Core domain models
│   │   ├── Product.cs
│   │   ├── Category.cs
│   │   ├── Cart.cs
│   │   ├── Order.cs
│   │   ├── Payment.cs
│   │   └── ...
│   └── Identity/               # User and role models
│       ├── ApplicationUser.cs
│       └── ApplicationRole.cs
│
├── E-Commerce.Infrastructure/   # Data access and external services
│   ├── DatabaseContext/        # Entity Framework DbContext
│   ├── Services/               # Business logic implementations
│   │   ├── AuthService.cs
│   │   ├── ProductService.cs
│   │   ├── CartService.cs
│   │   ├── OrderService.cs
│   │   └── ...
│   ├── Migrations/             # Database migrations
│   └── Seeders/                # Database seeders
│
├── E-Commerce.Application/      # Application contracts and DTOs
│   ├── Contracts/              # Service interfaces
│   ├── DTOs/                   # Data Transfer Objects
│   └── ...
│
└── E-Commerce.API/             # ASP.NET Core Web API
    ├── Controllers/            # API endpoints
    ├── Program.cs              # Application setup
    └── appsettings.json        # Configuration
```

## 📦 Prerequisites

- .NET 8.0 SDK or later
- SQL Server (or compatible database)
- Git
- Visual Studio 2022 or VS Code (optional)

## 🚀 Installation

1. **Clone the repository**

   ```bash
   git clone https://github.com/Yousef-Khaled-Mohamed/E-Commerce-API.git
   cd E-Commerce-API
   ```

2. **Restore NuGet packages**

   ```bash
   dotnet restore
   ```

3. **Install Entity Framework Core CLI tools** (if not already installed)
   ```bash
   dotnet tool install --global dotnet-ef
   ```

## ⚙️ Configuration

1. **Update Connection String**

   Edit `E-Commerce.API/appsettings.json`:

   ```json
   {
     "ConnectionStrings": {
       "DefaultConnection": "Server=YOUR_SERVER;Database=ECommerceDB;Trusted_Connection=true;"
     },
     "JwtSettings": {
       "SecretKey": "your-secret-key-here",
       "ExpirationMinutes": 60
     }
   }
   ```

2. **Configure JWT Settings**
   - Update the `JwtSettings` section with your secret key
   - Ensure the secret key is strong and secure

## 🗄️ Database Setup

1. **Create and apply migrations**

   ```bash
   cd E-Commerce.Infrastructure
   dotnet ef database update
   ```

2. **Seed initial data** (optional)

   The application includes seeders to populate initial categories and products. These are typically run during startup if the database is empty.

## ▶️ Running the Application

1. **Using .NET CLI**

   ```bash
   cd E-Commerce.API
   dotnet run
   ```

2. **Using Visual Studio**
   - Open the solution file `E-Commerce_Solution.slnx`
   - Set `E-Commerce.API` as the startup project
   - Press F5 or click the Run button

3. **Access the API**
   - The API will be available at `https://localhost:5001` (or as configured)
   - Swagger UI: `https://localhost:5001/swagger`

## 📡 API Endpoints

### Authentication

- `POST /api/account/register` - Register a new user
- `POST /api/account/login` - Login and get JWT token

### Products

- `GET /api/products` - Get all products
- `GET /api/products/{id}` - Get product by ID
- `POST /api/products` - Create new product (Admin only)
- `PUT /api/products/{id}` - Update product (Admin only)
- `DELETE /api/products/{id}` - Delete product (Admin only)

### Categories

- `GET /api/categories` - Get all categories
- `GET /api/categories/{id}` - Get category by ID
- `POST /api/categories` - Create category (Admin only)
- `PUT /api/categories/{id}` - Update category (Admin only)
- `DELETE /api/categories/{id}` - Delete category (Admin only)

### Shopping Cart

- `GET /api/cart` - Get user's cart
- `POST /api/cart/add` - Add item to cart
- `DELETE /api/cart/remove/{itemId}` - Remove item from cart
- `PUT /api/cart/update/{itemId}` - Update cart item quantity

### Orders

- `GET /api/orders` - Get user's orders
- `GET /api/orders/{id}` - Get order details
- `POST /api/orders` - Create new order
- `PUT /api/orders/{id}/status` - Update order status (Admin only)

### Payments

- `POST /api/payments/process` - Process payment
- `GET /api/payments/{id}` - Get payment details

## 🔐 Authentication

The API uses JWT (JSON Web Tokens) for authentication:

1. **Register**: Create a new user account

   ```bash
   POST /api/account/register
   Content-Type: application/json

   {
     "email": "user@example.com",
     "password": "password123",
     "firstName": "John",
     "lastName": "Doe"
   }
   ```

2. **Login**: Get JWT token

   ```bash
   POST /api/account/login
   Content-Type: application/json

   {
     "email": "user@example.com",
     "password": "password123"
   }
   ```

3. **Use Token**: Include token in Authorization header
   ```bash
   GET /api/cart
   Authorization: Bearer <your_jwt_token>
   ```

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add some amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## 📝 License

This project is licensed under the MIT License - see the LICENSE file for details.

## 👤 Author

**Yousef Khaled Mohamed**

- GitHub: [@Yousef-Khaled-Mohamed](https://github.com/Yousef-Khaled-Mohamed)

## 📞 Support

For support, please open an issue in the repository or contact the project maintainer.

---

**Happy Coding! 🚀**
