# October 6 - 2022
# Identity Disclosure

## Definition of K-anonymity

**K-anonymity**, together with its enforcement via *generalization* and *suppression* has been proposed as an approach to protect respondents' identities while releasing truthful information

It tries to capture the following requirement:

**the released data should be indistinguishably related to no less than a certain number of respondents**

Quasi-identifier: attributes that can be exploited for linking

*Basic idea*: translate the K-anonymity requirement on the released data

**Each release of data must be such that every combination of values of quasi-identifiers can be indistinctly matched to at least k respondents** 

K-anonymity requires that each quasi-identifier value appearing in the released table must have at least **k occurrences**

## Generalization and suppression to enforce K-anonymity

**Generalization**: the values of a given attribute are substituted by more general values

**Suppression**: protect sensitive information by removing it (it can reduce the amount of generalization)

### Domain generalization hierarchy

A **generalization relationship** $\leq_D$ defines a mapping between domain D and its generalizations

Given two domains $D_i,D_j \in DOM, D_i \leq_D D_j$ states that the values in domain $D_j$ are generalizations of values in $D_i$ 

$\leq_D$ implies the existence, for each domain $D$, of a **domain generalization hierarchy** $DGH_D = (DOM, \leq_D)$:

![[Pasted image 20221009185701.png]]

### Value generalization hierarchy

A **value generalization relationship** $\leq_V$ associates with each value in domain $D_i$ a unique value in domain $D_j$, direct generalization of $D_i$

$\leq_V$ implies the existence, for each domain D, of a **value generazation hierarchy** $VGH_D$

$VGH_D$ is a tree:
- The leaves are the values in $D$
- The root is the value in the maximum element in $DGH_D$

#### Domain and value generalization hierarchies - Example

![[Pasted image 20221009190019.png]]


### Generalized table with suppression

Let $T_0$ and $T_G$ be two tables defined on the same set of attributes. Table $T_G$ is said to be a **generalization (with tuple suppression)** of a table $T_0$ if:

1. The cardinality of $T_G$ is **at most** that of $T_0$
2. The domain of each attribute $A$ in $T_G$ **is equal** to, or a **generalization** of, the domain of attribute $A$ in $T_0$
3. It is possible to define a **correspondence** (an injective function) associating each tuple $t_G$ in $T_G$ with a different tuple $t_0$ in $T_0$, such that the value of each attribute in $t_G$ is equal to, or a generalization of, the value of the corresponding attribute in $t_0$

#### Generalized table with suppression - Example

![[Pasted image 20221009190653.png]]

### Better to suppress or generalize?

- **Suppression** is equivalent to **generalization** to the most (if unique) **general value**: complete information loss on the cell
- If **generalization** operates at the level of **attribute** (column) and **suppression** at the level of **cell** (value), generalizing may increase information loss
- Assume a *threshold* of **suppression**, if required suppression is:
	- below the threshold $\rightarrow$ suppress
	- above the threshold $\rightarrow$ generalize

## Minimal generalization

Generalization and suppression cause **information loss**
- do not **overdue it**

*Minimal solution*: suppress and generalize **as needed, not more**


### K-minimal generalization with suppression

![[Pasted image 20221009191319.png]]


![[Pasted image 20221009191614.png]]

#### Minimal generalization - Example

![[Pasted image 20221009191808.png]]

![[Pasted image 20221009191823.png]]

#### Minimal generalization - Example 2

![[Pasted image 20221009191930.png]]

### Computing a preferred generalization

Different **preference criteria** can be applied in choosing a preferred minimal generalization, among which:

- **Minimum absolute distance** prefers the generalization(s) with the smallest absolute distance: smallest number of generalization steps
- **Minimum relative distance** prefers the generalization(s) with the smallest relative distance: minimal total number of relative steps
- **Maximum distribution** prefers the generalization(s) with the greatest number of distinct tuples
- **Minimum suppression**: prefers the generalization(s) that suppresses less tuples, that is, the one with the greatest cardinality