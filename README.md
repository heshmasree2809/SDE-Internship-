## Distributed event-driven microservices
> Java, Spring Boot, Kafka, Elasticsearch, PostgreSQL, Prometheus, Grafana, Logstash, Kibana

### Introduction
**A distributed event-driven microservices project using Spring boot, Spring cloud, Kafka and Elasticsearch**
- Implemented CQRS and event sourcing pattern in Spring Boot, Spring Cloud, Apache Kafka, and Elasticsearch
- Utilized mock streaming tweets as source data and Docker for microservices cont# Distributed Event-Driven Microservices Platform

A distributed microservices application built with Java, Spring Boot, Spring Cloud, Apache Kafka, and Elasticsearch, developed as part of a **3-month online internship at OracleHub (June–September 2026)**.

## Internship Experience

**Organization:** OracleHub
**Duration:** June 2026 – September 2026
**Mode:** Online
**Project:** Distributed Event-Driven Microservices Platform

During my internship, I worked on a distributed application demonstrating event-driven communication, microservices architecture, asynchronous data processing, and search-oriented data retrieval. The project uses simulated Twitter data to demonstrate how events can flow between independently deployed services.

## Technology Stack

* **Programming Language:** Java
* **Backend Framework:** Spring Boot
* **Microservices & Configuration:** Spring Cloud
* **Event Streaming:** Apache Kafka
* **Search & Data Indexing:** Elasticsearch
* **Build Tool:** Maven
* **Containerization:** Docker and Docker Compose

## Project Overview

The application demonstrates an event-driven architecture in which individual services communicate through Kafka rather than relying exclusively on synchronous HTTP requests.

The workflow begins with simulated Twitter data, publishes events to Kafka, processes the events through a consumer service, indexes the resulting data in Elasticsearch, and exposes an API for querying the indexed information.

### Key Features

* **Event-driven communication:** Uses Apache Kafka to transfer events between independent services.
* **Microservices architecture:** Separates data ingestion, event processing, and search functionality into individual services.
* **Elasticsearch integration:** Indexes processed events to support search and retrieval.
* **Centralized configuration:** Uses Spring Cloud Config to externalize application configuration.
* **API versioning:** Demonstrates content negotiation using HTTP `Accept` headers.
* **Containerization:** Includes Docker-related configuration for running services in a containerized environment.
* **Modular codebase:** Organizes common configuration, shared utilities, and service-specific components into separate modules.

## Architecture and Data Flow

The application follows this general event-processing workflow:

1. **Data Ingestion:** `twitter-to-kafka-service` generates or receives simulated Twitter data.
2. **Event Streaming:** Apache Kafka transports events between the producer and consumer services.
3. **Event Processing:** `kafka-to-elastic-service` consumes Kafka events and forwards processed data for indexing.
4. **Data Indexing:** Elasticsearch stores the indexed event data.
5. **Search and Retrieval:** `elastic-query-service` exposes functionality for querying indexed information.
6. **Web Client:** `elastic-query-web-client` provides a separate web-client module for interacting with the search functionality.

```text
Simulated Twitter Data
          |
          v
twitter-to-kafka-service
          |
          v
     Apache Kafka
          |
          v
  kafka-to-elastic-service
          |
          v
     Elasticsearch
          |
          v
   elastic-query-service
          |
          v
  Search Results / API Client
```

The diagram represents the intended application workflow. Individual service capabilities depend on their current implementation and configuration.

## Project Structure

```text
Event_driven_microservices/
├── app-config-data/
├── common-config/
├── common-util/
├── config-server/
├── config-server-repository/
├── docker-compose/
├── elastic/
├── elastic-query-service/
├── elastic-query-web-client/
├── kafka/
├── kafka-to-elastic-service/
├── twitter-to-kafka-service/
├── pom.xml
├── mvnw
├── mvnw.cmd
└── README.md
```

### Core Services

| Service                    | Responsibility                                                               |
| -------------------------- | ---------------------------------------------------------------------------- |
| `twitter-to-kafka-service` | Produces simulated Twitter events for downstream processing.                 |
| `kafka-to-elastic-service` | Consumes Kafka events and integrates with Elasticsearch.                     |
| `elastic-query-service`    | Provides search and retrieval functionality for indexed data.                |
| `elastic-query-web-client` | Contains the web-client component for interacting with search functionality. |
| `config-server`            | Provides centralized application configuration.                              |
| `common-config`            | Holds shared configuration components.                                       |
| `common-util`              | Provides reusable utilities for the application.                             |

