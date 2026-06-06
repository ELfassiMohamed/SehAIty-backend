# SehAIty Backend

### Overview

SehAIty Backend is a Spring Boot microservices platform for coordinating healthcare interactions between patients and providers. It includes authentication, patient/provider management, medical records, patient requests, notifications, and medical certificate generation.

### Architecture

![SehAIty Architecture](https://sehaity-main-architecture.mohamed-el-fassi.workers.dev/)

The project is split into independent services:

| Service | Port | Role |
| --- | ---: | --- |
| Gateway-Service | 8080 | API entry point and routing |
| Eureka-Server | 8761 | Service discovery |
| Config-server | 8888 | Centralized configuration |
| Patient-Service | 8081 | Patient accounts, profiles, requests, notifications |
| Provider-Service | 8082 | Provider accounts, patient assignment, medical record creation |
| Medicalrecord-Service | 8083 | Medical record storage and access |
| Request-Service | 8084 | Patient requests, provider responses, certificates |

External dependencies:

| Dependency | Default port | Purpose |
| --- | ---: | --- |
| MongoDB | 27017 | Database |
| RabbitMQ | 5672 | Asynchronous messaging |
| RabbitMQ Management | 15672 | RabbitMQ dashboard |

### Main Features

- JWT authentication for patients and providers
- Patient profile and account status management
- Provider registration and patient assignment
- Medical record creation and access
- Patient request/response workflow
- Email notifications
- Medical certificate creation and PDF export
- Service discovery with Eureka
- Centralized configuration with Spring Cloud Config

### Prerequisites

- Java 17+
- Maven 3.6+
- MongoDB
- RabbitMQ
- Docker, optional for running infrastructure

### Run Order

Start the services in this order:

```bash
cd Eureka-Server
mvn spring-boot:run
```

```bash
cd Config-server
mvn spring-boot:run
```

```bash
cd Patient-Service
mvn spring-boot:run
```

```bash
cd Provider-Service
mvn spring-boot:run
```

```bash
cd Medicalrecord-Service
mvn spring-boot:run
```

```bash
cd Request-Service
mvn spring-boot:run
```

```bash
cd Gateway-Service
mvn spring-boot:run
```

### Useful URLs

- API Gateway: `http://localhost:8080`
- Eureka Dashboard: `http://localhost:8761`
- Config Server: `http://localhost:8888`
- RabbitMQ Dashboard: `http://localhost:15672`
- Swagger UI:
  - Patient-Service: `http://localhost:8081/swagger-ui/index.html`
  - Provider-Service: `http://localhost:8082/swagger-ui/index.html`
  - Medicalrecord-Service: `http://localhost:8083/swagger-ui/index.html`
  - Request-Service: `http://localhost:8084/swagger-ui/index.html`

### Configuration Notes

Configuration files are stored in:

```text
Config-server/config-repo/
```

Before using this project outside local development, move secrets such as JWT keys, RabbitMQ credentials, and mail credentials to environment variables or a secret manager.

---
