Structure of the movie table inside our imdb database

Specify relationships between two tables: movie and gender table

**Many to many relation**: given a specific record of movie, there could be many records in gender associated with it. And the same for a record in gender applies.

**tables**
movie(*id*, official_title, year, length) - *identifier id*

genre(*name*) - *identifier name*

movie-genre(*movie-id, genre-id*) - *identifier the combination of the two* (so it's 
impossible to insert the same value two times)

crew(*movie-id*, *person-id*, role, character)
$\rightarrow$ usually, the identifier is the combination of the two referenced tables. But in this case a persona can play multiple roles and characters in the same movie, so we add the role and character in the identifier
crew(*movie-id*, *person-id*, *role*, *character*) - worst case scenario where all attributes conform the identifier

This is problematic because the more attributes the more complicated references get when calling instances of a table

person(id, firstname, lastname, bith_date, death_date, bio)

rating(*source, movie, r-date*, scale, score)

the table *movie-genre* is the solution to represent the **many-to-many** relationship between pairs of record of table *movie* and table *genre*

the table *crew* is the solution to represent the **many-to-many** 
relationship between pairs of record of table *movie* and table *person*
$\rightarrow$ One record shows one specific relation between just one person and one movie. All instances give the complete picture

There is a relationship at the schema level, and relations at the instance level

when you create the crew table, you also specify that the 
attribute <u>crew.movie-id</u> is **related** to the attribute <u>movie.id</u>

when you create the crew table, you also specify that the 
attribute <u>crew.person-id</u> is **related** to the attribute <u>person.id</u>

---

One can only insert attributes related to existing movies and existing persons. This is a **constraint** defined at the level of the *schema* (attributed crew.person-id related to the attribute person.id), but also valid at the level of *instances*, because values from crew can only appear values that are present in the values of person and in the values of movie

---

the table *rating* is the solution to represent the **one-to-many** 
relationship between the records of *rating* (only one movie for a given rating) and the records of *movie* (possible many ratings for a given movie)

One cannot insert rating in movie table as one movie can have multiple ratings
movie(id, official_title, year, length, ~~rating~~)

But I can insert a movie in the rating table as the rating corresponds to only one movie
rating(source, movie, r-date, scale, score)

We don't need an intermediate table

the <u>rating.movie</u> attribute is a **foreign key** that refers to *movie.id*
$\rightarrow$ when a attribute refers to an attribute of another key it is in fact a foreign key


**genre**
id | name
--
001	  |  drama
002   |  comedy
003   |  thriller
004   |  biography

**movie-genre**
movie-id | genre-id
--
001         |   002
001         |   004
002         |   001
002         |   003

**movie**
id | title | year | length   
--
001  | WWS      | 2013   |    180
002  | inc.		| 2010   |    192

It's important to have an unique identifier in each table: **the key**

---

The **degree** is the number of attributes in the schema of a table

**Cardinality** refers to the number of records/tuple (at least one value in the row) inside the table




