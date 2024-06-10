# What is an API?
After capturing all functional requirements, we can think of our system as a black box.
- The black box has: 
  - Behavior
  - Well-defined interface.
- That interface is a contract between:
  - Engineers who implement the system
  - Client applications who use the system
- Since the interface is called by other applications, it is referred to as an Application Programming Interface or API.
- In a large-scale system, API is called by other application remotely through the network.

#### Applications that may call the API:
- Frontend clients
- Backend systems
- Internal systems within our organization.

### Categories of APIs
- Public APIs
  - Exposed to the general public.
  - Any developer can use/call from their application.
  - It is a good practice to require the users to register with us before allowing to send requests and use the system. 
- Private / internal APIs
  - Exposed only internally within the company.
  - The allow other teams to take advantage of the system and provide bigger value for the company. 
- Partner APIs
  - Exposed only to companies/users having business relationship with us.
  - The business relationships is in the form of customer agreement after buying product or subscribing to the service.

### Benefits of API
- Client who uses it can immediately and easily enhance their business by using our system.
- They need not know anything about our system's internal design / implementation.
- Once we define and expose our API, clients can integrate with us without waiting for full implementation of our system.
- API makes it easier to design and architect the internal structure of our system.

### Best Practices
- Complete Encapsulation of the internal design and implementation. API should be completely decoupled from our internal design and implementation.
- Needs to be easy to use, easy to understand, impossible to misuse.
  - Only one way to get certain data/perform a tasks
  - Descriptive names for actions and resources.
  - Exposing only the information and actions that the users need.
  - Keeping things consistent all across our API.
- Keeping the operations Idempotent. An operation doesn't have any additional effect on the result if it is performed more than once.
- API pagination.
  - Important when a response from our system to the client request contains a very large payload or dataset.
  - Without pagination most client applications not be able to handle big responses or result in a poor user experience.
  - Pagination allows the client to request only a small segment of the response.
  - Asynchronous operations. A client app receives a response immediately without having to wait for the final result which includes some kind of identifier that allows to track progress.
  - Versioning the API.
    - In practice there may be a need to make non-backward compatible API changes.
    - When explicitly version the APIs, we can maintain two version at the same time and deprecate one gradually.     
 
## RPC API (Remote Procedure Call)

RPC revolves more around actions and less around data/resources. Every action is a new method with a different name.

### Unique Features 
- The remote method invocation looks like calling a normal local method in terms of the developer code.
- This is referred to as location transparency.
- To the developer of the client application a method executed locally or remotely looks the same.
- RPC frameworks support multiple programming languages.
- Application written in different programming languages can talk to each other using RPC.
### Benefits
- Convenience to the developers of the client applications
- They can communicate with our system easily by calling methods on objects similar to calling normal, local methods.
- The details of communication establishment or data transfer between client to server abstracted away from the developers.
- Failures in communication with server result in an error or exception depending on the programming language.
### Drawbacks
  - Slowness - the client never know how long those remote methods invocations can take. Slowness can be addressed by introducing asynchronous version for slow methods.
  - Unreliability - the client is remotely running on a computer and is using the network to communicate with our system.
### When to use RPC
  -  RPC are used in communication between backend systems.
  -  Frameworks that support RPC from frontend clients are less common.
  -  Perfect choice for API provided to a different company instead of an end user web/app page.
### When no to use RPC
- Where we don't want to abstract the network communication away.
- When we want to take direct advantage of HTTP cookies or headers.

## REST API (Representational State Transfer)
A set of architectural constraints and best practices for defining APIs for the web.

 ### Quality Attributes
  - The server is stateless.
    - It does NOT maintain any session information about client.
    - Each message should be served in isolation without any information about previous requests.
  - Cacheability - The server has to either explicitly/implicitly define each response as either cacheable or non-cacheable.
### Named resources
  - Each resource is named and addressed using a URI (Uniform Resource Identifier).
  - The resources are organized in a hierarchy where each resource is a simple resource or collection resource. The hierarchy is represented using "/".
    - A simple resource has a state and can contain one/more sub-resources.
    - A collection resource contains a list of resources of the same type.
### Best practices
- Naming our resources using nouns.
- Making distinction between collection resources and simple resources by using plurals.
- Giving the resources clear and meaningful names.
- The resource identifiers should be unique and URL friendly.

### REST Operations
- The API limits the number of methods we can perform. These operations are:
  - Creating a new resource. -> POST
  - Updating a existing resource. -> PUT
  - Deleting a existing resource. -> DELETE
  - Getting the current state of the resource or list of resources if collection. -> GET
    
### Methods Guarantees
- The GET method is considered safe, applying to a resource will not change its state.
- GET, PUT DELETE methods are idempotent - applying them multiple times would not result in the same state change as applying them once.
- GET requests are considered cacheable by default.
- Responses to POST requests can be made cacheable.

REST API Definition - Step by step process
1. Identifying Entities.
2. Mapping Entities to URIs.
3. Defining Resources' Representations, usually using JSON format.
4. Assigning HTTP Methods to Operations on Resources.
