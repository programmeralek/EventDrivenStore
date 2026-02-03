## 2. What Actually Gets Deployed

The system is deployed in two clearly separated layers:

### 2.1 Infrastructure Layer

These components are deployed first and are considered **long-lived runtime dependencies**:

| Component | Responsibility |
|---------|----------------|
| Kafka | Event backbone for asynchronous communication |
| Zookeeper | Kafka cluster coordination |
| Eureka Server | Service discovery |
| Databases | Per-service persistence |

These components:
- Change infrequently
- Are shared across services
- Can be replaced with managed cloud services without modifying application code

---

### 2.2 Service Layer

Each domain service is deployed independently as its own container:

| Service | Runtime | Responsibility |
|-------|--------|----------------|
| Orders Service | Java 25 / Spring Boot | Order creation, lifecycle, and domain events |
| Inventory Service | .NET 9 | Stock ownership and reservation decisions |
| Billing Service | Node.js | Payment workflows and billing events |
| Gateway | Spring Cloud Gateway | External entry point and routing |

Each service:
- Has its own Dockerfile
- Owns its database schema
- Registers itself with Eureka
- Communicates with other services via Kafka events

There is no shared deployment unit across services.
