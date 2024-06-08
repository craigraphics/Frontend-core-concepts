## List of Quality attributes:
- Performance
- Scalability
- Availability
- Testability
- Deployability
- Maintainability
- Portability
- Security
- Observability
- Consistency
- Efficiency
- Usability

### Performance
#### Response time
The response time is the time between a client sending a request and receiving a response.
- It is broken in 2 parts:
  - Processing time - it's the time that takes a system to process a request and send a response. 
  - Waiting time or latency - is the duration of time between the request / response spends inactively in our system.
#### Throughput 
  - Amount of work performed by our system per unit of time. It's measured in tasks/second.
  - Amount of data processed by our system per unit of time. It's measured inn bits/second.
#### Important considerations:
  - Proper measuring of response time. We should talk in percentages and not median or average.
  - Response time percentile distribution. We need to find the tail latency which is the percentage of worst-case scenarios of response times.
  - Performance degradation (potential overly-utilized resources eg. high CPU utilization, high memory consumption, etc.).

### Scalability
Is the measure of a system's ability to handle a growing amount of work, in an easy and cost effective way, by adding resources to the system.
Traffic or load may increase:
- Over time
- On the seasonal pattern
- Sporadically
We can scale our system in 3 dimensions:
- Vertical scalability - scaling up
  -  Adding more resources or upgrading the existing resources on a single computer, to allow our system to handle higher traffic or load (memory, storage, CPU, etc.).
  -  Pros:
    - Any application can benefit from it.
    - No code changes are required.
    - The migration between different machines is ery easy.
  - Cons:
    - The scope of upgrade is limited.
    - We are locked to a centralized system which cannot provide high availability and fault tolerance.
- Horizontal scalability - scaling out
  - Adding more resources in a form of new instances running on different machines, to allow our system to handle higher traffic or load.
  - Pros:
    - No limit on scalability.
    - It's easy to add / remove machines.
    - If designed correctly we get high availability and fault tolerance.
  - Cons:
    - Initial code changes may be required.
    - Increased complexity, coordination overhead.
- Organizational scalability
  - Increasing productivity while hiring more engineers into the team.
 
### Availability
It is the fraction of time / probability that our service is operationally functional and accessible to the user.

#### Importance
Two risks that our business faces if our system goes down:
-  Loss of revenue
-  Loss of customers to our competitors.

#### Formulas
  - Uptime = time that our system is operationally functional and accessible to the user.
  - Downtime = time that our system is unavailable to the user.
  - Availability (in %) = uptime / (entire time our system is running). Availability = Uptime / (Uptime + Downtime)
  - MTBF (Mean time between failures) - represents the average time our system is operational.
  - MTTR (Mean time to recovery) - time average it takes us to detect and recover from a failure.
  - Availability = MTBF / (MTBF + MTTR)
  - Industry standard set by cloud vendors is typically 99.9% or higher

### Fault Tolerance & High Availability
Fault Tolerance enables our system to remain operational and available to the users despite failures within one or multiple of its components.

#### Types of failures:
- Human Errors - pushing a faulty config to prod, running wrong command, deploying incompletely tested new version.
- Software Errors - long garbage collection, out-of-memory exceptions, null pointer exceptions, segmentation faults.
- Hardware Failures - servers/routers/storages breaking down, power outages, network failures.

Fault Tolerance is defined as the ability for our system to remain operational and available to the user despite failures to one or some of its components.

Fault Tolerance revolves around 3 major tactics:
- Failure prevention
- Failure detection and isolation
- Recovery - rollback strategy

To prevent our system from going down, eliminate any Single Point of Failure in our system. The best way to eliminate a single point of failure is through Replication and Redundancy.

### SLA, SLO, SLI
SLAs are crafted by the business and legal team.
SLOs and SLIs are defined and set by the software engineers and architects.

#### SLA - Service Level Agreement
It is a legal contract that represents our quality service such as availability, performance, data durability, time to respond to system failures.
It states the penalties and financial consequences, if we breach the contract.

#### SLO - Service Level Objectives
Are the individual goals set for our system. Each SLO represents a target value/range that our service needs to meet.

#### SLI - Service Level Indicators
It is a quantitative measure of our compliance with a service-level objective. It is the actual numbers measured using a monitoring service and calculated from our logs. It can be later compared to our SLOS.

#### Important Considerations
- We shouldn't take every SLI that we can measure in our system and define an objective associated with it. Think about the metrics that users care about the most.
- Promising fewer SLOs is better. Hard to prioritize when too many.
- Set realistic goals with a budget for error.
- Create a recovery plan for when the SLIs show that we are not meeting our SLOs. The plan should include automatic alerts to engineers, automatic failovers/restarts/rollbacks, should have predefined handbooks on what to do in certain situations.

