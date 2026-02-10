This file outlines and documents the architecture that was chosen for the Open-API. Why these decisions were made
is documented in [[designprocess]].

## Technologies
The API will be written in **Java** with the JDK version being the LTS version 25 [OpenJDK](https://jdk.java.net/25/) 

The build system is [Maven](https://maven.apache.org/)

The framework [Javalin](https://javalin.io/) is used to simplify the building of the API. 

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
        +getRelationshipOverview(id: String) RelationshipOverview
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
    CustomerRepository..> CustomerEntity : manages
```

