# Authentication-API
This is the authentication API by using Java + Spring boot + maven.

## Getting Started
In this section, you will find instructions on how to set up and run the Authentication API project.

## Requirement

# Authentication-API

Lightweight Authentication API built with Java and Spring Boot, providing user registration, login, and JWT\-based stateless authentication.

## Table of Contents
- \#\# Features
- \#\# Tech Stack
- \#\# Requirements
- \#\# Quick Start
- \#\# Configuration
- \#\# API Endpoints
- \#\# Project Structure
- \#\# Tests
- \#\# Contributing
- \#\# License
- \#\# Repository

## Features
- User registration and login with secure password hashing.
- JWT access token issuance and validation.
- Role\-based authorization-ready endpoints.
- Health check endpoint for quick verification.

## Tech Stack
- Java 17+ (adjust to project `java.version`)
- Spring Boot
- Maven
- JWT (library configurable)
- H2 (in-memory) or PostgreSQL (configurable)
- IntelliJ IDEA, Git / GitHub

## Requirements
- JDK 17+ installed and `JAVA_HOME` configured.
- Maven 3.6+
- Windows (development environment)

## Quick Start
1. Clone the repository:
   git clone `https://github.com/Het-2004/Authentication-API.git`
2. Open in IntelliJ IDEA and set Project SDK to match `java.version` in `pom.xml`.
3. Build:
    mvn -U clean package
4. Run (development):
    mvn spring-boot:run
5. Run the packaged jar:
    java -jar target\auth-api-0.0.1-SNAPSHOT.jar
6. Health check:
   Visit `http://localhost:8080/` (default port) to verify the app responds.

## Configuration
- Application properties are in `src/main/resources/application.properties` (or `application.yml`).
- Common settings: server port, datasource URL/credentials, JWT secret and expiry.
- Example (customize as needed):
  - `server.port=8080`
  - `spring.datasource.url=jdbc:postgresql://localhost:5432/dbname`
  - `jwt.secret=your-secret-key`

## API Endpoints (examples)
- `GET /` — Health check (returns "OK")
- `POST /api/auth/register` — Register new user (body: username, password, roles)
- `POST /api/auth/login` — Authenticate and receive JWT (body: username, password)
- Protected endpoints: require `Authorization: Bearer <token>`

Adjust paths to match your controllers.

## Project Structure
- `src/main/java/...` — application code (controllers, services, repositories)
- `src/main/resources` — configuration and static resources
- `pom.xml` — Maven build and dependencies

## Tests
- Run unit/integration tests:
    mvn test

## Contributing
- Fork the repository, create a feature branch, add tests, and open a pull request.
- Keep changes small and document configuration changes in `application.properties`.

## License
- Add your chosen license file at project root (e.g., `LICENSE`).

## Repository
- Remote: `https://github.com/Het-2004/Authentication-API.git`
- Branch: `master`