# Topics studied
## With DataCamp

- SELECT *variable* FROM *table*
- SELECT COUNT()
- WHERE, AND, OR
- WHERE, BETWEEN
- WHERE, IN [multiple or conditions]
- IS NULL
- LIKE, % wildcard, _ wildcard
- NOT LIKE
- SELECT SUM()/AVG()/MIN()/MAX()
- SELECT AS *aliasing*
- ORDER BY
- ORDER BY *variable* DESC
- ORDER BY *variable1*, *variable2*
- Different: <>
- SELECT *variable* COUNT(), GROUP BY
- In SQL aggregate functions can´t be used in WHERE clauses
- HAVING COUNT() > 10
- LIMIT
- INNER JOIN
	- SELECT table1.*variable1* as *alias1*, table2.*variable2* as *alias2*
	- FROM table1
	- INNER JOIN table2
	- ON table1.*id1* = table2.*id2*
	- can use USING(*id*) if both tables share the same id name
- CASE WHEN *variable* *logic operator* THEN *string*
	- ELSE *string* END
	- AS *alias*
- INTO

- SET THEORY:
	![[Pasted image 20220914000710.png]]
UNION basically stacks two tables resulting from queries on top of each other
UNION all includes duplicates}
INTERSECT only records in both tables
EXCEPT only records in the left table