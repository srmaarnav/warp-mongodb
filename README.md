# Warp MongoDB REST API

A RESTful API built with Rust's Warp framework and MongoDB for managing a collection of books.

## Overview

This project demonstrates how to build a modern REST API using Rust with the following technologies:

- [Warp](https://github.com/seanmonstar/warp) - Lightweight web framework
- [MongoDB](https://www.mongodb.com/) - NoSQL database 
- [Tokio](https://tokio.rs/) - Asynchronous runtime for Rust
- [Serde](https://serde.rs/) - Serialization/deserialization framework

## Features

- Complete CRUD operations for a book resource
- Async request handling
- MongoDB integration
- Error handling with custom types
- Docker-based MongoDB setup

## Project Structure

```
.
├── src/
│   ├── main.rs     # Application entry point and route definitions
│   ├── db.rs       # MongoDB connection and database operations
│   ├── handler.rs  # Request handlers for the API endpoints
│   └── error.rs    # Error types and error handling
├── Cargo.toml      # Rust dependencies and project configuration
└── Makefile        # Utility commands for development
```

## Getting Started

### Prerequisites

- Rust and Cargo
- Docker (for MongoDB)

### Setup

1. Clone the repository

2. Start MongoDB with Docker:
```bash
make mongostart
```

3. Run the application:
```bash
make dev
```

The server will start on port 8080.

## API Endpoints

### Fetch all books

```bash
curl http://localhost:8080/book
```

### Create a new book

```bash
curl -X POST http://localhost:8080/book \
  -d '{"name": "The Lean Startup", "author": "Eric Ries", "num_pages": 480, "tags": ["non-fiction", "startup"]}' \
  -H "content-type: application/json"
```

### Edit a book

```bash
curl -X PUT http://localhost:8080/book/5f15fd5400b98edc001944c0 \
  -d '{"name": "The Lean Way", "author": "Eric Ries", "num_pages": 650, "tags": ["non-fiction", "business"]}' \
  -H "content-type: application/json"
```

### Delete a book

```bash
curl -X DELETE http://localhost:8080/book/5f15fd3900789205001944bf
```

## Book Data Model

```json
{
  "id": "5f15fd5400b98edc001944c0",
  "name": "The Lean Startup",
  "author": "Eric Ries",
  "num_pages": 480,
  "added_at": "2023-04-01T10:30:00Z",
  "tags": ["non-fiction", "startup"]
}
```

## Development

### Build the project
```bash
make build
```

### Run tests
```bash
make test
```

### Generate documentation
```bash
make docs
```

### Lint with Clippy
```bash
make lint
```

### Format code with Rustfmt
```bash
make style-check
```

### Stop MongoDB
```bash
make mongostop
```

### Clean up build artifacts and data
```bash
make clean
```

## Error Handling

The API returns appropriate HTTP status codes and error messages:

- 404: Resource not found
- 400: Invalid request body
- 405: Method not allowed
- 500: Internal server error

