**Schema**: name of the table and the features characterizing the table
$\rightarrow$ defined at the beginning, stable

**Instances**: records inside the table
$\rightarrow$ dynamic

importance of **many-to-many** vs **one-to-many**
importance of **foreign key**

When I insert a foreign key I use an identifier for the table that I am referencing


**Null value**: value that does not exist
$\rightarrow$ But also the value could exist but we don't know it. Also could be ambiguous


---

movie(id, official_tile,...)
rating(check_date, source, movie,...)

foreign key: rating.movie is a foreign key that refers to modie.id

example queary: retrieve the records of person that are still alive
result: I retrieve those that have NULL on the death_date


## Identification of records

What is the identifier of movies? Attribute or set of attributes so I don´t have duplicates

movies(id,official_title,year,length,plot,budget)

-id

What if I don't have the id:
-official_title, year
-official_title, year, length
-official_title, year, length, plot, budget (worst case)

**Superkey**: attribute or combination of attributes that ensure the unique identification of records inside the table. Two records with the same value on the combination of attributes cannot be a superkey

SK - id
SK - official_title, year
SK - official_title, year, length
SK - official_title, year, length, plot, budget

Any attribute + superkey it's still a superkey

**Minimality constraint**: associated to a combination of attributes that is a superkey that cannot be reduced

When I take a superkey, consider if I can remove some attributes and still have a superkey

SK - id
SK - id, official title *no minimality constraint*
SK - official_title, year *minimality constraint*
SK - official_title, year, length *no minimality constraint*
SK - official_title, year, length, plot, budget

A **key** is something that cannot be reduced
Any **key** is a superkey, but not any superkey is key

---

The id alone is compact but not meaningful. In contrast, tittle and year give me a lot more information although less compact

The id ensures that there are not duplicated data in terms of id only. One can specify additional constraints to truly don't have duplicates

---

With null values keys do not work well

**Primary key**: unique identification + minimality + not null (entity integrity constraint)

In a table we have one and exactly one **PK**
The designer has to choose the PK

Both good candidates
SK, K, PK - id
SK, k, PK - official_title, year

In the crew table
crew(person, movie, p_role, character)

We cannot choose a combination of all attributes because character has null values. Then we have a modeling problem, where the PK is the combination of person, movie and p_role but we cannot represent the case of a person interpreting different characters in the same movie

If we want to represent the previous situation we need to change the modeling:

use another table called cast
cast(person, movie, character) where character is composed of only actors
crew(person, movie, p_role) PK the combination of these three

---
## Referential integrity constraint

Relational databases prevent you from inserting a value that references an attribute of another table that is missing. The insertion generates an error (pending references between foreign key and primary key in the referenced table)

If I change the value of an existent reference record that does not exist in the reference table, also generates an error

Any pending reference is stopped by the DBMS

In the crew table: FOREIGN (movie) REFERENCES movie(id)

The behavior is called **NO ACTION**:
- the update of a movie.id value is possible only is the value is not used in crew.movie
- the delete of a movie record is possible only if the movie.id values is not used in crew.movie

Other possible option: **CASCADE**
- the update of a movie.id is applied also to the referencing values in crew.movie
- the delete of a movie record is applied also to the referencing records in crew

