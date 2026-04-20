# CQRS (Command and Query Responsibility Segregation)

## English

CQRS (Command and Query Responsibility Segregation) is an architectural pattern that separates the responsibilities of handling data retrieval (**Query**) and performing state-changing operations (**Request**).

### Key Concepts:
- **Queries**: Designed to retrieve data without altering the system's state. They are purely read-only operations.
- **Requests**: Intended to change the system's state. These operations typically involve creating, updating, or deleting data.

### Data Models:
In CQRS, it's possible to use a single database for both operations (Queries and Requests) or to separate them into two distinct data models, one optimized for reads and the other for writes.

---

## Project Structure

The project follows the CQRS pattern, organized into different layers and components to separate concerns and enhance maintainability:

<pre>
FundamentalsCqrs
├── FundamentalsCqrs.API
│   ├── Controllers
│   ├── Configurations
│   └── appsettings.json
│
├── FundamentalsCqrs.Application
│   ├── Requests
│   ├── Queries
│   ├── EventHandlers
│   ├── DTOs
│   └── Handlers
│
├── FundamentalsCqrs.Domain
│   ├── Entities
│   ├── ValueObjects
│   ├── Aggregates
│   ├── Services
│   ├── Interfaces
│   └── Events
│
├── FundamentalsCqrs.Infrastructure
│   ├── Contexts
│   ├── Mappings
│   ├── Repositories
│   ├── Migrations
│   ├── Integrations
│   └── EventStore
│
└── FundamentalsCqrs.CrossCutting
    ├── Logging
    ├── DependencyInjection
    └── Exceptions
</pre>

### Components Overview:
- **Controllers**: Handle HTTP requests and route them to the appropriate services or handlers.
- **Configurations**: Application configuration settings, including dependency injection and middleware setup.
- **appsettings.json**: Centralized configuration file for application settings, such as connection strings and external service URLs.

- **Requests**: Classes representing actions that alter the state of the system.
- **Queries**: Classes representing read-only operations that retrieve data.
- **EventHandlers**: Classes that handle events triggered by domain actions, typically used for side effects or integration with other systems.
- **DTOs**: Data Transfer Objects used to pass data between different layers of the application.
- **Handlers**: Process Requests and Queries, containing the core business logic.

- **Entities**: Core business objects with unique identities.
- **ValueObjects**: Immutable objects defined by their properties, representing a concept in the domain.
- **Aggregates**: Groups of entities and value objects that are treated as a single unit with consistent state management.
- **Services**: Domain services encapsulate business logic that doesn't naturally belong to any specific entity.
- **Interfaces**: Define contracts for services, repositories, and other dependencies.
- **Events**: Represent significant actions or changes within the domain, used to notify other parts of the system.

- **Contexts**: Database contexts or units of work, responsible for managing data persistence.
- **Mappings**: Configurations for mapping domain entities to database tables and vice versa.
- **Repositories**: Implement data access logic, providing methods to interact with the database.
- **Migrations**: Manage schema changes in the database, ensuring consistency across environments.
- **Integrations**: Handle communication and integration with external systems or services.
- **EventStore**: A specialized storage mechanism for persisting domain events.

- **Logging**: Implements logging mechanisms for monitoring and diagnosing application behavior.
- **DependencyInjection**: Configures and manages the application's dependencies, ensuring loose coupling and testability.
- **Exceptions**: Centralized handling of exceptions, providing consistent error responses and logging.
## Documentation
- [Overview](docs/overview.md)
- [Architecture](docs/architecture.md)
- [Repository Prompt](docs/repository-prompt.md)
