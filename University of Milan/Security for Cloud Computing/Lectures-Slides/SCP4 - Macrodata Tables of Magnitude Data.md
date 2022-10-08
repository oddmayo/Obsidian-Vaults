# September 30 - 2022

# Macrodata Disclosure Protection Techniques: Tables of Magnitude Data

## Protection of tables of magnitude data -1

Magnitude data are generally **nonnegative quantities** reported in surveys or censuses

The distribution of these values is likely to be **skewed**

Disclosure limitation techniques focus on preventing precise estimation of the values for **outliers**

Sampling is less likely to provide protection

The units that are most visible because of their size do not receive any protection from sampling

## Protection of tables of magnitude -2

1. Identify sensitive cells
	1. p-percent
	2. pq
	3. (n,k)
2. Protect sensitive cells: suppression
3. Verify result: audit, information loss, parameters disclosure

## Suppression rules

**Primary suppression rules** determine whether a cell could reveal individual respondent information; such cells are considered **sensitive**

Most common suppression rules
- the p-percent rule
- the pq rule
- the (n,k) rule

These rule verify whether it is enough difficult for one respondent to estimate the value reported by another respondent **too closely**

### p-percent

A cell is sensitive if *upper and lower estimates for the respondent's value are closer to the reported value than a pre-specified percentage p*

A cell is protected if:

$\sum^N_{i=c+2}x_i \geq \frac{p}{100}x_1$ 

$x_1, x_2,..., x_N$: respondent's value in decreasing order
$c$: size of a coalition of respondents interested in estimating $x_1$

The largest value $x_1$ is the most exposed

#### Primary suppression rule: p-percent example

Consider the respondents that contribute to the total income in a city, which is equal to 250k, to be (in decreasing order)

- Alice: 100K
- Bob: 80K
- Carol: 30K
- David: 20K
- Eve: 10K
- Frank: 3K
- ...

The most sensitive value is Alice's because it is **easier to estimate**

If Alice's income cannot be estimated accurately, the income of the other citizens is protected

Which is the coalition of **c = 3** respondents that can better estimate *Alice's income*?

**Bob, Carol, David** whose total income is 130K can estimate that Alice's income is **between 80K and 120K** 
- $\geq80K$ since it is higher than Bob's
- $\leq120K$ since $250K-130K = 120K$

Sensitive for any $p\geq20$

---

Formally, Alice's cell is protected for any $p$ such that:

![[Pasted image 20221008122832.png]]
![[Pasted image 20221008122856.png]]

![[Pasted image 20221008122912.png]]


$p\leq250-(100+80+30+20)$

$p\leq20$


# Privacy in Data Publication

