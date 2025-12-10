# Authentication API

A secure RESTful Authentication API built with **Java** and **Spring Boot**, featuring JWT-based stateless authentication, user registration, login, and role-based access control.

## 📋 Table of Contents
- [Features](#features)
- [Tech Stack](#tech-stack)
- [Requirements](#requirements)
- [Getting Started](#getting-started)
- [Configuration](#configuration)
- [API Endpoints](#api-endpoints)
- [Project Structure](#project-structure)
- [Security](#security)
- [Running Tests](#running-tests)
- [Contributing](#contributing)
- [License](#license)

## ✨ Features

- ✅ **User Registration** - Secure user signup with password encryption
- 🔐 **JWT Authentication** - Token-based stateless authentication
- 🔒 **Spring Security Integration** - Role-based access control
- 👤 **User Management** - Custom UserDetailsService implementation
- 💾 **H2 Database** - In-memory database for development (easily switchable to production DB)
- 🏥 **Health Check Endpoint** - Monitor API status
- 🎨 **Web UI** - Static web interface included
- 🔄 **RESTful API Design** - Clean and intuitive endpoints

## 🛠️ Tech Stack

- **Java**: 17
- **Spring Boot**: 3.2.0
- **Spring Security**: JWT-based authentication
- **Spring Data JPA**: Data persistence layer
- **H2 Database**: In-memory database (development)
- **JWT (JJWT)**: JSON Web Token implementation
- **Maven**: Dependency management and build tool
- **Lombok**: Reduces boilerplate code

## 📦 Requirements

- **JDK 17** or higher
- **Maven 3.6+**
- **Git** (for version control)

## 🚀 Getting Started

### 1. Clone the Repository
```bash
git clone https://github.com/Het-2004/Authentication-API.git
cd Authentication-API/auth-api
```

### 2. Build the Project
```bash
mvn clean install
```

### 3. Run the Application
```bash
mvn spring-boot:run
```

Or run the packaged JAR:
```bash
java -jar target/auth-api-0.0.1-SNAPSHOT.jar
```

### 4. Access the Application
- **API Base URL**: `http://localhost:8080`
- **H2 Console**: `http://localhost:8080/h2-console`
  - JDBC URL: `jdbc:h2:mem:testdb`
  - Username: `sa`
  - Password: *(leave empty)*
- **Web Interface**: `http://localhost:8080/index.html`

## ⚙️ Configuration

The application is configured in `src/main/resources/application.properties`:

```properties
# Server Configuration
server.port=8080

# Database Configuration (H2 In-Memory)
spring.datasource.url=jdbc:h2:mem:testdb
spring.datasource.username=sa
spring.datasource.password=

# JPA Configuration
spring.jpa.hibernate.ddl-auto=update
spring.jpa.show-sql=true

# H2 Console
spring.h2.console.enabled=true

# JWT Configuration
app.jwt.secret=MySuperSecretKeyForJwtDontUseInProd123
app.jwt.expiration-ms=3600000  # 1 hour
```

> ⚠️ **Important**: Change the JWT secret before deploying to production!

## 📡 API Endpoints

### Public Endpoints

#### Health Check
```http
GET /
GET /api/hello
```
Returns: Health status message

#### Register User
```http
POST /api/auth/register
Content-Type: application/json

{
  "username": "john_doe",
  "email": "john@example.com",
  "password": "securePassword123"
}
```
Returns: JWT token in `AuthResponse`

#### Login
```http
POST /api/auth/login
Content-Type: application/json

{
  "username": "john_doe",
  "password": "securePassword123"
}
```
Returns: JWT token in `AuthResponse`

### Protected Endpoints

All protected endpoints require JWT token in the Authorization header:
```http
Authorization: Bearer <your-jwt-token>
```

#### Demo Protected Endpoint
```http
GET /api/demo
Authorization: Bearer <token>
```

## 📁 Project Structure

```
auth-api/
├── src/
│   ├── main/
│   │   ├── java/com/example/authapi/
│   │   │   ├── AuthApiApplication.java       # Main application class
│   │   │   ├── HealthController.java         # Health check endpoint
│   │   │   ├── auth/                          # Authentication module
│   │   │   │   ├── AuthController.java        # Register & Login endpoints
│   │   │   │   ├── AuthService.java           # Authentication logic
│   │   │   │   ├── AuthRequest.java           # Login DTO
│   │   │   │   ├── AuthResponse.java          # JWT response DTO
│   │   │   │   └── RegisterRequest.java       # Registration DTO
│   │   │   ├── demo/                           # Demo protected endpoints
│   │   │   │   └── HelloController.java
│   │   │   ├── security/                       # Security configuration
│   │   │   │   ├── SecurityConfig.java         # Spring Security config
│   │   │   │   ├── JwtService.java             # JWT utilities
│   │   │   │   ├── JwtAuthenticationFilter.java # JWT filter
│   │   │   │   └── CustomUserDetailsService.java
│   │   │   └── user/                           # User entity & repository
│   │   │       ├── User.java
│   │   │       └── UserRepository.java
│   │   └── resources/
│   │       ├── application.properties          # App configuration
│   │       └── static/                          # Web UI files
│   │           ├── index.html
│   │           ├── css/styles.css
│   │           └── js/app.js
│   └── test/                                    # Test classes
│       └── java/com/example/authapi/
│           └── AuthApiApplicationTests.java
├── pom.xml                                      # Maven configuration
└── README.md
```

## 🔐 Security

- **Password Encryption**: BCrypt hashing algorithm
- **JWT Tokens**: Stateless authentication with configurable expiration
- **Spring Security**: Fine-grained access control
- **CORS**: Configurable cross-origin resource sharing
- **HTTP Security**: CSRF protection (configurable)

### Security Features:
- User passwords are never stored in plain text
- JWT tokens expire after 1 hour (configurable)
- All protected endpoints require valid authentication
- Custom authentication filter for JWT validation

## 🧪 Running Tests

Execute the test suite:
```bash
mvn test
```

Run with coverage:
```bash
mvn clean test jacoco:report
```

## 🤝 Contributing

Contributions are welcome! Please follow these steps:

1. **Fork** the repository
2. **Create** a feature branch (`git checkout -b feature/AmazingFeature`)
3. **Commit** your changes (`git commit -m 'Add some AmazingFeature'`)
4. **Push** to the branch (`git push origin feature/AmazingFeature`)
5. **Open** a Pull Request

### Guidelines:
- Follow Java coding conventions
- Write meaningful commit messages
- Add tests for new features
- Update documentation as needed

## 📄 License

This project is licensed under the terms specified in the [LICENSE](LICENSE) file.

## 📞 Contact & Links

- **Repository**: [https://github.com/Het-2004/Authentication-API](https://github.com/Het-2004/Authentication-API)
- **Author**: Het-2004
- **Branch**: master

---

Made with ❤️ using Spring Boot