# Class material
## Introduction
#database: collection of data managed by a DBMS
A **DBMS** - Data Basse Management System is a software system able to support the definition, construction, manipulation and sharing of persistent and large databases. Its *goal* is to support efficient <u>data retrieval</u> and to enforce <u>data protection</u>

### DBMS functionalities
- **DB definition**: specification of type, structure, and integrity constraints
- **DB construction**: population of the database and storage of data in a persistent way
- **DB manipulation**: queries, modifications and report generation
- **DB sharing**: multiple applications and users at the same time access the stored data

It provides some level of *data abstraction*

![[Pasted image 20220913154617.png]]

Data are organized as sets of homogenous records that can be represented as **tables**

### Example database
![[Pasted image 20220913155155.png]]

**schema**: describes the structure of the database (headings)
**instance**: varying very rapidly, that is the actual data stored in the database (content)

Data Definition Language: defines database schema
Data Manipulation language: querying and editing the database instances

---

## Relational databases

*Attributes* are used as column headings, a relational database is composed by a collection of relations with attributes represented as tables

The relational model imposes a rigid structure to the data:
- information is represented by means of tuples
- Tuples have to conform to relation schemas