## Design Concepts

### Event-Driven Architecture

Kafka decouples event producers from consumers, allowing services to process events independently and reducing the need for direct synchronous communication between components.

### CQRS

Command Query Responsibility Segregation separates operations that modify application state from operations that retrieve information. This project explores CQRS concepts through its event-processing and query-service design.

### Event Sourcing Concepts

The event-streaming workflow demonstrates the role of events in distributed processing. A complete event-sourced implementation would additionally require durable event history and mechanisms for reconstructing application state; these capabilities should be verified separately.

### API Versioning

HTTP content negotiation using the `Accept` header demonstrates an approach to exposing different API representations or versions without necessarily changing the resource URL.

### Centralized Configuration

The Spring Cloud Config components support separating application configuration from individual service implementations.

## Running the Project

### Prerequisites

Install the following tools before attempting to run the application:

* Java Development Kit compatible with the project's Maven configuration
* Maven, or use the included Maven Wrapper
* Docker Desktop
* Git

### Clone the Repository

```bash
git clone https://github.com/heshmasree2809/SDE-Internship-.git
cd SDE-Internship-
```

### Build the Project

On Windows:

```bat
mvnw.cmd clean package
```

On Linux or macOS:

```bash
./mvnw clean package
```

### Start the Services

Review the Docker Compose configuration and service-specific application settings before starting the application.

If the Compose configuration is complete and configured for your environment, run:

```bash
docker compose up --build
```

**Note:** The exact startup sequence, required environment variables, service ports, and dependency configuration may vary. Consult the configuration files for the current setup.

## Skills and Learning Outcomes

Through this project, I gained practical experience working with:

* Java and Spring Boot application development
* Microservices design and service separation
* Apache Kafka event producers and consumers
* Elasticsearch integration and search-oriented data access
* Spring Cloud centralized configuration
* Maven-based builds and dependency management
* Docker-based development environments
* Distributed application workflows and asynchronous communication

## Future Enhancements

The following items represent potential improvements and should be marked complete only after they have been implemented and tested.

* [ ] Complete and improve the reactive Elasticsearch web client.
* [ ] Add authentication and authorization.
* [ ] Implement Kafka Streams state-store functionality.
* [ ] Integrate PostgreSQL for analytics and persistent relational data.
* [ ] Add service discovery using Netflix Eureka.
* [ ] Implement a Spring Cloud API Gateway with Redis-based rate limiting.
* [ ] Integrate Prometheus and Grafana for metrics and dashboards.
* [ ] Expand centralized logging with Logstash and Kibana.
* [ ] Add automated integration tests and a CI/CD pipeline.

## Repository

**GitHub:** https://github.com/heshmasree2809/SDE-Internship-

## Acknowledgment

This project was developed and explored during my online internship at OracleHub from June to September 2026. It reflects my practical learning in Java, Spring Boot, event-driven systems, Kafka, Elasticsearch, and distributed application development.
ainerization
- Adopted accept header/ content negotiation pattern for API versioning
- Externalized configuration in a separate [config server repository](https://github.com/alimhtsai/spring-cloud-config-server-repository)

### Event-driven Microservices Architecture

![microservices_20240528](https://github.com/alimhtsai/Event_driven_microservices/assets/48788292/63580b33-5ef0-492c-bfc2-76be5739a188)

### Live Demo
- Containerization of three microservices with docker images:
  - twitter-to-kafka-service
  - kafka-to-elastic-service
  - elastic-query-service

https://github.com/alimhtsai/Event_driven_microservices/assets/48788292/e9fc58a3-5658-49b6-857e-3ed04398fd05

### TODO
- [x] Elastic query service
- [ ] Reactive elastic web client service
- [ ] Security
- [ ] Kafak stream state store
- [ ] Postgres analytics store
- [ ] Netflex Eureka discovery service
- [ ] Spring API gateway & Redis rate limiter
- [ ] Monitored microservices with Prometheus, Grafana, and ELK stack (Elasticsearch, Logstash and Kibana)
