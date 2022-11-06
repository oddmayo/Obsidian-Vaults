
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


```