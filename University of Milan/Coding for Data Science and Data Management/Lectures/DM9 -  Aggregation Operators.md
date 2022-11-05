``` sql
-- retrieve the overall length of 2010 movies
SELECT SUM(LENGTH)
FROM imdb.movie
WHERE year = '2010'

SELECT *
FROM imdb.movie
WHERE year = '2019'

-- retrieve the average value of length on movies from 2010
SELECT AVG(LENGTH)
FROM imdb.movie
WHERE year = '2010'

-- retrive the number of stored movies
SELECT COUNT(*)
FROM imdb.movie
-- this includes possible null values


-- retrieve the number of stored movies for which the title is defined
SELECT COUNT(official_title)
FROM imdb.movie
-- no null values included

-- no duplicate values
SELECT COUNT(DISTINCT official_title)
FROM imdb.movie


-- retrieve the number of movies per year
SELECT COUNT(*)
FROM imdb.movie
GROUP BY year

SELECT year, COUNT(*) AS "number of movies"
FROM imdb.movie
GROUP BY year
-- In the select of a group by you can only show attributes that appear in the group by
-- or an aggregate function applied to that group

-- return the number of movies with a rating score higher than 8
SELECT COUNT(*)
FROM imdb.rating
WHERE score > 8

-- return the average score of movies by year
SELECT year, AVG(score) AS "average score", COUNT(*) AS "number of movies"
FROM imdb.rating, imdb.movie
WHERE rating.movie = movie.id
GROUP BY year
ORDER BY year
-- some years are missing because some movies don't have a rating
-- so we make a right join to keep all the records from the rigth table (movie)

SELECT year, AVG(score) AS "average score", COUNT(*) AS "number of movies"
FROM imdb.rating RIGHT JOIN imdb.movie on rating.movie = movie.id
GROUP BY year
ORDER BY year

-- retrieve the years after 2010 in which more than 10 movies have been produced
-- we need to apply HAVING which is a filter condition applied on the group result
SELECT year, COUNT(*)
FROM imdb.movie
WHERE year > '2010'
HAVING COUNT(*) > 10
ORDER BY year

-- for each movie retrieve the number of persons involved in each role
-- subgroups
SELECT movie, p_role, COUNT(person)
FROM imdb.crew
GROUP BY movie, p_role

-- for each person retrieve the number of played movies by role
SELECT person, p_role, COUNT(movie)
FROM imdb.crew
GROUP BY person, p_role

-- in the previous query, return also the given_name of the person
SELECT person, given_name, p_role, COUNT(movie)
FROM imdb.crew INNER JOIN imdb.person ON crew.person = person.id
GROUP BY person, given_name, p_role

-- for each person return the number of played movies by role
SELECT person, given_name, p_role, COUNT(movie)
FROM imdb.crew INNER JOIN imdb.person ON crew.person = person.id
GROUP BY person, given_name, p_role
-- in group by always use first an unique identifier (primary key)


-- retrieve the best rating score for each movie
SELECT movie, MAX(score) AS "best score"
FROM imdb.rating
GROUP BY rating.movie

```
