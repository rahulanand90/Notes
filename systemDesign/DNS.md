Browser needs IP address to create HTTP connection

### Type of Name Servers:
1. Local or Default Severs
2. Root Level Name Servers 
   - .edu, .com etc.
   - returns list of TLD servers. that holds IP of particular domain.
3. Top Level Domain (TLD) Name Servers
   - Holds IP address of Authoritative name servers of that particular organization (like google.com)
4. Authoritative Name server
   - returns back IPs of web or application servers

DNS resolution can be recursive as well as iterative. Iterative is preferred to reduce query load.

### Caching stages
1. Browser
2. OS
3. local DNS resolver
4. ISP
5. DNS Infra

##### DNS as a distributed system

##### Highly scalable
roughly 1000 copies of 13 TLD are placed strategically over globe.

##### Reliable
it is reliable because of 
- caching
- replication
- protocol 

##### Consistent
- compromises on strong consistency to achieve high performance because data is read frequently from DNS databases 
  as compared to writing. 
- 

DNS Resolution can be done ny
- router / isp
- or by using any private dns resolvers like cloudfare, google etc.

How Resolution Works?
- there are 13 fixed root name server IPs. RS from single operator are distributed across the world and they 
  leverage anycast (they advertise the same IP address using anycast)
- request gets landed to any of the replicas of any root name servers. They redirect to nearest physical server 
  which returns the TLD server IP.
- same process is followed for TLD server, which returns authoritative server IP
- 