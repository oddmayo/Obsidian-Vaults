
``` javascript

db.movie.find(
{
	*/filterring criteria over field values - WHERE clause in SQL
},	

{
	*/filtering criteria over field to project - SELECT clause of SQL

}

)

*/retrieve the documents about movie of 2010 and show only title and length
*/In SQL this would be:
SELECT title, length
FROM movie
WHERE year = '2010'

db.movie.find(
{
	"year": "2010"
},
{
	title: 1,
	length: 1
}
	
).count()

*/ 1 means show the feature, 0 don´t
*/ .count() at the end counts the number of records of the filtering criteria, so the second part of the query becomes irrelevant

*/ In SQL this would be
SELECT COUNT(*)
FROM movie
WHERE year = '2010'

*/ retrieve the documents that are about 2010 with length greater than 60 minutes

db.movie.find(
{
	"year": "2010",
	"length": {"$gt": 60}
},
{
	title: 1,
	year: 1,
	length: 1
}
	
)


*/ In SQL

SELECT title, year, length
FROM movie
WHERE year = '2010' AND length > 60;

*/ other operators: $gt, $gte, $lt, $lte

*/ retrieve the title of the movies where Leonardo di Caprio is an actor (use of regular expression)

db.movie.find(
{
	"crew.give_name": {"$regex": /.*caprio.*/i}
},
{
	"_id": 0,
	"title": 1,
	"crew.give_name": 1
}
	
)


db.movie.find(
{
	"crew.give_name": "Leonardo DiCaprio"
},
{
	"_id": 0,
	"title": 1,
	"crew.give_name": 1
}
	
)

*/ add .$ at the end of the desired field to only show the documents that meet the condition


db.movie.find(
{
	"crew.given_name": {$elematch: {
		"$and": [
			{"give_name": {"$regex: /.*caprio.*/i"}},
			{"give_name": {"$ne": "Leonardo DiCaprio"}}
			]
	}
	}
},
{
	"_id": 0,
	"title": 1,
	"crew.give_name": 1
}
	
)

```