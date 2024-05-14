# Microservices

## Key Points

1. Microservices are _independently deployable_ modules. 
2. Every microservice has to be an independent process.
3. A system that is not made up of microservices can only be deployed in its entirety. -- Deployment monolith
4. the term microservice suggests that especially small services are meant. However, in practice, microservices can 
   vary hugely in size.


### Advantages

1. Microservices for scaling development:
   1. With the help of microservices, the projects can be divided into smaller units that can work independently of 
      each other.
   2. individual team can make most technology decisions on their own. (it is irrelevant which programming language 
      a microservice is written in) 
   3. it can not only be developed independently, but it can also be brought into production on its own.
   
2. Sustainable development
   1. Replaceability of microservices.
   2. Dependency management between the microservices. Classical architectures often have difficulties at this level.
      Microservices have clear boundaries due to their interface irrespective of whether the interface is 
      implemented as a REST interface or via messaging. 
   3. microservices can ensure a high architecture quality.
3. Continuous delivery
   1. The continuous delivery pipeline is significantly faster because the deployment units are smaller.
   2. Building up a continuous delivery pipeline is easier for microservices. **Whereas** Setting up an environment for a 
      deployment monolith is complicated.
   3. A microservice requires less powerful hardware. _However, running all microservices together in one 
      integration test can cancel out this advantage._
   4. deployment of a microservice poses a smaller risk
   5. **PLEASE NOTE:** Deployment must be automated. Microservices substantially _increase the number of deployable 
      units_ compared to a deployment monolith. 
4. Robustness
   1. When a memory leak exists in a microservice, only this microservice is affected and crashes. The other 
      microservices keep running

5. Independent scaling
   1. Each microservice can be independently scaled. scaling the whole system is not required 
   2. they must be stateless. Otherwise, requests of a specific client cannot be transferred to another instance **???**

6. Free technology choice

7. Security
   1. it is possible to introduce firewalls into the communication between microservices. 
   2. Besides, the communication between microservices can be encrypted to guarantee that the communication really 
      originates from another microservice and is authentic.

8. In general: isolation


### Microservices involve trade-offs
If robustness does not matter, other alternatives can be considered. For example, multiple microservices can run 
together as Java web applications in one Java application server. In this case, they all run in one process and 
therefore are not isolated in respect to robustness. Still they are independently deployable. 
1. A memory leak in any of the microservices will cause them all to fail. 
2. However, such a solution is easier to operate and therefore might be the better trade-off in the end.

### Two levels of microservices: Domain and technical
1. coarse-grained division by domain: enables the teams to develop largely independently and allows them to roll out 
   a new feature with the deployment of a single microservice. For example, in an e-commerce system, customer 
   registration and the order process can be examples of such coarse-grained microservices. 
2. For technical reasons some microservices can be further divided. These microservices can then be scaled 
   independently of the other microservices. When, for example, the last step of the order process is under 
   especially high load, this last step can be implemented in a separate microservice.  
3. It is difficult to state a typical number of microservices per system. 10-20 coarse-grained domains are usually 
   defined, and each of these might be subdivided into one to three microservices. However, there are also systems 
   with far more microservices.  


### Disadvantages

1. **Increased operations effort** - requires more effort than running a deployment monolith. (more deployable units 
   exist that all have to be deployed and monitored). his is feasible only when the operation is largely automated 
   and the correct functioning of the microservices is guaranteed via appropriate monitoring. 
2. **Must Be Independently Deployable** - Changes to interfaces must be implemented in such a way that an independent 
   deployment of individual microservices is still possible. For example, the microservice which implements the 
   interface has to offer the `new` and the `old` interface. Then this microservice can be deployed without requiring 
   that the calling microservice be deployed at the same time.  
3. Testing must be independent
4. Difficult to change multiple microservices - Changes that affect multiple microservices are more difficult to 
   implement than the changes that concern several modules of a deployment monolith.
5. Increased latency and failures - Microservices communicate through the network - latency is much higher. - 
   communication will fail. 

### Which one to choose

1. Identify the problems 
2. prioritize the benefits 
3. Access potential challenges.
4. identify suitable recipe for project building

#### Notes:
Microservices communicate over the network, which is unreliable. The app should not depend on this communication.

