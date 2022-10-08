# September 23 - 2022
## Macrodata Disclosure Protection Techniques: tables of counts or frequencies

### Tables of counts or frequencies
Protection operates in *three steps*
1. Sampling
2. Identification of sensitive cells
	1. special rules
	2. threshold rules
3. Protection of sensitive cells
	1. table restructuring
	2. suppression

### Sampling
**Sample survey** rather than a census
Before aggregating estimates are multiplied by a **sampling weight**
If weights are not published $\rightarrow$ respondent's data less identifiable
Estimates must achieve a specified **accuracy**

### Identification of sensitive cells: special rules
**Special rules** define restrictions on the level of detail that can be provided in a table
Differ depending on: *agency* and *kind of the table*

#### Example
Social Security Administration (SSA) rules prohibit publishing tables where the value of a cell:
- is equal to a marginal total
- allow users to determine: an individual's age (5), earnings (1000), benefits (50) [intervals]
- to satisfy special rules: table restructuring and category combination

![[Pasted image 20221004120220.png]]

### Identification of sensitive cells: threshold rules
A cell is sensitive **if the number of respondents is less than some specified number**
A sensitive cell cannot be released
Different techniques can be applied **to protect them**: table restructuring, category combination, cell suppression, random rounding, confidentiality edit

#### Example
Table containing information about employees by company and education level
![[Pasted image 20221004120818.png]]

A cell with fewer than **5** respondents is defined as sensitive

### Protection of sensitive cells: restructuring
Number of employees by department and annual income
Special rule: income within a **5K** Euro interval
To protect confidentiality the table can be **restructured** and rows or columns **combined**

![[Pasted image 20221004122203.png]]

Combining $Dept_1$ with $Dept_2$ and $Dept_3$ with $Dept_4$ does offer the required protection:
![[Pasted image 20221004122401.png]]


Instead if we combine $Dept_2$ with $Dept_4$ it would reveal that the income is within a 5k interval [23K,27K]

![[Pasted image 20221006193255.png]]

