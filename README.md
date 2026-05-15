# SehAIty Backend

## English

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

## Francais

### Apercu

SehAIty Backend est une plateforme de microservices Spring Boot pour faciliter la coordination entre patients et prestataires de sante. Elle couvre l'authentification, la gestion des patients et prestataires, les dossiers medicaux, les demandes patient, les notifications et la generation de certificats medicaux.

### Architecture

![Architecture SehAIty](https://sehaity-main-architecture.mohamed-el-fassi.workers.dev/)

Le projet est compose de plusieurs services independants:

| Service | Port | Role |
| --- | ---: | --- |
| Gateway-Service | 8080 | Point d'entree API et routage |
| Eureka-Server | 8761 | Decouverte des services |
| Config-server | 8888 | Configuration centralisee |
| Patient-Service | 8081 | Comptes patients, profils, demandes, notifications |
| Provider-Service | 8082 | Comptes prestataires, assignation patients, creation de dossiers |
| Medicalrecord-Service | 8083 | Stockage et acces aux dossiers medicaux |
| Request-Service | 8084 | Demandes patient, reponses prestataires, certificats |

Dependances externes:

| Dependance | Port par defaut | Utilisation |
| --- | ---: | --- |
| MongoDB | 27017 | Base de donnees |
| RabbitMQ | 5672 | Messagerie asynchrone |
| RabbitMQ Management | 15672 | Tableau de bord RabbitMQ |

### Fonctionnalites principales

- Authentification JWT pour patients et prestataires
- Gestion des profils et statuts patients
- Inscription des prestataires et assignation des patients
- Creation et consultation des dossiers medicaux
- Systeme de demandes et reponses
- Notifications par email
- Creation de certificats medicaux et export PDF
- Decouverte des services avec Eureka
- Configuration centralisee avec Spring Cloud Config

### Prerequis

- Java 17+
- Maven 3.6+
- MongoDB
- RabbitMQ
- Docker, optionnel pour lancer l'infrastructure

### Ordre de demarrage

Lancer les services dans cet ordre:

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

### URLs utiles

- API Gateway: `http://localhost:8080`
- Eureka Dashboard: `http://localhost:8761`
- Config Server: `http://localhost:8888`
- RabbitMQ Dashboard: `http://localhost:15672`
- Swagger UI:
  - Patient-Service: `http://localhost:8081/swagger-ui/index.html`
  - Provider-Service: `http://localhost:8082/swagger-ui/index.html`
  - Medicalrecord-Service: `http://localhost:8083/swagger-ui/index.html`
  - Request-Service: `http://localhost:8084/swagger-ui/index.html`

### Notes de configuration

Les fichiers de configuration sont dans:

```text
Config-server/config-repo/
```

Avant d'utiliser ce projet hors developpement local, deplacer les secrets comme les cles JWT, les identifiants RabbitMQ et les identifiants email vers des variables d'environnement ou un gestionnaire de secrets.
