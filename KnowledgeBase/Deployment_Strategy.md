# Deployment Strategy

## 1. Core Deployment Philosophy

The deployment strategy is built on three principles:

### Principle #1 - Service Autonomy

#### Each service:
* Has its own runtime
* Has its own Dockerfile
* Can be deployed, restarted, scaled, or replaced independently

There is no shared deployment unit.

####  This is why I explicitly rejected:
* A single giant docker-compose.yml for all projects
* A monorepo-style “bring everything up together” approach for this project

### Principle #2 - Infrastructure as Contracts, Not Coupling

I separated infrastructure concerns into reusable building blocks:
```
infrastructure/
├── kafka-compose.yml
├── eureka-compose.yml
├── mysql-orders-compose.yml
├── mssql-inventory-compose.yml
├── mariadb-billing-compose.yml
```
Each file represents: 

* A runtime dependency
* Not a service implementation

 This allows us to:
* Run infra locally via Compose
* Replace it later with managed services (MSK, RDS, Azure SQL, etc.)
* Keep services unchanged

