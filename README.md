# aws-production-architecture

> Enterprise production AWS architecture reference implementations featuring Mermaid topologies, Well-Architected Framework reviews, security postures, and cost optimization analyses.

> [!NOTE]
> Architecture specifications are provided as a production-style reference implementation and are not executed automatically in this portfolio repository.

## Architectures Catalog
1. **[01-three-tier-web-app.md](architectures/01-three-tier-web-app.md)**: Route 53 -> CloudFront -> ALB -> Auto Scaling EC2 -> Multi-AZ RDS -> S3.
2. **[02-serverless-jamstack.md](architectures/02-serverless-jamstack.md)**: CloudFront -> S3 -> API Gateway -> Lambda -> DynamoDB.
3. **[03-containerized-ecs-fargate.md](architectures/03-containerized-ecs-fargate.md)**: ECS Fargate Serverless Containers with Aurora Serverless v2 and ElastiCache Redis.
4. **[04-enterprise-cicd-oidc.md](architectures/04-enterprise-cicd-oidc.md)**: Keyless GitHub Actions OIDC integration deploying to Amazon ECR and ECS.

## Author
**Manish Lalotra**  
Full Stack Developer & DevOps Engineer  
*Full Stack Developer | DevOps Engineer | Cloud & Infrastructure Engineer*

## License
MIT License. See [LICENSE](LICENSE) for details.
