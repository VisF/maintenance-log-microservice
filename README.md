# Maintenance Log Microservice

A RESTful microservice built with **Java and Spring Boot** for recording and storing maintenance logs in **MongoDB**.

The service exposes an HTTP endpoint that receives maintenance reports and persists them as MongoDB documents.

## Overview

This project implements a lightweight backend service for managing maintenance records associated with electric scooters.

Each maintenance log stores information such as:

* Scooter identifier
* Maintenance report
* Date and time
* Unique document identifier

The application demonstrates the implementation of a Spring Boot microservice using a layered architecture and MongoDB for persistence.

## Architecture

The application follows a simple layered architecture:

```text
Client
  │
  ▼
REST Controller
  │
  ▼
Service Layer
  │
  ▼
Repository
  │
  ▼
MongoDB
```

### Layers

**Controller**

Handles HTTP requests and exposes the REST endpoint for creating maintenance logs.

**Service**

Contains the application logic and coordinates the persistence operation.

**Repository**

Provides the persistence abstraction for MongoDB using Spring Data.

**Model**

Defines the MongoDB document representing a maintenance log.

The project structure reflects these responsibilities through dedicated `controller`, `service`, `repository`, and `model` packages.

## API

### Create Maintenance Log

```http
POST /logMantenimientos/
```

Example request:

```json
{
  "idMonopatin": 101,
  "reporte": "Brake inspection and adjustment",
  "fecha": "2024-11-20T14:30:00"
}
```

The request is received by the REST controller and passed to the service layer for persistence.

## Data Model

Maintenance logs are stored as MongoDB documents.

```text
Log
├── id
├── idMonopatin
├── reporte
└── fecha
```

The `Log` model is mapped to the MongoDB `Log` collection using Spring Data MongoDB.

## Technology Stack

* **Java 17**
* **Spring Boot 3.3.5**
* **Spring Web**
* **Spring Data MongoDB**
* **MongoDB**
* **Lombok**
* **Maven**
* **Docker**

The project is configured as a Maven application using the Spring Boot parent and includes the Spring Web, Spring Data MongoDB and testing dependencies.

## Project Structure

```text
maintenance-log-microservice/
│
├── src/
│   └── main/
│       ├── java/
│       │   └── ar/edu/cresta/
│       │       ├── controller/
│       │       │   └── LogController.java
│       │       │
│       │       ├── model/
│       │       │   └── Log.java
│       │       │
│       │       ├── repository/
│       │       │   └── LogRepositoryInterface.java
│       │       │
│       │       ├── service/
│       │       │   └── LogService.java
│       │       │
│       │       └── MongoLogsApplication.java
│       │
│       └── resources/
│           └── application.properties
│
├── Dockerfile
├── pom.xml
└── README.md
```

## Running Locally

### Requirements

* Java 17+
* Maven
* MongoDB

### Clone the repository

```bash
git clone https://github.com/VisF/maintenance-log-microservice.git
cd maintenance-log-microservice
```

### Configure MongoDB

Make sure a MongoDB instance is running and configure the connection in:

```text
src/main/resources/application.properties
```

### Run the application

Using Maven:

```bash
./mvnw spring-boot:run
```

Or, if Maven is installed globally:

```bash
mvn spring-boot:run
```

The application can then receive requests through its REST endpoint.

## Docker

The repository also includes a Dockerfile configured for MongoDB.

```bash
docker build -t maintenance-log-mongodb .
docker run -p 27017:27017 maintenance-log-mongodb
```

The container exposes MongoDB on port `27017`.

## What This Project Demonstrates

This project was developed to practice and demonstrate:

* REST API development with Spring Boot
* Layered backend architecture
* Dependency Injection
* Spring Data MongoDB
* NoSQL persistence
* REST controllers
* Service and repository separation
* Maven-based project configuration
* Docker fundamentals

## Project Context

This microservice was developed as part of a distributed application architecture exercise, where maintenance information is handled as an independent service.

The project focuses on separating maintenance-log functionality from other application responsibilities through a dedicated backend service.

## Author

**Facundo Vis**

Full Stack Developer focused on Java, Spring Boot, software architecture, REST APIs, databases, and modern web development.

* GitHub: https://github.com/VisF
* LinkedIn: https://www.linkedin.com/in/facundo-vis/
