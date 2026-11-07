# Golang Microservices - Clean Architecture



A production-ready microservices boilerplate built with Go, implementing Clean Architecture principles with comprehensive testing, security, and documentation.

## 🏗️ Architecture Overview

### Clean Architecture Layers

```mermaid
graph TB
    subgraph "External Layer"
        UI[Web UI]
        API[REST API]
        DB[(PostgreSQL)]
    end
    
    subgraph "Infrastructure Layer"
        Controllers[REST Controllers]
        Repositories[Repositories]
        Security[JWT Security]
        Logger[Structured Logging]
    end
    
    subgraph "Application Layer"
        AuthUC[Auth Use Cases]
        UserUC[User Use Cases]
        MedicineUC[Medicine Use Cases]
    end
    
    subgraph "Domain Layer"
        Entities[Domain Entities]
        Rules[Business Rules]
        Errors[Domain Errors]
    end
    
    UI --> API
    API --> Controllers
    Controllers --> AuthUC
    Controllers --> UserUC
    Controllers --> MedicineUC
    AuthUC --> Entities
    UserUC --> Entities
    MedicineUC --> Entities
    Repositories --> DB
    AuthUC --> Repositories
    UserUC --> Repositories
    MedicineUC --> Repositories
    Security --> AuthUC
    Logger --> Controllers
    Logger --> Repositories
```

### Dependency Flow

```mermaid
graph LR
    subgraph "Dependencies Point Inward"
        A[Infrastructure] --> B[Application]
        B --> C[Domain]
        A --> C
    end
    
    subgraph "Domain is Independent"
        C --> D[No External Dependencies]
    end
```

