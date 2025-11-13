# WAD

```mermaid
graph TB
    Client[Frontend Client<br/>HTML / CSS / JS] --> Gateway[API Gateway<br/>Express.js]
    
    Gateway --> CS[Customer Service<br/>Menu, Cart, Order]
    Gateway --> PS[Provider Service<br/>Menu Management & Delivery]
    
    %% Inter-service communication (optional if needed)
    CS -.->|HTTP Request/Response| PS
    PS -.->|HTTP Request/Response| CS
    
    subgraph ServiceLayer [Service Layer]
        CS
        PS
    end

    subgraph DataLayer [Data Layer (SQLite)]
        CDB[(customer.db)]
        PDB[(provider.db)]
    end
    
    CS --> CDB
    PS --> PDB

```

