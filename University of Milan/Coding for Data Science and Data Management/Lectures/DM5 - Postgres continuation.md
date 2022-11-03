
Creation of foreign keys

Different referential integrity policies

**Postgres connection**

When you install Postgres, a default username is specified and it its called postgres (superuser)

Still working on the dsedb schema

``` sql
-- create the table for containing person data
-- person(id, bio, birth_date, death_date, given_name)
-- max length of varchar is 256
-- date domain yyyy-mm-dd, 2022-04-26, not correct: 2022-02-32
-- constraints: PRIMARY KEY

CREATE TABLE dsedb.person(
	id varchar(10) PRIMARY KEY,-- possible values: 0034304, 234933 ; integer for math operations ; varchar use less space
	bio text,
	birth_date date,
	death_date date,
	given_name varchar(200) NOT NULL,

);

-- create the table country
-- country(iso3, name)
-- country ITA - Italy
-- country USA - United States
CREATE TABLE dsedb.country(
	iso3 char(3) PRIMARY KEY, -- primary key already means unique and not null
	name varchar(100) UNIQUE NOT NULL

);
	
-- producer table with attrbiutes as foreign keys
CREATE TABLE dsedb.producer(
	country char(3),-- same datatype as the foreign that is being referenced
	movie varchar(10), -- same datatype...
	FOREIGN KEY(country) REFERENCES dsedb.country(iso3),
	FOREIGN KEY(movie) REFERENCES dsedb.movie(id),
	PRIMARY KEY(country, movie)
);


-- inserting data specifying which attributes
INSERT INTO dsedb.movie(id,official_title,year,budget)
VALUES(1212,'another name',2005,50000); -- single quotes for text data

```

