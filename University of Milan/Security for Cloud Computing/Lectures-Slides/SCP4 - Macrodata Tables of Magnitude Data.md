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

## Disclosure risk: kinds of disclosure

### Information disclosure

Attribution of sensitive information to a respondent (an individual or organization)

- A respondent is identified from the released data: **identity disclosure**
- Sensitive information about a respondent is revealed through the released data: **attribute disclosure**
- the released data make it possible to determine the value of some characteristics of a respondent even if no released record refers to him: **inferential disclosure**

### Identity disclosure

If a third party can **identify** a respondent from the released data

- *Macrodata*: generally **not a problem**, unless it leads to divulging confidential information
- *Microdata*: generally regarded as a **problem**, usually implies **attribute disclosure**

### Attribute disclosure

When **confidential information** about a respondent is revealed and can be attributed to her

- revealed exactly
- closely estimated

### Inferential disclosure

When information can be **inferred with high confidence** from statistical properties of the released data

Inferences are often poor predictors of individual data values

- by itself does not always represent a risk
- it may be used together with other information and increase potential for inference

## Disclosure risk: reduce it

### Restricted data and restricted access - 1

The choice of disclosure limitation methods depends on the nature of the data products whose confidentiality must be protected

Some microdata include **explicit identifiers**

Removing such identifiers is a **first step** in preparing for the release of microdata

---

Confidentiality can be protected by:

- restricting the **amount of information** in the released tables
- imposing **conditions on access** to the data product
- some combination of these two strategies


## Disclosure risk: the anonymity problem

The amount of private own records is increasing every day

These data are **de-identified** before release (remove explicit identifiers)

**De-identification is not sufficient**

Most municipalities sell population registers that include the identities of individuals along with basic demographics

These data can be used for linking identities with de-identified information: **re-identification**

![[Pasted image 20221009122320.png]]

## Disclosure risk: re-identification

### Classification of attributes in a microdata table

The attributes in the original microdata table can be classified as:

- **identifiers**: uniquely identify a microdata respondent
- **quasi-identifiers**: in combination, can be linked with external information to reidentify all or some of the respondents to whom information refers
- **confidential**: contain sensitive information
- **non confidential**: that the respondents do not consider sensitive and whose release do not cause disclosure


### Re-identification

A study of the 2000 census data reported that the US population was uniquely identifiable by:

![[Pasted image 20221009162323.png]]


### Factors contributing to disclosure risk - 1

1. **Existence of high visibility records**
2. **Possibility of matching the microdata with external information**

The possibility of linking or its precision increases with:
- The existence of a **high number of common attributes** between the microdata table and the external sources
- The **accuracy** of resolution of the data
- The number and richness of **outside sources**

### Factors contributing to decrease the disclosure risk

1. A microdata table often contains a **subset** of the whole population
2. Information released to the public is **not always up to date**
3. The information contain **noise** that decreases the ability to link information
4. The information can contain data expressed in **different forms**

### Measures of risk

Measuring the disclosure risk requires considering:

The probability:
- the respondents for whom an intruder is looking is represented on both the microdata and some external file
- that the matching variables are recorded in a linkable way on the microdata and on the external file
- that the respondent for whom the intruder is looking is unique in the population of the external file

**Unique population** plays a major role in the disclosure risk of microdata

Each population unique is a sample unique, the vice-versa is not true