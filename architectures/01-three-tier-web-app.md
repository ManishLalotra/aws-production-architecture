# Architecture 1: Highly Available 3-Tier Enterprise Web Application

## Topology Diagram

```mermaid
graph TD
    User([End User]) -->|DNS Query| Route53[Amazon Route 53]
    Route53 -->|Anycast Routing| CloudFront[Amazon CloudFront CDN / WAF]
    CloudFront -->|Dynamic Requests| ALB[Application Load Balancer (Public Subnets)]
    CloudFront -->|Static S3 Assets| S3Bucket[(Amazon S3 Static Assets)]
    
    subgraph VPC [AWS Virtual Private Cloud (10.0.0.0/16)]
        ALB -->|HTTPS :443| ASG[Auto Scaling Group (EC2 / Private Subnets)]
        
        subgraph AZ1 [Availability Zone 1]
            EC2_1[EC2 Instance 1]
            RDS_Primary[(RDS Multi-AZ Primary)]
        end

        subgraph AZ2 [Availability Zone 2]
            EC2_2[EC2 Instance 2]
            RDS_Standby[(RDS Multi-AZ Standby)]
        end

        ASG --> EC2_1
        ASG --> EC2_2
        EC2_1 --> RDS_Primary
        EC2_2 --> RDS_Primary
        RDS_Primary -.->|Synchronous Replication| RDS_Standby
    end
```

## Security & Resilience
- **WAF Rules**: AWS WAF shields against OWASP Top 10 vulnerabilities, SQL injection, and DDoS.
- **Multi-AZ RDS**: High availability failover in under 60 seconds with zero data loss.
- **Private Subnets**: Compute instances reside in private subnets with egress restricted via NAT Gateways.
