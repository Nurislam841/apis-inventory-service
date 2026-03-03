# Inventory Service (Go + Clean Architecture + REST)

## Overview

This project is a standalone **Inventory Service** implemented in **Go**.  
It follows **Clean Architecture principles**, clearly separating business logic, data access, and delivery layers.

The service exposes **RESTful HTTP APIs** for managing inventory-related entities and is structured for scalability and maintainability.

---

## Architecture

The project follows layered Clean Architecture:

```text
cmd → adapter → usecase → repository → entity
```

### Layer Responsibilities

- **entity/**  
  Core domain models and business rules.

- **usecase/**  
  Application business logic and orchestration.

- **repository/**  
  Data persistence abstraction layer.

- **adapter/http/**  
  HTTP handlers and routing logic.

- **cmd/**  
  Application entry point.

This structure ensures:
- Separation of concerns
- High testability
- Maintainable and scalable design

---

## Project Structure

```text
apis-inventory-service-main/
│
├── cmd/
│   └── main.go
│
├── internal/
│   ├── adapter/
│   │   └── http/
│   │       ├── handler.go
│   │       └── router.go
│   │
│   ├── entity/
│   │   └── product.go
│   │
│   ├── repository/
│   │   └── product_repository.go
│   │
│   └── usecase/
│       └── product_usecase.go
│
├── go.mod
└── go.sum
```

---

## Domain Model

### Product Entity

The core domain entity is:

- `Product`

Typically includes:
- ID
- Name
- Description
- Price
- Quantity

(All business rules related to products are encapsulated in the domain layer.)

---

## API Endpoints

The service exposes REST endpoints for product management.

Typical operations include:

```text
POST   /products
GET    /products
GET    /products/{id}
PUT    /products/{id}
DELETE /products/{id}
```

These endpoints are implemented in:

```text
internal/adapter/http/
```

---

## How to Run

### 1. Clone repository

```bash
git clone <your-repository-url>
cd apis-inventory-service-main
```

### 2. Install dependencies

```bash
go mod tidy
```

### 3. Run the service

```bash
go run cmd/main.go
```

The server starts and listens on the configured port (defined in `main.go`).

---

## Design Principles

- Clean Architecture
- Dependency inversion
- Layer isolation
- Interface-based repository pattern
- Minimal external dependencies

---

## What This Project Demonstrates

- REST API development in Go
- Clean Architecture implementation
- Proper separation of domain and infrastructure
- Repository pattern usage
- Scalable service structure
