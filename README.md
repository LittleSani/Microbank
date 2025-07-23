# Microbank: A Java Spring Boot Microservices Application

This project is a demonstration of a microservices architecture for a banking application, built with Java and Spring Boot.

### Installation

1. Clone the repository:

```shell
$ git clone <your-repository-url>
```

2. Navigate to the docker-compose folder:

```shell
$ cd microbank/docker-compose
```
3. Start the application using docker-compose:

```shell
$ docker-compose up -d
```

#### Docker Containers

| Container | IP | Port Mapping |
| --- | --- | --- |
| openzipkin_server | 172.25.0.12 | 9411 |
| keycloak_web | 172.25.0.11 | 8080 |
| keycloak_postgre_db | 172.25.0.10 | 5432(Closed Port) |
| mysql_microbank_app | 172.25.0.9 | 3306 |
| microbank-config-server | 172.25.0.8 | 8090 |
| microbank-service-registry | 172.25.0.7 | 8081 |
| microbank-api-gateway | 172.25.0.6 | 8082 |
| microbank-user-service | 172.25.0.5 | 8083 |
| microbank-fund-transfer-service | 172.25.0.4 | 8084 |
| microbank-utility-payment-service | 172.25.0.3 | 8085 |
| core-banking-service | 172.25.0.2 | 8092 |

### Postman Collection

A Postman collection is available for testing the API.

#### Test Data

By default, dummy account details and user details are available in the `core-banking-database`. The Keycloak instance is also deployed with a default dataset that includes realm, client, and user data.

To begin testing, use the `AUTHENTICATION` API request in the `BANKING_CORE_MICROSERVICES` collection.

```
Test Credentials: admin@microbank.com / password
```

### Microservices in This Project

This project consists of the following microservices:

*   **User Service (`microbank-user-service`)**: Manages user operations, including registration and retrieval. It uses Keycloak for user management and a local PostgreSQL database.
*   **Fund Transfer Service (`microbank-fund-transfer-service`)**: Handles fund transfers between accounts and sends messages to a centralized RabbitMQ queue for the Notification service.
*   **Payment Service (`microbank-utility-payment-service`)**: Processes utility payments and sends notification messages to RabbitMQ.
*   **Notification Service**: Consumes messages from RabbitMQ and sends notifications to users. (PENDING Development)
*   **Banking Core Service**: A dummy banking core that manages accounts, users, transaction details, and processes banking transactions.

### Technology Stack

*   Java 21
*   Spring Boot 3.2.4
*   Spring Cloud 2023.0.0
*   Netflix Eureka Service Registry
*   Netflix Eureka Service Client
*   Spring Cloud API Gateway
*   Spring Cloud Config Server
*   Zipkin
*   Spring Cloud Sleuth
*   Open Feign
*   RabbitMQ
*   Prometheus
*   MySQL
*   Keycloak
*   Docker / Docker Compose
*   Kubernetes