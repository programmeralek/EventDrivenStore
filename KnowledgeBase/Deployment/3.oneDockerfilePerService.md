## 3. One Dockerfile per Service

Each service defines its own Dockerfile:

- orders-service/
Dockerfile

- inventory-service/
Dockerfile

- billing-service/
Dockerfile

- gateway/
Dockerfile

This approach ensures:

- Independent build pipelines
- Independent versioning
- Independent rollbacks
- Independent scaling strategies

This enables:
-	Rolling deployments
-	Blue/green deployments
-	Canary releases
-	Independent rollback


A service can be rebuilt, redeployed, or replaced without impacting the rest of the system.

This is a foundational requirement for microservice autonomy.
