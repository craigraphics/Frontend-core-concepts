## Gathering, classifying and analyzing requirements for large scale systems

System requirements means to figure out and narrow down what exactly needs to be built for the client.

## Challenges
1. Scope and level of abstraction - we need to understand the problem to also understand the complexity.
2. Level of ambiguity - it's important to clarify all the requirements for that system. Asking the questions to clarify.

## Types of Requirements or architectural drivers
### 1. Features of the System - functional requirements.
   - They describe the system's behavior. 
   - Easily tied to the objective of the system.
   - Functional requirements do not determine its architecture.
### 2. Quality attributes - non-functional requirements
   - Are properties that the system must have as opposed to what the system must do.
   - Scability, Availability, Reliablity, Security, Performance.
   - Quality attributes do dictate the software architecture of our system.
### 3. System constraints - limitations and boundaries
  - Time constraints.
  - Financial constraints.
  - Staffing constraints.

## Steps for capturing the features and functional requirements
   - Identifying all the users and the actors.
   - Gathering all the use cases.
   - Expanding each use case with a flow of interactions between the actors in our system.

## Quality Attributes - Motivation
   - Systems are frequently redesigned NOT because of functional requirements
   - But because the system as it stands:
      -    Isn't fast enough
      -    Doesn't scale
      -    Slow to develop
      -    Hard to maintain
      -    Not secure enough
   - They describe
      - The qualities of the functional requirements.
      - The overall properties of the system.
      - Provide a quality measure on how well our system performs on a particular dimension.
   - Quality attributes need to be:
      - Measurable
      - Testable
   - Important considerations - trade offs
      - Testability and measureability - No single software architecture can provide all the quality attributes.
      - Trade offs - Certain quality attribures contradict one another.
      - Feasibility - Some combinations of quality attributes are very hard / impossible to achieve.
    
## System Constraints - architectural drivers
   - Are the decisions that were already either fully or partially made for us, restricting our degrees of freedom.
   - There are 3 types of constraints:
      - Technical Constraints - they affect the decisions we make in the design phase.
      - Business Constraints - this forces us to make sacrifices in architecture and implementation.
      - Legal Constraints - they may be global or specific to a region.
   - Considerations:
      - Not to take them lightly.
      - Use loosely coupled architecture.     
