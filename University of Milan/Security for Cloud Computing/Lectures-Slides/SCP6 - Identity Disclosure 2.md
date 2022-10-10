# October 7 - 2022
# Identity Disclosure

## Classification algorithms


### Classification of K-anonymity techniques

1. **Generalization**: can be applied at the level of single column or single cell
2. **Suppression**: can be applied at the level of row, column or single cells

![[Pasted image 20221010120601.png]]

#### 2 - anonymized tables wrt different models
![[Pasted image 20221010120702.png]]
![[Pasted image 20221010120807.png]]
![[Pasted image 20221010120835.png]]

![[Pasted image 20221010120855.png]]

### Examples of algorithms

The problem of finding minimal K-anonymous tables, with attribute generalization and tuple suppression is **computationally hard**

#### Incognito algorithm

K-anonymity with respect to a proper subset of $QI$ is a necessary (not sufficient) condition for K-anonymity with respect to $QI$

![[Pasted image 20221010121725.png]]

Incognito adopts a **bottom-up** approach for the visit of DGHs

##### Example

![[Pasted image 20221010122246.png]]

![[Pasted image 20221010122314.png]]

#### Mondrian multidimensional algorithm

Each attribute in $QI$ represents a **dimension**
Each tuple in PT represents a **point** in the space defined by $QI$

Tuples with the same $QI$ value are represented by giving a **multiplicity** value to points

The multidimensional space is partitioned by **splitting dimensions** such that each area contains at least $k$ occurrences of point values

All the points in a region are **generalized** to a unique value

The corresponding tuples are substituted by the computed generalization

---

Mondrian algorithm is flexible and can operate:
- on a different **number of attributes**
- with different **recoding** (generalization) strategies
- with different **partitioning** strategies
- using different **metrics** to determine how to split on each dimension

##### Example

![[Pasted image 20221010123159.png]]

![[Pasted image 20221010123215.png]]

### K-anonymity revisited

**K-anonymity requirement**: each release of data must be such that every combination of values of quasi-identifiers can be indistinctly matched to at least $k$ respondents

When generalization is performed at attribute level (AG) this is equivalent to require each quasi-identifier n-uple to have at least $k$ occurrences

When generalization is performed at cell level (CG) the existence of at least $k$ occurrences is a sufficient but no necessary condition; a less strict requirement would suffice

![[Pasted image 20221010125010.png]]

---

# Attribute Disclosure 

#### 2 - anonymous table according to the AG_ model

K-anonymity is vulnerable to some attacks

![[Pasted image 20221010182324.png]]

#### Homogeneity of the sensitive attribute values

All tuples with a quasi-identifier value in a k-anonymous table may have the same sensitive attribute value
- An adversary knows that Carol is a *black female* and that her data are in the microdata table
- The adversary can infer that Carol suffers from *short breath*

#### Background knowledge

Based on prior knowledge of some additional external information
- An adversary knows that Hellen is a *white female*  and she is in the microdata table
- The adversary can infer that the disease of Hellen is either *chest pain* or *short breath*
- The adversary knows that Hellen runs 2 hours a day and therefore that Hellen cannot suffer from *short breath*
	- the adversary infers that Hellen's disease is *chest pain*
![[Pasted image 20221010183121.png]]

### l-diversity

A $q$-block in $T$ is $l-diverse$ if it contains at least $l$ different **well represented** values for the sensitive attribute in $T$
- well represented: different definitions bases on entropy or recursion

l-diversity: and adversary needs to eliminate at least $l-1$ possible values to infer that a respondent has a given value

---

$T$ is $l-diverse$ if all its $q$-blocks are $l-diverse$
- the homogeneity attack is not possible anymore
- the background knowledge attack becomes more difficult

l-diversity is **monotonic** with respect to the generalization hierarchies considered for k-anonymity purposes

Any algorithm for k-anonymity can be extended to enforce the l-diverse property

**BUT**

l-diversity leaves space to attacks based on the distribution of values inside $q$-blocks (**skewness** and **similarity** attacks)

#### Skewness attack

Occurs when the distribution in a $q$-block is different than the distribution in the original population

![[Pasted image 20221010184613.png]]

#### Similarity attack
Happens when a $q$-block has different but semantically similar value for the sensitive attribute

![[Pasted image 20221010184708.png]]

### t-closeness / Group closeness

A q-block respects $t-closeness$ if the distance between the distribution of the values of the sensitive attribute in the $q$-block and in the considered population is lower than $t$

$T$ respects $t-closeness$ is all its $q$-blocks respect $t-closeness$

$t-closeness$ is **monotonic** with respect to the generalization hierarchies considered for k-anonymity purposes

Any algorithm for k-anonymity can be extended to enforce the $t-closeness$ property, which however might be difficult to achieve