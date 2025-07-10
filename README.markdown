

```mermaid
erDiagram
    CUSTOMERS ||--o{ DOMAINS : owns
    CUSTOMERS ||--o{ CREDITS : has
    CUSTOMERS ||--o{ CREDIT_LOGS : logs
    DOMAINS ||--o{ VISITORS : tracks
    VISITORS ||--o{ EVENTS : generates
    CREDITS ||--o{ CREDIT_LOGS : tracks

    CUSTOMERS {
        bigint id PK
        varchar email
        varchar password_hash
        varchar name
        boolean is_deleted
        timestamp created_at
        timestamp updated_at
    }

    DOMAINS {
        bigint id PK
        bigint customer_id FK
        varchar domain_name
        boolean is_deleted
        timestamp created_at
        timestamp updated_at
    }

    VISITORS {
        bigint id PK
        bigint domain_id FK
        inet ip_address
        varchar user_agent
        varchar location
        jsonb metadata
        boolean is_deleted
        timestamp created_at
        timestamp updated_at
    }

    EVENTS {
        bigint id PK
        bigint visitor_id FK
        varchar event_type
        jsonb event_data
        boolean is_deleted
        timestamp created_at
        timestamp updated_at
    }

    CREDITS {
        bigint id PK
        bigint customer_id FK
        integer balance
        boolean is_deleted
        timestamp created_at
        timestamp updated_at
    }

    CREDIT_LOGS {
        bigint id PK
        bigint customer_id FK
        bigint credit_id FK
        integer amount
        varchar transaction_type
        boolean is_deleted
        timestamp created_at
        timestamp updated_at
    }
```
 