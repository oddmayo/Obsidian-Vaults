Released in 2007 is a cross-platform, document-oriented database engine

It is made up of databases which contain **collections**
- A collection shares enough in common with the notion of table in a relational database
- A collection is made up of **documents**: a document shares enough in common with the notion of *tuple/record* in a relational database

Each document is made up of **fields**: like the attributes in a relational database
Collections can be **indexed**, which improves lookup and sorting performance

MongoDB employs **BSON** (Binary JSON) to store documents and enforce remote procedure calls

The MongoDB syntax is **case sensitive**

Each document has a predefined **\_id** field which represents the primary key of the document within the collection. This value is unique and if not inserted, it is automatically generated to provide a unique ObjectId

Simple find queries and aggregations

**Filter**: retrieve data over filtering of certain field
**Project**: which fields do you want to retrieve when you have a certain document in the result
**Sort**:  sort the result
Collation: ignore for this course


``` javascript

use dse_movie_db
db.getCollectionNames();
< [ 'movie' ]

db.movie.findOne();
-- first document from the movie collection


```

