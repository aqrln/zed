# Mermaid Diagram Test Suite

A collection of different mermaid diagram types for testing theme color integration.

## Flowchart (Top-Down)

## Flowchart with Subgraphs

```mermaid
flowchart TB
    subgraph Frontend
        A[React App] --> B[State Management]
        B --> C[UI Components]
    end
    subgraph Backend
        D[API Server] --> E[Database]
        D --> F[Cache Layer]
        F --> E
    end
    subgraph Infrastructure
        G[Load Balancer] --> D
        G --> H[CDN]
    end
    C -->|API Calls| G
    H --> A
```

## Sequence Diagram

```mermaid
sequenceDiagram
    participant U as User
    participant C as Client
    participant S as Server
    participant DB as Database

    U->>C: Click login
    C->>S: POST /auth/login
    activate S
    S->>DB: Query user
    activate DB
    DB-->>S: User record
    deactivate DB
    S-->>C: JWT Token
    deactivate S
    C->>C: Store token
    C-->>U: Show dashboard

    Note over U,C: User is now authenticated
    Note right of S: Token expires in 24h

    U->>C: Request data
    C->>S: GET /api/data
    activate S
    S->>DB: Fetch records
    activate DB
    DB-->>S: Results
    deactivate DB
    S-->>C: JSON response
    deactivate S
    C-->>U: Display data
```

## Pie Chart

```mermaid
pie title Language Usage in Project
    "Rust" : 45
    "TypeScript" : 25
    "Python" : 15
    "Go" : 10
    "Other" : 5
```

## Git Graph

```mermaid
gitGraph
    commit id: "init"
    commit id: "add readme"
    branch feature/auth
    checkout feature/auth
    commit id: "add login"
    commit id: "add signup"
    checkout main
    branch feature/api
    checkout feature/api
    commit id: "add endpoints"
    commit id: "add middleware"
    checkout main
    merge feature/auth id: "merge auth"
    merge feature/api id: "merge api"
    commit id: "release v1.0"
```

## State Diagram

```mermaid
stateDiagram-v2
    [*] --> Idle

    Idle --> Processing : Submit
    Processing --> Success : Complete
    Processing --> Error : Fail
    Error --> Idle : Reset
    Success --> Idle : New Task
    Error --> Processing : Retry

    state Processing {
        [*] --> Validating
        Validating --> Executing
        Executing --> [*]
    }

    Success --> [*]
```

## Class Diagram

```mermaid
classDiagram
    class Animal {
        +String name
        +int age
        +makeSound() void
        +move() void
    }
    class Dog {
        +String breed
        +fetch() void
        +bark() void
    }
    class Cat {
        +bool isIndoor
        +purr() void
        +scratch() void
    }
    class Owner {
        +String name
        +List~Animal~ pets
        +adopt(Animal a) void
    }

    Animal <|-- Dog
    Animal <|-- Cat
    Owner "1" --> "*" Animal : owns
```

## Entity Relationship Diagram

```mermaid
erDiagram
    CUSTOMER ||--o{ ORDER : places
    CUSTOMER {
        int id PK
        string name
        string email
    }
    ORDER ||--|{ LINE_ITEM : contains
    ORDER {
        int id PK
        date created_at
        string status
    }
    LINE_ITEM }|--|| PRODUCT : references
    LINE_ITEM {
        int quantity
        float price
    }
    PRODUCT {
        int id PK
        string name
        float base_price
        string category
    }
```

## Gantt Chart

```mermaid
gantt
    title Project Timeline
    dateFormat  YYYY-MM-DD
    excludes    weekends

    section Planning
    Requirements Gathering  :done,    req, 2024-01-01, 10d
    Architecture Design     :done,    arch, after req, 7d

    section Development
    Backend API             :active,  api, after arch, 20d
    Frontend UI             :active,  ui, after arch, 25d
    Database Schema         :         db, after arch, 10d

    section Testing
    Unit Tests              :         unit, after api, 10d
    Integration Tests       :         integ, after unit, 7d
    UAT                     :         uat, after integ, 5d

    section Deployment
    Staging                 :         stg, after uat, 3d
    Production              :milestone, prod, after stg, 0d
```

## Flowchart with Styled Nodes

```mermaid
flowchart LR
    A([Terminal Shape]) --> B[[Subroutine]]
    B --> C[(Database)]
    C --> D((Circle))
    D --> E>Ribbon]
    E --> F{Decision}
    F --> G[/Parallelogram/]
    F --> H[\Reverse Parallelogram\]
    G --> I[/Trapezoid\]
    H --> J[\Reverse Trapezoid/]
```

## Sequence Diagram with Loops and Alternatives

```mermaid
sequenceDiagram
    participant Client
    participant Server
    participant Cache

    Client->>Server: Request resource

    alt Cache hit
        Server->>Cache: Check cache
        Cache-->>Server: Cached data
        Server-->>Client: Return cached response
    else Cache miss
        Server->>Cache: Check cache
        Cache-->>Server: Not found
        Server->>Server: Compute result
        Server->>Cache: Store result
        Server-->>Client: Return fresh response
    end

    loop Every 60 seconds
        Server->>Cache: Refresh stale entries
    end

    opt Debug mode enabled
        Server->>Client: Send debug headers
    end
```

## Flowchart with Long Labels and Edge Labels

```mermaid
flowchart TD
    A[User opens application] -->|Checks authentication state| B{Authenticated?}
    B -->|Valid session token found| C[Load user dashboard]
    B -->|No valid session| D[Show login screen]
    D -->|Enter credentials| E[Validate with server]
    E -->|Success with 200 OK| C
    E -->|Failure with 401| F[Show error message]
    F -->|User retries| D
    C -->|User clicks logout| G[Clear session data]
    G --> D
```
