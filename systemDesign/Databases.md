# Databases

Storing any information for later retrieval. 

#### Problem with file storage
1. no concurrency
2. access rights
3. scaling
4. searching

A `database` is an organized collection of data that can be managed and accessed easily. Make below operations easier:
1. storage 
2. retrieval/search
3. delete
4. modify

#### Advantages
1. Managing large data 
2. Retrieving accurate data (data consistency)
3. Easy update using DML 
4. Security 
5. Data integrity 
6. Availability - replication 
7. Scalability - manage the growing load (partition)


# Types

### Relational
- adheres to predefined structure/schema before storing data 
- each tuple should be unique 
- **note:** acid properties aims to provide integrity to database.

#### ACID
1. Atomicity
2. Consistency - should be in a consistent state after every transaction (multiple user should get same result each 
   time)
3. Isolation
4. Durability - completed txns will persist in database even in case of failure.

#### Why relational databases?
1. Flexibility - adding data without server restart 
2. Reduced redundancy
3. Concurrency - handled via transactional access to data.
4. Backup & Recovery

#### Drawbacks
Impedance mismatch - datastructures can have a complex structure but db has a much simpler structure. So translation 
needs to be done.

### Non - Relational databases (NoSql)
- for semi-structured or unstructured data
- was made for data models to access and modify data.

1. Simple Design - no impedance mismatch
2. horizontal scaling - these dbs have capability to run on large clusters
3. availability - node replacement - replication
4. costs - mostly open source and free

### Types of NoSql
1. Key-value database - efficient for session-oriented applications. 
2. Document - store and retrieve documents in formats like XML, JSON, BSON etc. good option for content management 
   applications. Faster reading speed.
3. Columnnar - store data in columns instead of rows. They enable access to all entries in the database column 
   quickly and efficiently. 
4. Graph - allows us to store the data once and then interpret it differently based on relationships. Graph 
   databases can be used in social applications and provide interesting facts and figures among different kinds of 
   users and their activities.  

### Drawbacks
1. Lack of standardisation
2. Consistency - No strong data integrity here but slowly converging using a weak model like eventual consistency.  


Note: When strong consistency is not required, and there are many read-write operations and concurrent users, a 
better choice is to use a NoSQL database. Hence, this is the right option to avoid the relational database. 


# Data Replication
Replication refers to keeping multiple copies of the data at various nodes to achieve: 
1. Availability under faults (failure of some disk, nodes, and network and power outages)
2. Scalability (with increasing reads, writes, and other operations)
3. Performance ((low latency and high throughput for the clients)

### Challenges
1. how to keep multiple copies of data consistent?
2. how to deal with replicated node failure?
3. replicate - sync or async
4. how to handle concurrent writes?
5. which consistency model to choose?

### Synchronous vs Asynchronous

##### Synchronous
the primary node waits for acknowledgement from secondary nodes about updating the data. 
After receiving acknowledgement from all secondary nodes, the primary node reports success to the client
- `Advantage` - all the secondary nodes are completely up-to-date with the primary node.
- `Disadvantage` - causes high latency if one of the node fails to send acknowledgement.

##### Asynchronous
the primary node doesn't wait for acknowledgement and goes on for another work it has. problem here occurs when 
master fails before secondary nodes update themselves.

# Data replication models

### 1. Single leader or primary-secondary replication
- primary is responsible for processing any writes to data stored on the cluster. It also sends all the writes to the 
  secondary nodes and keeps them in sync. 
- for read heavy systems.
- Read resilience.
- Replication via this approach comes with inconsistency if we use synchronous replication. 

##### Primary-secondary replication methods
- Statement-based replication 
- Write-ahead log (WAL) shipping 
- Logical (row-based) replication



### 2. Multi-leader replication
- There are multiple primary nodes that process the writes and send them to all other primary and secondary nodes to 
  replicate 
- gives better performance and scalability than single leader replication
- What happens if same data present on both primary gets updated by 2 different processes simultaneously? 
  called as concurrent writes problem.

##### How to handle conflicts?
- conflict avoidance - works fine but it is not always possible that same data updates can happen via same node.
- last write wins - problem here is global clock synchronization.
- custom logic


Multi-leader replication topologies - circular, star etc etc.


### 3. Peer-to-peer/leaderless replication
- In primary-secondary replication, the primary node is a bottleneck and a single point of failure. Moreover, it 
  helps to achieve read scalability but fails to provide write scalability. 
- The `peer-to-peer replication model` resolves these problems by not having a single primary node.
- this replication can also yield inconsistency like above 2.


##### Quorums
A helpful approach used for solving write-write inconsistencies.
Let’s suppose we have three nodes. If at least two out of three nodes are guaranteed to return successful updates, 
it means only one node has failed. This means that if we read from two nodes, at least one of them will have the 
updated version, and our system can continue working.  


# Data Partition
- Increasing data and concurrent read/write traffic to the data puts scalability pressure on traditional databases. 
  As a result, the latency and throughput are affected.
- At some point, a single node-based database isn’t enough to tackle the load. We might need to distribute the data 
  over many nodes but still export all the nice properties of relational databases.
- Data partitioning (or sharding) enables us to use multiple nodes where each node manages some part of the whole data.
- aim is to strive for balanced partitions and balanced read/write load.

## Sharding
divide load among multiple node. this partitioning must be balanced which makes queries fall equally.

Partitions that are heavily loaded will create a system bottleneck - Such partitions are known as hotspots (a 
significant portion of data retrieval queries will be sent to the nodes that carry the highly congested partitions) 

### Vertical Sharding
- Dividing columns of a table into multiple tables.
- We should be careful if there are joins between multiple tables. We may like to keep such tables together on one 
  shard. 
- Creating shards by moving specific tables of a database around is also a form of vertical sharding.

### Horizontal Sharding
divide a table into multiple tables by splitting the data row wise. Each partition table is called a shard. 
There are 2 strategies: 

##### Key-range based sharding
each partition is assigned a range of contiguous range of keys (partition keys).
problem with this is: search can only be performed via partition key column. Also, if keys are not properly selected,
some nodes may store more data due to uneven partitioning.

##### Hash based sharding
Hash-based sharding uses a hash function on an attribute. Once we’ve found an appropriate hash function for keys, we 
may give each partition a range of hashes 
- `Advantage` here is that keys are uniformly distributed across the nodes.
- `Disadvantage` is we cannot perform range queries.


##### Consistent Hashing
Consistent hashing assigns each server or item in a distributed hash table a place on an abstract circle, called a 
ring, irrespective of the number of servers in the table. 
- `Advantage` easy to scale. increased throughput and improves latency.
- `Disadvantage` may cause non uniform distribution


### Re-balance the partitions #TODO
- Avoid hash mod n
- Fixed number of partitions
- Dynamic partitioning
- Partition proportionally to nodes


### Zookeeper
separate management server for cluster

# TODO
Visit again for pros and cons of distributed vs centralised DB.

# Conclusion
Data distribution (vertical and horizontal sharding) across multiple nodes aims to improve the following features, 
considering that the queries are optimized: 

- Reliability (fault-tolerance)
- Performance
- Balanced storage capacity and dollar costs
- Both centralized and distributed databases have their pros and cons. We should choose them according to the needs 
  of our application. 
