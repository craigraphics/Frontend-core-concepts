## What are Software Architectural Patterns
- Are general repeatable solutions to commonly occurring system design problems.
- Common solutions to software architectural problems that involve multiple components that run as separate runtime units.

## Incentives for using Software Architectural Patterns
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
- 
