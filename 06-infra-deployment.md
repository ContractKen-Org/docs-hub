# 06 — Infrastructure & Deployment

**Environments**
- Dev / Stage / Prod; promotion path; feature flags.

**Cloud topology**
```mermaid
flowchart LR
  Internet --> CDN[CDN/WAF]
  CDN --> ALB[Ingress/ALB]
  ALB --> ECS[ECS/K8s]
  ECS --> SVC1[Service A]
  ECS --> SVC2[Service B]
  SVC1 --> DB[(RDS/Cloud SQL)]
  SVC1 --> Cache[(Redis/Memcached)]
  SVC2 --> Queue((SQS/Kafka))
  Queue --> Worker[Worker Fleet]
  Worker --> Obj[(Object Storage)]
```

**IaC**
- Terraform/CDK/ARM locations; state management; review process.

**CI/CD**
- Build, test, scan, sign images; deploy with canary/blue-green; rollback strategy.