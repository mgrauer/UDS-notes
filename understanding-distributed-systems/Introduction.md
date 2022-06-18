## Why do we need distributed systems?

* some systems are inherently distributed: mobile, browsers
* physical proximity for caching
* redundancy for availability and reliability
* large workloads that individual systems couldn't handle

## What are the central challenges of distributed systems?

1. Communication that is reliable and secure
2. Coordination in the presence of network failures
3. Scalability - the ability to handle increasing load on some resource
  * performance is often measured in throughput and response time
  * capacity is the maximum load a system can take when some resource is exhuasted, which is a function of the architecture
  * scalable systems mean that increases in load do not degrade performance
4. Resiliency - the system can continue to do its job in the face of failures
5. Maintainability - the system can be modified, extended, and operated while continuing to work with the same performance
  * systems spend a lot more of their time being maintained than the original writing (same ratio as code modification and code writing, and same ratio as code reading to code writing!)
  * hexagonal architecture or the ports and adapters architecture help
    * port - connection to another system
    * adapter - ability to connect different providers over the same port
  * dependency inversion principle
    * provides loose coupling, meaning one thing does not have to change when another one does
    * have low level details depend on abstractions and not the other way around
    * component should not import from a low level module, but rather both should depend on interfaces
    * this allows for greater testability too, as dependencies can be passed into constructors
