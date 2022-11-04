``` sql

-- These queries are not saved in the database

-- Select all columns from movie table
SELECT *
FROM imdb.movie

-- Select certain columns, with condition on attribute and ordered
SELECT official_title, year, length
FROM imdb.movie
WHERE year = '2010'
ORDER BY year ASC, official_title DESC

-- retrieve the data of movies about 2010 and with length greater than 120 minutes
SELECT *
FROM imdb.movie
WHERE (year = '2010') AND (length > 120)

-- retrieve the data of movies about 2010 and 2011 and order by year
SELECT *
FROM imdb.movie
WHERE (year = '2010') OR (year = '2011')
ORDER BY year
-- We use OR here beacuse the same attribute cannot comply with the both conditions at the same time

-- retrieve the title and year of movies in the range 2000 and 2010
SELECT official_title, year
FROM imdb.movie
WHERE year >= '2000' AND year <= '2010'

-- alternative syntax for previous excercise
SELECT official_title AS "title", year AS "released year"
FROM imdb.movie
WHERE year BETWEEN '2000' AND '2010'

-- retrieve the data of movies for which length is not defined (IS NULL)
SELECT *
FROM imdb.movie
WHERE length IS NULL

-- retrieve the data of movies for which length is defined (IS NOT NULL)
SELECT *
FROM imdb.movie
WHERE length IS NOT NULL

-- the previous two queries are complementary

-- retrieve the movies that are about muerder (title contains the word murder)
SELECT *
FROM imdb.movie
WHERE official_title ILIKE '%murder%'
-- ILIKE insensitive case
-- wildcards:
-- %: string of any length
-- _: just one character

SELECT *
FROM imdb.movie
WHERE official_title ILIKE '%murder_'
-- In this case, it admits anything before the word murder but only one additional character after

-- An alternative way of using LIKE capturing case sensitive titles
SELECT *
FROM imdb.movie
WHERE official_title LIKE '%_urder%'

-- retrieve the persons where john is the first name
SELECT given_name
FROM imdb.person
WHERE given_name ILIKE 'john%'

-- retrieve the persons where john is the last name
SELECT given_name
FROM imdb.person
WHERE given_name ILIKE '%john'

-- retrieve the crew of the movie inception - with this now we need another table
-- join operation
SELECT *
FROM imdb.person, imdb.crew, imdb.movie
-- this is the cartesian product, a cross joing between the three tables

-- cardinality of cartesian product: 38340 * 51541 * 1031
-- 38340 persons
-- 51541 crew records
-- 1031 movie records

-- back to the excercise
SELECT *
FROM imdb.person INNER JOIN imdb.crew ON person.id = crew.person INNER JOIN imdb.movie ON crew.movie = movie.id
-- to be continued next lesson

```
