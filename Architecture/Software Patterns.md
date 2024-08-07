### What are Software Architectural Patterns
- Are general repeatable solutions to commonly occurring system design problems.
- Common solutions to software architectural problems that involve multiple components that run as separate runtime units.

### Incentives for using Software Architectural Patterns
- Save valuable time and resources.
- Avoid making our architecture resemble a Big Ball of Mud.
- Other engineers and architects can follow it.

## Multi-Tier Architecture
- Logical separation - limits the scope of responsibility on each tier.
- Physical separation - Allows each tier to be separately developed, upgraded, scaled.

### Three-Tier Architecture
- Most common and popular architectural pattern for client-server web-based services.
- Presentation Tier - is the top level that contains the user interface.
    - Display information to the user
    - Take the user's input
    - webpage, mobile app or desktop app.
    - It does not contain any business logic.
    - The code that runs in the client's browser is accessible and visible to the user.
    - It is an anti-pattern to include any business logic.
- Application Tier or Logic Tier
    - Provides all the functionality and features.
    - Responsible for processing the data that comes from the Presentation Tier.
    - Responsible for applying the relevant business logic to it.
- Data Tier
    - Responsible for storage and persistence of user and business-specific data.
#### Benefits
- Easy to adopt and scale horizontally.
#### Drawbacks
-  Monolithic structure of our logic tier.
-  High CPU and memory consumption.
-  Low development velocity.
#### Conclusion
- It is the perfect choice for companies whose codebase is:
    - relatively small and not complex.
    - Maintained by a small team of developers.
    - Egs. early-startup companies and well-established companies.

## Microservices Architecture
- Microservices Architecture organizes our business logic as a collection of loosely coupled and independently deployed services.
- Each service is owned by a small team and has a narrow scope of responsibility.
- Smaller codebase.
    - Development becomes easier and faster.
    - Codebase loads instantaneously in our IDE.
    - Building and testing becomes easier.
    - Troubleshooting or adding new features becomes easier.
- Better performance and horizontal scalability.
    - Instances become less CPU intensive and less memory-consuming.
- Better Organizational Scalability
- Better security (fault isolation)
### Considerations 
- We don't get all these benefits out-of-the-box.
- Overhead and challenges.
- We need to make sure that the services are logically separated such that every change:
    - Can happen only in one service.
    - Would not involve multiple teams.
- Separate database per microservice.
- We should always start with a monolithic architecture.

## Event-Driven Architecture
- Instead of direct messages that issue commands or requests that ask for data we have only events.
#### An event is an immutable statement of a fact or a change.
- In an event-driven architecture we have 3 components, on the serving side we have the event emitter/producer on the receiving end we have the consumers and in between we have the event channel which is the message broker.
-  event emitter ---- message broker ---- consumers
### Benefits
- Decoupling microservices - higher horizontal and organizational scalability
- Analyze and respond to large streams of data in real time.
### Architectural Patterns
- Event sourcing - allowed us to store and audit the current state of a business entity by only appending inmutable events only when we need to.
- CQRS pattern (Command Query Responsibility Segregation) - allows us to optimize a database with a high load of Read and Update operations by completely splitting operations to different services. It can help us to join data from completely different services and databases.

