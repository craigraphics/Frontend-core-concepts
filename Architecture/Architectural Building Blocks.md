## Load Balancer
The basic role is to balance load among a group of servers in our system.

### Quality Attributes
 1. Scalability
    - By hiding our servers behind a load balancer, we can scale the system up and down by adding additional servers when the load increases and removes servers when it decreases.
    - In a cloud environment, we can use auto-scaling policies to intelligently add/remove servers based on requests/second or network bandwidth.
 2. High Availability
    - Can be configured to stop sending traffic to servers that cannot be reached.
 3. Performance (Throughput)
    - Load balancers may add a little latency but it is an acceptable price to pay for increased performance in terms of throughput.
 4. Maintainability
    - We can take down individual servers for maintenance or upgrades without interrupting the service.

### Types of Load Balancers
  - DNS (Domain Name System)
    - DNS is part of the internet infrastructure that maps human/friendly URLS to IP addresses.
    - They can be used by network routers to route requests to individual computers on the web.
    - It is the "phone book of the internet".
    - It exposes all the IPs and does not run any kind of health checks.
  - Hardware Load Balancers
    - Run on dedicated devices designed and optimized specifically for load balancing.
  - Software Load Balancers
    - Programs that can run on a general-purpose computer and perform a load balancing function.
    #### Software and Hardware Load Balancers can balance the load intelligently taking into account:   
      - Different types of hardware.
      - current load on each server.
      - Number of open connections.
      - They can create an abstraction between services.
    - Load balancers on their own do not solve the DNS resolution problem.
    - We would still need some kind of DNS solution to map a human-readable domain name to an IP address.
  - Global Server Load Balancer
    - It is a hybrid between a DNS service and the hardware/software load balancer.
    - It provides a DNS service.
    - It provides an intelligent solution with the same monitoring capabilities as other load balancers.
    - Most GSLB can be configured to route traffic based on a variety of strategies and not just by physical location.
    - Since they are in constant communication with our data centers, they can be configured to route users based on:
      - The current traffic.
      - CPU load on each data center.
      - Best-estimated response time.
      - Bandwidth between user and data center.
    - Load balancing solutions:
      - HAProxy - open source software 
      - NGINX - open source software
      - AWS (ELB) - cloud based with 4 different modes: application LB HTTP and HTTPS traffic, Network LB for TCP and UDP traffic, Gateway LB for deploying and scaling, Classic LB for routing traffic to EC2 instances.
      - GCP (Google) - cloud based with 4 types: External HTTP(S) run services behind internal IP, Internal HTTP(S) run services behind an internal IP, External TCP/UDP and Internal TCP/UDP.
      - Microsoft Azure - cloud based with 3 types: Standard public and internal LB, Gateway for high performance, basic for small scale apps.
      - Amazon Route 53 - GSLB solution highly available and scalable DNS web service.
      - Google Cloud Platform Load Balancer and Cloud DNS - GSBL solution. Reliable resilient, low-latency DNS serving from Google.
      - Azure Traffic Manager - GSLB DNS-based load balancing.

## Message Broker
- A software architectural building block that uses the queue data structure to store messages between senders and receivers.
- A message broker is used inside our system and not exposed externally.
- They are the fundamental building block of asynchronous software architecture.
### Basic capabilities 
  - Storing/temporarily buffering the messages.
  - Message routing.
  - Transformation validation.
  - Load balancing.
### Benefits
  - Most message broker implementations offer the publish/subscribe pattern when multiple services can:
  - Publish messages to a particular channel.
  - Subscribe to that channel.
  - Get notified when a new event is published.
### Quality Attributes
 - A message broker adds a lot of fault tolerance to our system.
 - It allows different systems to communicate with each other while some of them may be unavailable temporarily.
 - Message brokers prevent messages from being lost.
 - Availability and Scalability
   - The additional fault tolerance helps us provide high availability to our users.
   - A message broker can queue up messages when there is a traffic spike.
   - It allows our system to scale to high traffic.
 - Performance - We pay a little in performance when it comes to latency.

## API Gateway
- An API Gateway is an API management service that sits between the client and a collection of backend services.
- It follows a software architecture pattern called API composition.
- We compose all the APIs of all our services into one single API.
- The client applications can call one single service.
- Monitoring and alerting.
- Protocol Translation.
### Benefits
 - Seamless internal modifications/refactoring.
 - Consolidating all security, authorization, and autentication in a single place.
 - Request routing - we save the overhead of authenticating every request from the user at each service by performing in a single place.
### Security Features
- Depending on the permissions and the role of the user, we can allow different operations such as:
  - Viewing private content
  - Deleting/updating content.
- We can also implement rate-limiting at the API Gateway to block Denial of Service attacks from malicious users.
### Considerations
- API Gateway shouldn't contain business logic.
- API Gateway may become a Single Point of Failure.
- Avoid bypassing API Gateway from external services.
### Solutions
- Netflix Zuul - is a free and open-source application gateway written in Java for dynamic routing, monitoring, resiliency, security and more.
- Amazon API Gateway - a fully managed service that makes it easy for develpers to create, publish, maintain, monitor and secure APIs. Supports RESTful APIs and WebSocket APIs.
- Google Cloud Platform API Gateway - enables you to provide secure access to your services through a well-defined REST API
- Microsoft Azure API Management - helps organizations publish APIs to external, partner, and internal developers to unlock the potential of their data and services.

## CDN Content Delivery Network
### Problem
- 53% of mobile users abandoned a website if it took longer than 3 seconds to load.
### What is a CDN
- It is a globally distributed network of servers.
- Located in strategic places.
- Main purpose: speeding up the delivery of content to end-users.
### Advantages of Edge Servers
- CDNs provide service by caching our website content on their edge servers which are relocated at different Points of Presence (PoP).
- Those edge servers physically are closer to the user
- The edge servers are more strategically located in terms of network infrastructure.
- This allows them to transfer content much quicker to the user.
- Improve our perceived system performance.
### Types of Content
-  Images
-  Text
-  CSS
-  JavaScript
-  Video Streams (live and on-demand)
### Quality Attributes
- Performance - faster page loads.
- High availability - issues/slowness are less noticeable.
- Security - Protection against Distributed Denial of Service attacks (DDoS).
### Additional Techniques
- CDN providers use faster and more optimized hard drives to store the cached content.
- Reduce bandwidth by compressing the content delivered using algorithms like GZIP and minification of JS files.
### Pull Strategy
- We need to tell the content delivery network provider:
  - Which content we want on our website to be cached.
  - How often this cache needs to be invalidated.
-  It is configured by setting a Time To Live (TTL) property on each asset/type of asset.
#### Advantages
- Everything is taken care of by the CDN provider. Lower maintenance on our part.
#### Drawbacks
- The first users to use an asset not cached yet, will have a longer latency.
- We still need to maintain a general high availability of our system.
### Push Strategy
- Some content delivery network providers support this model directly
- Others enable this strategy by setting a long TTL for our assets so that the cache never expires.
  - Whenever we want to publish a new version we purge the content from the cache.
  - This forces the CDN to fetch that content from our servers whenever a user requests it.
#### Advantages
- If our content doesn't change frequently, we can simply push it once to the CDN.
- It reduces the traffic in our system and the burden to maintain high availability.
#### Drawbacks
- If content changes frequently, we have to actively publish new versions of the content to the CDN.
- Users will get stale and out-of-date content.
### Solutions
- Cloudflare - ultra-fast static and dynamic content delivery
- Fastly
- Akamai
- Amazon CloudFront
- Google Cloud Platform
- Microsoft Azure CDN
