continuation of previous exercise

``` sql
-- retrieve the persons for which birth place is not defined
-- it can be achieved using the left join
-- in addition to persons with connection to location, show the ones that don't

-- to solve it we create the following view
-- the view is about the birth event and returns the person code and the country of the persons
CREATE VIEW imdb.birth_paces AS(
SELECT person, country
FROM imdb.location
WHERE d_role = 'B'
)

SELECT given_name AS "person"
FROM imdb.person 
WHERE id NOT IN (SELECT person FROM imdb.birth_paces)
-- solution based on nested query


-- alternative solution based on join
SELECT *
FROM imdb.person LEFT JOIN imdb.birth_paces ON person.id = birth_paces.person
WHERE birth_paces.person IS NULL


-- retrieve the countries without produced movies
SELECT *
FROM imdb.country LEFT JOIN imdb.produced ON iso3 = country
WHERE country IS NULL

-- alternative solution with nested query
SELECT *
FROM imdb.country
WHERE iso3 NOT IN (SELECT DISTINCT country FROM imdb.produced)

-- alternative solution
-- EXCEPT operator
-- set A: full list of countries
-- set B. list of countries where at least one movie is produced
SELECT iso3
FROM imdb.country
EXCEPT
SELECT country
FROM imdb.produced

-- retrieve the movies that are produced in USA and FRA
-- INTERSECT operator
-- give two sets A,B: the intersection is the set of records belonging to both A and B
SELECT movie
FROM imdb.produced
WHERE country = 'FRA'
INTERSECT
SELECT movie
FROM imdb.produced
WHERE country = 'USA'


-- alternative solution

SELECT movie
FROM imdb.produced
WHERE country = 'FRA' AND movie IN
(SELECT movie
FROM imdb.produced
WHERE country = 'USA')

-- retrieve the movies that are released in FRA or USA (distinct drops duplicates)
SELECT DISTINCT movie
FROM imdb.produced
WHERE country = 'FRA' OR country = 'USA'


-- alternative with union
SELECT movie
FROM imdb.produced
WHERE country = 'FRA'
UNION
SELECT movie
FROM imdb.produced
WHERE country = 'USA'


-- retrieve the movies produced in FRA and USA and NOT in other countries
SELECT movie
FROM imdb.produced
WHERE country = 'FRA'
INTERSECT
SELECT movie
FROM imdb.produced
WHERE country = 'USA'
EXCEPT
SELECT movie
FROM imdb.produced
WHERE country NOT IN ('USA','FRA')


-- retrieve the movie with the highets/lowest length
-- AGGREGATE operators: min, max, avg, sum (value of attributes), count (number of records)
SELECT MAX(LENGTH)
FROM imdb.movie

SELECT MIN(LENGTH)
FROM imdb.movie

-- get the record corresponding to the lowest length
SELECT 
FROM imbd.movie
WHERE LENGTH = (SELECT MIN(LENGTH) FROM imbd.movie)


-- retrieve the overall length of 2010 movies
SELECT SUM(LENGTH)
FROM imdb.movie
WHERE year = '2010'

```
