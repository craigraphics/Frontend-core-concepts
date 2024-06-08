## What is an API?
After capturing all functional requirements, we can think of our system as a black box.
The black box has:  
  - Behavior
  - Well-defined interface
That interface is a contract between:
  - Engineers who implement the system
  - Client applications who use the system
Since the interface is called by other applications, it is referred to as an Application Programming Interface or API.
In a large-scale system, API is called by other application remotely through the network.

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
