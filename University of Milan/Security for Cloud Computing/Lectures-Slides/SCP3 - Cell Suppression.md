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
