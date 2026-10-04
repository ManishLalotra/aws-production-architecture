# Architecture 2: Serverless Jamstack Static Platform

```mermaid
graph LR
    Client([Client Browser]) --> Route53[Route 53]
    Route53 --> CloudFront[CloudFront Edge Locations]
    CloudFront -->|Cached Assets| S3[(S3 Website Bucket)]
    CloudFront -->|API Invocations| APIGW[API Gateway HTTP API]
    APIGW --> Lambda[AWS Lambda Microservices]
    Lambda --> DynamoDB[(Amazon DynamoDB On-Demand)]
```

## Highlights
- Sub-50ms global latency via CloudFront edge caching.
- Zero server maintenance, automated scaling, and pay-per-request pricing.
