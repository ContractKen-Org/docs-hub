# 03 — Data Model

**Entity relationship (ER)**
```mermaid
erDiagram
  TENANT ||--o{ USER : "has"
  USER ||--o{ SESSION : "creates"
  TENANT ||--o{ CONTRACT : "owns"
  CONTRACT ||--|{ CLAUSE : "contains"
  CLAUSE }o--o{ TERM : "references"
```

**Data classification**
- Public / Internal / Confidential / Restricted (PII/PHI).
- Retention & deletion policy.
- Encryption at rest & in transit (KMS keys, TLS versions).