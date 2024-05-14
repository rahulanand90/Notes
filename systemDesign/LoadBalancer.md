# Load Balancer
The job of the load balancer is to fairly divide all client requests among the pool of available servers.
The load balancing layer is the first point of contact within a data center after the firewall. 

It provides
- scalability
- availability
- performance

### Services offered
- Health checking
- Service Discovery
- Security
- Reduced human intervention
- TLS termination

### Placement of LB
- between end users and web servers/application gateway.
- between web servers and application servers.
- between application servers and database servers.

### Single point of failure ?
Generally they are in pair/cluster.

### Global server load balancing
GSLB ensures that the globally arriving traffic load is intelligently forwarded to a datacenter (across multiple 
geographical regions.)



GSLB takes decision based on
- user's geographic locations
- no of hosting servers in diff locations
- health of data clusters etc

GSLB offers automatic zonal failover. 

GSLB can also sits on top of other LBs for traffic diversion.

### How DNS can perform like GSLB?
dns gives different list of data centre IPs to different user in round-robin fashion. But there can be problems, 
obviously.
- uneven load distribution on end servers.
-  the availability of the service can take a hit due to DNS-level load balancing because it will keep in 
   distributing the crashed server IP until the TTL of the cached entries expires.
- Client behavior is out of control (they can choose any server from the given list to them)
- Clients can’t determine the closest address to establish a connection (because of round-robin fashion)


### What is local load balancing?
Local load balancers reside within a datacenter. 
