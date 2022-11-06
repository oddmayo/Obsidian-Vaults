
The real difference is the data model between relational and no relational

## Relational database

The DMBS is a concurrent, multi-user system: **multiple users at the same time**

**Transaction**: operation that form a logical unique unit of database processing
$\rightarrow$ the integrity of the data is preserved

Two possible outcomes
- *commit*: all operations successfully executed, database updated
- *rollback*: an error occurs and the database goes to the status before the execution of the transaction

Any relational database is based on ACID properties
1. **Atomicity**: a transaction is performed in its entirely
2. **Consistency**: move to a consistent status to another consistent status (**strict**)
3. **Isolation**: the execution of the transaction should not be interfered by other transaction
4. **Durability**: changes applied to the database by a committed transaction must persist


## No relational database

NoSQL systems are all different, so DynamoDB, Cassandra and MongoDB require individual learning

NoSQL are non relational, distributed open source and horizontally scalable

**Horizontal scalability**: when you need to increase the storage capabilities you can add a new node

**Availability, Replication**: data are usually replicated/mirrored to share the workload between machines

**Eventual consistency**: all the versions of the same record in the end will be consistent

**Horizontal fragmentation**: create partitions of the dataset and assign them to different nodes (data sharding)

### Replication models

**Master-slave**: the reads can be executed only on the master copy or can be allowed 
also at the slaves

**Master-master**: all reads and writes can be at any of the copies, then no guarantee that reads at different nodes with replicated data see the same value and different concurrent writes on the same data item at different nodes can generate temporary inconsistent values of the item

---

**Schema is not required**: NoSQL DBs allow self-describing, semi-structured (JSON) data. There could be a partial schema but it is not required

**Less powerful than SQL**: require to locate records in single files based on ley values and not via complex attribute conditions

### Classification of NoSQL database
- Key-value stores
- Document-based systems
- Column-family systems
- Graph-oriented systems

## Document-based systems

A document is a data item with a flexible notion of structure
- Is a self-describing both schema and data
- Have a hierarchical structure organization of inter-related data elements
- Can be specified in various formats: usually JSON

**Collection**: is a schema-free group of similar documents but with different structure. Two documents in a collection can have different data elements
![[Pasted image 20221106122545.png]]



## NoSQL for Big Data

NoSQL are generally considered as the natural data storage solution for supporting big-data applications due to horizontal scalability that allows to expand the storage

**Big Data**: any voluminous amount of structured, semi-structured and unstructured data that has the potential to be mined for information

Volume, Variety. Velocity, Veracity and Value

