# EventDrivenStore

EventDrivenStore is a polyglot, distributed system composed of independent bounded contexts, designed to demonstrate the design, implementation, and operation of a production type event driven architecture.

The system emphasizes service autonomy through deliberate domain partitioning, transactional integrity via relational databases, asynchronous communication, and reproducible infrastructure across multiple languages, frameworks, platforms, and runtimes, reflecting real-world distributed system design and engineering practices.


## Components (Repositories)

| Component | Repo | Responsibility | Tech |
|---|---|---|---|
| Orders Service | [`eds-orders`](https://github.com/programmeralek/eds-orders) | Owns order creation and persistence, and emits immutable domain events | Java 25 / Spring Boot / MySQL |
| Inventory Service | [`eds-inventory`](https://github.com/programmeralek/eds-inventory) | Owns inventory state and stock decisions, reacting to order-related domain events | .NET / C# / MariaDB |
| Billing Service | [`eds-billing`](https://github.com/programmeralek/eds-billing) | Owns billing and payment workflows, reacting asynchronously to domain events | Node.js / Docker / MSSQL |
