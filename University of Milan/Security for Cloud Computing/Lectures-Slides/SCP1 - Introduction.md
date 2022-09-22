# September 22 - 2022

**Written exam**

Can follow only slides and papers

Thursday 9:45am-11:15am - also via zoom (via celoria 10)
Friday 1pm-2:30pm

---

# Macrodata and Microdata Protection

When a company or *organization collects data* on people and is interested in making this information publicly available or **sell it to a third party**

- Outline DBMS: allow people from the outside access data through queries

- Macrodata protection
	- count and freq. tables
	- magnitude tables

- Microdata protection (more common nowadays)
	- masking techniques
	- synthetic techniques


## Statistical data dissemination

Often *statistical data* (or data for statistical purpose) are released

Such released data can be used to infer information that was **not
intended for disclosure**

Disclosure can: 
- occur based on the released data alone
- released data + public information
- released data + detailed external (public) data sources

The **disclosure risk** from the released data should be *very low*


## Statistical DBMS vs statistical data

- Statistical DBMS
	- responds only to statistical queries
	- need run time checking to control information

- Statistical data
	- publish statistics (macrodata release)
	- control on indirect release performed before publication

## Statistical DBMS

---
Respondent: people to whose collected data refer (for example a patient)
Recipient: people receiving/using released data (for example pharmaceutical company)

---

Is a DBMS that provides access to *statistics* about *groups* of individuals
- Should not reveal information about any *particular individual*

Confidential information can be deducted
- Combining the results of *different statistics*
- combining the results of statistics with *external knowledge*


### Example 1

Query: sum of the incomes of females with major in EE
![[Pasted image 20220922105222.png]]

Result: reveals the income of Baker (only female with EE) ) (50k)

This query is **sensitive** since it exposes confidential information of a single subject. It should **block** statistics computed over a *too small* number of respondents

### Example 2

*Query 1*: sum of the incomes of individuals with major in EE

![[Pasted image 20220922105512.png]]

Result: it does not reveal the income of any individual (240k)

This query is **not sensitive**


*Query 2*: sum of the incomes of males with major in EE 

![[Pasted image 20220922105730.png]]

Result: it does not reveal the income of any individual (190k)

This query is **not sensitive**

---

When we combine the queries:

![[Pasted image 20220922105958.png]]

![[Pasted image 20220922110010.png]]

This *combination* is **sensitive**



## Macrodata protection

## Macrodata vs microdata

In the past data we mainly released in tabular form (macrodata) and through statistical DBMS

Today many situations require that the specific stored data themselves, called microdata, be released
- more flexible and availability of information for recipients

**Micro data** are subject to **greater risk** of privacy breaches (*linking attacks*)


## Macro data

1. **Count/frequency**: Each cell contains the number (count) or the percentage (frequency) of respondents that have the same value over all attributes in the table

*Just counting* without any correlation

Example
Two dimensional table showing the number of employees by department and annual income

![[Pasted image 20220922111442.png]]

These table report marginal totals: sums of the rows or columns; sometimes published sometimes not

2. **Magnitude data**: Each cell contains an aggregate value of a quantity of interest over all attributes in the table

*Aggregation* 

Example
Average number of days spent in the hospital by respondents with a given disease

![[Pasted image 20220922111649.png]]

This table shows the value of an attribute

Microdata table example
Records about employees of company Alfa

![[Pasted image 20220922111813.png]]



