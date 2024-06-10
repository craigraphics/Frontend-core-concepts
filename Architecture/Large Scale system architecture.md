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
