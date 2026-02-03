# EventDrivenStore

EventDrivenStore is a polyglot, distributed system composed of independent bounded contexts, designed to demonstrate the design, implementation, and operation of a production type event driven architecture.

The system emphasizes service autonomy through deliberate domain partitioning, transactional integrity via relational databases, asynchronous communication, and reproducible infrastructure across multiple languages, frameworks, platforms, and runtimes, reflecting real-world distributed system design and engineering practices.


## Components (Repositories)

| Component | Repo | Responsibility | Tech |
|---|---|---|---|
| Orders Service | [`eds-orders`](https://github.com/programmeralek/eds-orders) | Owns order creation and persistence, and emits immutable domain events | Java 25 / Spring Boot / MySQL |
| Inventory Service | [`eds-inventory`](https://github.com/programmeralek/eds-inventory) | Owns inventory state and stock decisions, reacting to order-related domain events | .NET / C# / MSSQL |
| Billing Service | [`eds-billing`](https://github.com/programmeralek/eds-billing) | Owns billing and payment workflows, reacting asynchronously to domain events | Node.js / Docker / MariaDB |


## Overview of Distributed System Ownership


### 1.	Client → Gateway
####	•	Synchronous HTTP boundary
####	•	Routing resolved dynamically via Eureka
### 2.	Gateway → Domain Services
####	•	No hardcoded URLs
####	•	Service discovery enables elasticity
### 3.	Domain Services → Kafka
####	•	Domain events are emitted, not commands
####	•	Services never call each other directly
### 4.	Kafka → Domain Services
####	•	Services consume only what they own
####	•	No shared state, no implicit dependencies
### 5.	Each Service → Its Own Database
####	•	Local transactions only
####	•	State changes are private and protected

Each of these specifications can be validated through the following diagram:

![Overview](https://github.com/programmeralek/EventDrivenStore/blob/main/EDS_Architecturial_Diagram.drawio.png)

## Design Patterns & Architectural Principles Demonstrated

This project intentionally demonstrates multiple distributed-systems design patterns, each implemented end-to-end in a realistic, production-style manner.

#### 1. Event-Droven Architecture
#### 2. Saga Pattern (Choreography Based)
#### 4. Database-per-Service
#### 4. Outbox Pattern (Transactional Messaging)
#### 5. Idempotent Consumers (ACID Principles)
#### 6. Polyglot Microservices


Each pattern is described using the STAR methodology (Situation, Task, Action, Result) to clearly articulate design intent and outcomes in a detailled manner in 
<a href="https://github.com/programmeralek/EventDrivenStore/blob/main/STAR_specified_design_patterns.md" target="_blank">STAR_specified_design_patterns.md</a>

