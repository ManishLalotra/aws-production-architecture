# Architecture 3: Containerized Microservices Platform (ECS Fargate)

```mermaid
graph TD
    Client([Consumer]) --> ALB[Application Load Balancer]
    ALB --> FargateTasks[ECS Fargate Tasks (Serverless Containers)]
    FargateTasks --> Aurora[(Amazon Aurora PostgreSQL Serverless v2)]
    FargateTasks --> ElastiCache[(Amazon ElastiCache Redis Cluster)]
    FargateTasks --> SecretsManager[AWS Secrets Manager]
```
