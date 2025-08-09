# 02 — Architecture

## Container view (C2)
```mermaid
flowchart TB
  subgraph Client
    A[SPA / Web Client] --> B[Auth SDK]
  end
  subgraph Backend
    C[API Gateway / BFF]
    D[Service A]
    E[Service B]
  end
  subgraph Data
    F[(PostgreSQL)]
    G[(Redis)]
    H[(Object Storage)]
  end
  subgraph Async
    I((Kafka / SQS))
    J[Worker]
  end

  A -->|HTTPS| C
  C --> D
  C --> E
  D --> F
  E --> F
  D --> G
  E --> H
  D -->|events| I
  I --> J
  J --> F
```

## Component view (C3) — example service
```mermaid
flowchart LR
  Controller --> ServiceLayer --> Repository
  ServiceLayer --> "Policy/Playbook Engine"
  Repository -->|ORM| PostgreSQL[(PostgreSQL)]
```

## Key request flow (sequence)
```mermaid
sequenceDiagram
  participant U as User
  participant W as Web App
  participant A as API Gateway
  participant S as Service A
  participant DB as DB

  U->>W: Click "Analyze"
  W->>A: POST /analyze (JWT)
  A->>S: Forward request
  S->>DB: Read inputs
  S-->>A: Result
  A-->>W: 200 OK + JSON
```

> Replace placeholders with your actual services and names. Keep diagrams code-based so they live with the repo.