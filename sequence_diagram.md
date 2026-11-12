# Streamy POST /users Registration Sequence Flow

## 1. Sequence Diagram
```mermaid
sequenceDiagram
    autonumber
    participant C as UserController
    participant S as CreateUserService
    participant R as UserRepository
    participant M as WelcomeEmailService
    participant E as EventPublisher
    
    C->>+S: create_user(email: String): Result
    S->>R: find_by_email(email: String): User[]
    R-->>S: existingUsers: User[]
    loop each existingUser
        S->>S: is_active(existingUser): Boolean
    end
    alt active account exists
        S-->>C: conflict: RegistrationError
    else registration permitted
        S->>R: insert_user(email: String): User
        R-->>S: newUser: User
        par welcome email
            S->>M: send_welcome_email(newUser): Boolean
            M-->>S: emailAccepted: Boolean
        and creation event
            S->>E: publish_user_created(newUser): Boolean
            E-->>S: eventAccepted: Boolean
        end
        S-->>C: newUser: User
    end
    deactivate S
    
```
### Architectural Analysis & Code Smells

1. **Leaky Abstractions**: Iterating over all matched users in the application layer to identify active accounts can be inefficient and leaks database filtering logic into the service. In a production environment, it is recommended to use a dedicated repository method such as `exists_active_by_email(email)`, supported by proper database uniqueness rules[cite: 20].
2. **Side-Effect Coupling**: Sending welcome emails and publishing domain events synchronously during the user registration process makes retries and partial failures difficult to handle. To improve resilience, consider decoupling these operations using an event-driven worker or a transactional outbox pattern for reliable message delivery[cite: 20].
```