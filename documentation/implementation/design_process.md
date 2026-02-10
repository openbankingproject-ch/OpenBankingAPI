## Technology choices
### Java
Java was mainly chosen because of its robust type system and because in most open banking implementations
we analyzed Java was the language of choice. 

It also has a strong ecosystem and tooling for handling the security needs of an open banking project.

Java supports multi threading for doing cryptographic calculations in a non blocking way.

There is also a lot of developers that are familiar with Java. Java is also often used to teach programming
in Business Computer Science Programs.

### Maven
We chose Maven as the build system because we have more experience with it compared to Gradle.

### Javalin
Javalin was chosen because it is more lightweight than Spring which we determined was a positive aspect.
This is because the main complexity in the API is the security and consent flow. This means we want everything
that is not consent and security to be as simple as possible.

## Architecture 

### Class diagram

```mermaid
classDiagram
    direction TB

    %% Application Entry and Configuration
    class App {
        +main(args: String)
        +setupServer() Javalin
    }

    class ApiConfig {
        +PORT: int
        +configure(app: Javalin)
    }

    %% Presentation Layer (Handlers/Controllers)
    class CustomerHandler {
        -CustomerService customerService
        -AuthService authService
        +getAll(ctx: Context)
        +getOne(ctx: Context)
    }

    class RelationshipHandler {
        -RelationshipService relationshipService
        -ConsentService consentService
        +getRelationships(ctx: Context)
    }

    %% Security & Compliance Services
    class AuthService {
        +validateToken(token: String) UserPrincipal
        +hasRole(principal: UserPrincipal, role: String) boolean
    }

    class ConsentService {
        -ConsentRepository consentRepo
        +hasActiveConsent(customerId: String, scope: String) boolean
        +updateConsent(customerId: String, preferences: ConsentDTO)
    }

    %% Application Layer (Business Services)
    class CustomerService {
        -CustomerRepository customerRepo
        +getCustomerDetails(id: String) CustomerResponse
    }

    class RelationshipService {
        -RelationshipRepository relationRepo
        +get360Overview(id: String) RelationshipOverview
    }

    %% Persistence Layer (Infrastructure)
      class CustomerRepository {
        <<interface>>
        +findById(id: String) CustomerEntity
        +save(customer: CustomerEntity)
        +findAll() List~CustomerEntity~
    }
    class RelationshipRepository { <<interface>> }
    
    class ConsentRepository {
        <<interface>>
        +findLatestByCustomerId(id: String) ConsentEntity
        +save(consent: ConsentEntity)
    }

        class CustomerResponse {
        <<record>>
        +String id
        +String fullName
        +String email
        +List~AddressDTO~ addresses
    }

    class CreateCustomerRequest {
        <<record>>
        +String firstName
        +String lastName
        +String email
        +AddressDTO initialAddress
    }

    %% Domain Entities
    class CustomerEntity {
        -String internalId
        -String firstName
        -String lastName
        -String status
        -LocalDateTime createdAt
    }

    %% Relationships
    App --> ApiConfig : uses
    ApiConfig --> CustomerHandler : registers
    ApiConfig --> RelationshipHandler : registers
    
    %% Security Wiring
  
    RelationshipHandler --> AuthService : authenticates
    RelationshipHandler --> ConsentService : verifies privacy
    
    CustomerHandler --> CustomerService : delegates
    RelationshipHandler --> RelationshipService : delegates
    CustomerHandler --> AuthService : authenticates
    CustomerService --> CustomerRepository : uses
    RelationshipService --> RelationshipRepository : uses
    ConsentService --> ConsentRepository : uses
    CustomerService..> CustomerResponse : returns
    CustomerService..> CreateCustomerRequest : accepts
    CustomerRepository..> CustomerEntity : manages```
