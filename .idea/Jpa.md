Hibernate is a framework for performing crud opertions in db using java objects.
It provide object to relation mapping. 

JPA is jakarta persistence API (earlier Java Persistence API)  provides stadard API for ORM

Hibernate is a vendor and is a implementation of JPA. Therefore using JPA API makes us dependent of vendor like 
Hibernate etc. 
Also, it takes away the pain of writing queries for performing CRUD operations. 

Hibernate or JPA is another level of abstraction over JDBC. It uses JDBC internally for all the operations.

Entity class must have a public/protected no-args contructor. It can have other constructor too but former is must. 

@Table and @Column are not mandatory but always recommended.

ID Generation Strategies - AUTO, IDENTITY, SEQUENCE, TABLE & UUID.

Custom Id Generation
``` java
class Gen implements IdentifierGenerator {
    @Override
    public Object generate(SharedSessionContractImplementor sharedSessionContractImplementor, Object o) {
        return null;
    }
}
```

##### EntityManager vs JpaRepository
EntityManager - for low level control and flexibility (native SQL queries and stored procedure calls).

JpaRepository - for high level of abstraction