# September 29 - 2022

## Cell suppression

One of the most used ways of protecting sensitive cells
Suppressing sensitive cells (*primary suppression*) is **not sufficient**

At least one additional cell must be suppressed (*complementary suppression*) for each row or column with a suppressed sensitive cell (*primary*)

Even after this it is difficult to guarantee adequate protection

## Complementary suppressions

The selection of cells for this process is **complicated**

**Linear programming** techniques are used, also **audit techniques** can be applied to evaluate the proposed suppression pattern

### Table without disclosures example

Table containing information about employees by company and education level

![[Pasted image 20221006200137.png]]

A cell with fewer than **5** respondents in defined as sensitive

Suppressing the sensitive cells:

![[Pasted image 20221006200219.png]]

Not sufficient:

$35 = D_1 + 10 + 10 + 14 \rightarrow D_1 = 1$
$30 = D_2 + 10 + 10 + 7 \rightarrow D_2 = 3$
$50 = 15 + 20 + D_4 + 12 \rightarrow D_4 = 3$
$35 = 12 + 14 + 7 + D_6 \rightarrow D_6 = 2$
$20 = 15 + 1 + 3 + D_3 \rightarrow D_3 = 1$
$25 = 3 + 10 + 10 + D_5 \rightarrow D_5 = 2$

So now we suppress one additional cell for each row/column with a sensitive cell suppressed

![[Pasted image 20221006200733.png]]

The table appears to offer protection to the sensitive cells, but:

![[Pasted image 20221006201138.png]]


This table provides adequate protection:

![[Pasted image 20221006201241.png]]


But out of a total of 16 cells, only 7 cells are published, while 9 are suppressed

## Rounding

To reduce data loss due to suppression, use rounding values to a multiple of the sensitive threshold

- **Random**: random decision on whether cell values will be rounded up or down
	- Recipients may lose confidence in the data because sum value may differ from published marginal totals
- **Controlled**: ensure that the sum of published entries is equal to published marginal totals

*Note*: all cell values must be multiple of the threshold value

### Random rounding example

![[Pasted image 20221006204756.png]]


### Controlled rounding example
![[Pasted image 20221006204821.png]]

Linear programming methods are used to identify a controlled rounding for a table

**Disadvantages**:
- It requires the use of specialized computer programs
- Controlled rounding solutions *may not always exist* for complex tables

## Confidentiality edit
Developed y the U.S. Census Bureau in 1990

Two approaches:
1. to protect the regular decennial Census data (100% of the population)
2. to protect the long-form of the Census which refers to a sample of the population

Both apply statistical disclosure limitation techniques to the microdata

For the 100% microdata file, *confidentiality edit* applies **switching**:

1. Take a *sample* of records
2. Find a *match* for these records in some other geographic region, matching on a specified set of important attributes
3. *Swap* all attributes on the matched records

For small blocks, the sampling fraction is increased
The microdata file can be used directly to prepare macrodata tables

### Confidentiality edit example

Records for the 20 employees of company Alfa
Take a sample of records from the microdata file (say 10% sample)
![[Pasted image 20221008113453.png]]

Since we need tables by company and education level, we find a match in some other company on the other variables

![[Pasted image 20221008113553.png]]

Part of the randomly selected 10% sample from other companies match records in company Alfa

![[Pasted image 20221008114126.png]]


### Confidentiality edit example 2

![[Pasted image 20221008114252.png]]
