# Scalability

Scalability is the ability of a computer system to adapt to and accomodate an increased workload. Horizontal Scaling works by distributing the workload across multiple servers or systems. 
Vertical Scaling involves adding resources such as hardware upgrades to an existing server or system.

Simply, its defined as the overall capacity of any system, process or network to handle the growing amount of work. This is one of the most important conditions for any successful web applications.


Some common issues without Scalability

* Reduction in the performance of the web applications due to an increase in the number of requests.
* Increase in high response time/ load time due to expansion of some product ranges.
* Dangerous or over complicated procedure of changing code structure.

We should be following some set of principles to build a application of high standard.

## Principles

* Availability

> The system should be available for use as much as possible (always). It doesn't matter how good the application is if no one can access it.

* Performance

> The system must maintain high level of performance even under heavy loads. Latency is very critical because we as users will be fedup if any of our favourite services have high latency.

* Reliability

> The system must accurately store, retrive and edit data under stress. It should always return most current data. Its a very important principle to build good customer satisfaction.


Now that we know what's scaling and why we need scaling, lets look into how scaling can be achieved with the architecture of our application.

## Designing a scalable architecture

#### Scale

Always favor horizontal scaling over vertical scaling. Vertical scaling adds bottlenect to our application and also as it consumes expensive resources, its costly too.

#### Storage

Having physical servers are expensive to build, maintain and secure with risks of outdated hardware. Cloud storage puts data in logical pools spread across servers. We just have to purchase
the access to it. This approach takes away the burden of security, maintainance off and allows them to scale as we need. We can scale based on the incoming requests.

#### Bottlenecks

They are formed when multiple processes require same resources to proceed. We should be planning architecture to maximize the availability of resources to be in high demand.

> Caching? If data is not stored frequently, caching can be used for frequent access of same data at any level of the application.

> Non-Blocking IO calls serve more requests with limited resources by letting processes continue before a slower one has finished. (Needs a separate topic for discussion?)

> Load balancing software spreads the workload across the network to reduce the pressure on any single node.

> Redundancy safeguards against lost data as well as providng access to high-demand resources.

#### Microservices

This breaks the larger software into smaller pieces that can operate independently of one another. We can just scale a specific piece rather than the entire application.

## Requirements to consider

* Design Simplicity

Should be as simple as possible to reduce the overall maintenance cost and enhance the overall user experience.

* Decomposition

Applications shouldn't be monolithic but instead, these systems can be divided into autonomous sub-systems. These autonomous subsystems can be managed without any major risks of application failure.

* Asynchronicity

Shoould be able to execute various processes in parallel without blocking each other (Similar to NonBLocking IO?)

* Loose coupling

Should try to have low level of interdependence.

* Parallelization

Can help to perform independent development tasks in a series simultaneously.

* Decentralization

Scalable system should run on different servers and these should be distributed as a while to the users.
