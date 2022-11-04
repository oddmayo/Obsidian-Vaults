```sql
-- retrieve the title of movies produced in USA
SELECT official_title 
FROM imdb.movie, imdb.produced
WHERE produced.movie = movie.id AND country = 'USA'

-- alternative syntax:
SELECT official_title
FROM imdb.movie INNER JOIN imdb.produced ON produced.movie = movie.id
WHERE country = 'USA'

-- the above is the cartesian product of movie and produced
-- 1031 records in movie
-- 1332 records in produced
-- the result of cartesian product is 1031 * 1332
-- retrieve the countries in which movies of 2010 have been released (return the movie title, both the official and the released one (where available))

-- retrieve the official title of movies released in Italy
SELECT official_title AS "original title", title AS "title in Italy"
FROM imdb.movie, imdb.released
WHERE movie.id = released.movie AND country = 'ITA'

SELECT official_title AS "original title", title AS "title in Italy"
FROM imdb.movie INNER JOIN imdb.released ON movie.id = released.movie
WHERE country = 'ITA'

-- retrieve the name of actors in the movie Inception (I need the tables person, crew, movie)
SELECT given_name
FROM imdb.person INNER JOIN imdb.crew ON person.id = crew.person INNER JOIN imdb.movie ON movie.id = crew.movie
WHERE official_title ILIKE 'inception' AND p_role ILIKE 'actor'


-- crete a view that contains the name of the crew of all movies
-- these becomes a kind of virtual table
CREATE VIEW imdb.crew_names AS (
SELECT given_name AS "person name", official_title AS "movie title", p_role AS "role in the movie", character
FROM imdb.person INNER JOIN imdb.crew ON person.id = crew.person INNER JOIN imdb.movie ON movie.id = crew.movie
ORDER BY given_name, official_title);

SELECT "person name"
FROM imdb.crew_names
WHERE "movie title" ILIKE 'inception'

-- what happends when I add records to crew
-- is the view crew_names aligned?
-- Yes, it recieves all the changes of the original tables

-- retrieve the persons for which birth and death countries are different
SELECT *
FROM imdb.location
WHERE d_role = 'D'

SELECT *
FROM imdb.location
WHERE d_role = 'B'
-- we want to combine these two queries

SELECT *
FROM imdb.location AS birth_places, imdb.location AS death_places
WHERE birth_places.d_role = 'B' AND death_places.d_role = 'D' AND birth_places.person = death_places.person AND birth_places.country <> death_places.country
-- this is a self join, because we need to verify different conditions on the same attrbiute

-- retrieve the persons for which birth place is not defined

-- this is the opposite
SELECT given_name AS "person", country AS "country of birth"
FROM imdb.person INNER JOIN imdb.location on person.id = location.person
WHERE d_role = 'B'

-- it can be achieved using the left join
-- in addition to persons with connection to location, show the ones that don't
SELECT given_name AS "person", country AS "country of birth"
FROM imdb.person INNER JOIN imdb.location on person.id = location.person
WHERE d_role = 'B'

-- this last query is not working


```