🌟 Spring Boot Microservices — Full Enterprise System

A production-ready Microservices Architecture built using
Spring Boot 3, Spring Cloud, Eureka, API Gateway, PostgreSQL, Docker, and Lombok.

This system demonstrates real-world concepts like service discovery, centralized routing, event-driven communication, monitoring, containerization, and scalable microservices.

📘 Table of Contents

Project Overview

Architecture

Tech Stack

Project Structure

Microservices Explained

How to Run

API Endpoints

Database

Features

Author

🚀 Project Overview

This project demonstrates a complete distributed microservices ecosystem with:

✔ Independent services
✔ Central API Gateway
✔ Service Discovery
✔ Event-driven flows
✔ PostgreSQL databases
✔ Docker containerization
✔ Fully scalable architecture

Every microservice can be deployed independently, scaled independently, and communicates via Eureka and REST.

🏗️ Architecture
┌─────────────────────┐
│     API Gateway     │
└──────────┬──────────┘
│
┌───────────────────────────┼───────────────────────────┐
│                           │                           │
┌───────┐                 ┌──────────┐                ┌─────────────┐
│Product│<--------------->│ Inventory│<-------------->│   Order     │
│Service│                 │ Service  │                │  Service    │
└───────┘                 └──────────┘                └─────┬───────┘
│
┌────────▼────────┐
│ Notification     │
│    Service       │
└──────────────────┘

                     ┌─────────────────────────────┐
                     │     Eureka Discovery        │
                     └─────────────────────────────┘

🛠️ Tech Stack
Backend

Java 21

Spring Boot 3

Spring Web

Spring Data JPA

Spring Cloud (Eureka + Gateway)

Lombok

Database

PostgreSQL

Tools

Docker

Docker Compose

IntelliJ IDEA

📁 Project Structure
spring-boot-microservices/
│
├── api-gateway/                  # Central gateway
├── discovery-server/             # Eureka registry
│
├── product-service/              # Product CRUD, PostgreSQL
│   ├── controller/
│   ├── dto/
│   ├── model/
│   ├── repository/
│   └── service/
│
├── inventory-service/            # Stock validation
│   ├── controller/
│   ├── model/
│   ├── repository/
│   └── service/
│
├── order-service/                # Places orders
│   ├── controller/
│   ├── dto/
│   ├── listener/
│   ├── model/
│   └── service/
│
├── notification-service/         # Sends notifications on order events
│
├── docker-compose.yml            # Run entire stack with one command
└── pom.xml                       # Parent Maven project

🧩 Microservices Explained
⭐ 1. API Gateway

Single entry point

Route authentication

Routes all requests to downstream services

⭐ 2. Discovery Server (Eureka)

Service registry

Enables dynamic load balancing

Removes hard-coded URLs

⭐ 3. Product Service

Create products

Fetch products

Stores data in PostgreSQL

⭐ 4. Inventory Service

Check stock availability

Used by Order Service before placing orders

⭐ 5. Order Service

Receives order requests

Calls Product + Inventory Services

Publishes notifications

⭐ 6. Notification Service

Listens for order events

Logs/send notification messages

▶️ How to Run
🔹 Option 1 — Run Entire System Using Docker (Recommended)
docker-compose up --build


This starts:

✔ API Gateway
✔ Discovery Server
✔ Product Service
✔ Inventory Service
✔ Order Service
✔ Notification Service
✔ PostgreSQL

🔹 Option 2 — Run Each Service Manually

Run in this order:

1️⃣ discovery-server
2️⃣ api-gateway
3️⃣ product-service
4️⃣ inventory-service
5️⃣ order-service
6️⃣ notification-service

🌐 API Endpoints
Product Service
POST /api/product
GET  /api/product

Inventory Service
GET /api/inventory?skuCode=SKU001

Order Service
POST /api/order

🗄️ Database Configuration (PostgreSQL)
spring.datasource.url=jdbc:postgresql://localhost:5432/microservices
spring.datasource.username=postgres
spring.datasource.password=postgres
spring.jpa.hibernate.ddl-auto=update

✨ Features

Clean & modular architecture

Fully containerized microservices

Easy scalability

Uses DTO → Service → Repository pattern

Service discovery (Eureka)

Central API Gateway

PostgreSQL storage

Event-driven communication

Highly maintainable structure

👨‍💻 Author

Kartik Raj
Java Developer — Spring Boot | Microservices | Cloud