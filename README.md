# Microservice E-commerce Platform Backend

This project implements the backend for a conceptual e-commerce platform using a microservice architecture. It demonstrates various cloud-native patterns including service discovery, centralized configuration, API gateway, centralized security with Keycloak, and containerization with Docker.

---

## Project Overview

The system is composed of several independent microservices that work together to provide e-commerce functionalities. Key features include inventory management, order processing, and a secure API layer. The architecture is designed for scalability, resilience, and maintainability.

---

## Services Included

### 1. **Config Server (`config-server`)**
- Manages centralized configuration for all microservices using a Git backend.
- Built with Spring Cloud Config Server.

### 2. **Eureka Server (`eureka-server`)**
- Handles service discovery and registration for all microservices.
- Built with Spring Cloud Netflix Eureka.

### 3. **Keycloak Server (`keycloak`)**
- Acts as the central Identity and Access Management (IAM) solution.
- Provides Single Sign-On (SSO) and token-based authentication (OAuth 2.0/OIDC).
- Runs as a Docker container using the official Keycloak image.

### 4. **API Gateway (`api-gateway`)**
- Single entry point for all client requests.
- Handles request routing, rate limiting (conceptual), and security enforcement (JWT validation).
- Built with Spring Cloud Gateway.

### 5. **Inventory Service (`inventory-service`)**
- Manages product stock levels and product information.
- Exposes RESTful APIs and gRPC endpoints.
- Built with Spring Boot.

### 6. **Order Service (`order-service`)**
- Manages customer orders.
- Communicates with Inventory Service (via Feign and gRPC) to check stock and reserve products.
- Built with Spring Boot.

---

## Core Technologies & Patterns Used

### Backend Framework
- Java, Spring Boot

### Spring Cloud Suite
- Netflix Eureka (Service Discovery)
- Config Server (Centralized Configuration)
- Gateway (API Gateway)
- OpenFeign (Declarative REST Client)
- Spring Cloud LoadBalancer
- Bootstrap (for Config Client)

### Inter-Service Communication
- RESTful APIs
- gRPC with Protocol Buffers

### Containerization
- Docker (for each microservice)
- Docker Compose (for local orchestration)

### Security
- Keycloak (IAM, SSO)
- OAuth 2.0 & OIDC
- JSON Web Tokens (JWT)
- Spring Security (OAuth2 Resource Server)

### Database & Persistence
- PostgreSQL
- Spring Data JPA / Hibernate

### Logging (Initial ELK Stack Setup)
- Elasticsearch
- Logback with `logstash-logback-encoder`
- Structured JSON logging sent to Elasticsearch

### API Documentation
- Springdoc OpenAPI (Swagger UI)

### Build Tool
- Maven

### Version Control
- Git, GitHub (including for config files repo)

---

## Prerequisites

- Java JDK 21 (or as specified in `pom.xml`)
- Apache Maven 3.6+
- Docker Desktop / Docker Engine
- Docker Compose
- Git

---
## Key Service Ports
| Service        | Port                          |
| -------------- | ----------------------------- |
| Config Server  | `localhost:8888`              |
| Eureka Server  | `localhost:8761`              |
| Keycloak       | `localhost:8180`              |
| API Gateway    | `localhost:7070`              |
| Inventory API  | `localhost:8080` (if exposed) |
| Inventory gRPC | `localhost:9091` (if exposed) |
| Order Service  | `localhost:9090` (if exposed) |
| Elasticsearch  | `localhost:9200`              |

│   ├── inventory-service-dev.properties
│   ├── order-service-dev.properties
│   ├── api-gateway-dev.properties
│   └── application.properties
└── docker-compose.yml

