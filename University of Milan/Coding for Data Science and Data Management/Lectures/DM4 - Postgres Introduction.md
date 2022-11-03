Our database is the schema inside the database

## Use of PgAdmin

Connect to Postgres with the superuser (the user created during the installation procedure)
- Create a database (specify name, encoding, and owner)
- Create a schema inside the database
- use the schema to create the database tables

A **DBMS** is a management system for many databases

In the common case the DBMS has one database with a multitude of schemas inside

In Postgres you can create many databases, each databases contains many schemas

---

On the dsedb empty schema

``` SQL 
-- SQL is composed of
-- DDL component: data definition language; creation of tables
CREATE TABLE
DROP TABLE
-- DML component: data manipulation language; quearying and populating
INSERT
DELETE
UPDATE
SELECT


-- Example: create the movie table of the imbd case-study
-- movie(id, official_tile, year, budget, length, plot)
-- possible data types: 
--varchar - character varying
--char - character string of fixed length
--integer - numeric data without decimal parts
--date, 
--decimal - numeric data with decimal parts
--boolean
--text - very long textual data
CREATE TABLE dsedb.movie(
id varchar(10) PRIMARY KEY,
official_title varchar(256) NOT NULL,
year char(4) NOT NULL,
budget decimal (12,2),
length integer CHECK(length > 0),
plot text,
UNIQUE(official_title, year)		
);

-- possible values of official_title: 'inception', 'the wolf of wallstreet'
-- possible values of year: '1974', 'abcd', '183 ' (postgres automatically fill in blanks)
-- possible values of budget: 234322.23, 284838.23, 9999999999.99
	
-- Another valid configuration considering a combination of attributes as primary key
CREATE TABLE dsedb.movie(
id varchar(10) UNIQUE,
official_title varchar(256) NOT NULL,
year char(4) NOT NULL,
budget decimal (12,2),
length integer,
plot text,
PRIMARY KEY(official_title, year)		
);
	
-- create the table crew
-- crew(personid, movieid, role, character)
	
CREATE TABLE dsedb.crew(
movieid varchar(10),
personid varchar(10),
role varchar(10),
character varchar(100),
PRIMARY KEY(movieid, personid, role)

);

```

