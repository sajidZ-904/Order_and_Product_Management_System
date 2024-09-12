# Order and Product Management System

## Overview

This project implements an Order and Product Management System using a microservices architecture with ASP.NET Core, Docker, RabbitMQ for event-driven communication, and MSSQL for data storage. The system is designed to handle separate read and write operations through Command Query Responsibility Segregation (CQRS) and supports high scalability for read-heavy operations.

## Architecture

The system is composed of two main services:

- **Order Service**: Manages customer orders.
- **Product Service**: Manages the product catalog.

### Key Features

- **Microservices Architecture**: The system is loosely coupled, ensuring scalability and maintainability.
- **Event-Driven Communication**: Services communicate through RabbitMQ, allowing for asynchronous processing of events such as order creation and product updates.
- **CQRS Pattern**: Separates read and write operations for better performance and scalability.
- **MSSQL Database**: Each service has its own database schema for data isolation.
- **Docker**: Services are containerized using Docker, enabling easy deployment and scalability.

## Prerequisites

- Docker and Docker Compose installed
- .NET 8.0 SDK installed
- RabbitMQ instance running


## Getting Started

### 1. Clone the Repository

```bash
git clone https://github.com/sajidZ-904/order-product-management-system.git
cd order-product-management-system
```

### 2. Set Up Environment Variables

For this project, environment variables can be configured directly in the docker-compose.yml file or passed as parameters.

### 3. Build and Run the Services

Use Docker Compose to build and run the services:

```bash
docker-compose up --build
```
This command will build the Docker images for the Order Service and Product Service and start the necessary containers, including RabbitMQ and the MSSQL databases.

### 4. Access the Services
   
**Order Service**: Accessible at http://localhost:5001

**Product Service**: Accessible at http://localhost:5002

**RabbitMQ Management**: Accessible at http://localhost:15672 (default username: guest, password: guest)

### Testing

# Unit Tests

Unit tests for core functionalities are implemented using xUnit. To run the tests, navigate to the respective service directory and execute:

```bash
dotnet test
```

### Integration Tests

Integration tests simulate real-world scenarios like placing an order and updating product stock. These tests can be run using the same command:

```bash
dotnet test
```

### Design Considerations

**Scalability**: The Product Service is designed to handle high read volume through indexing and optimized queries.
**Loose Coupling**: Event-driven architecture ensures that services remain loosely coupled, allowing for independent scaling and updates.
**Database Isolation**: Each service uses a separate database schema to maintain data integrity and isolation.

### Scaling the System

For increased load, consider:

a. Adding more replicas of the Product Service for read scalability.
b. Implementing caching for frequently accessed data.
c. Using a cloud-based RabbitMQ service for higher availability and scaling.

### License
This project is licensed under the MIT License - see the LICENSE file for details.
