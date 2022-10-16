# 13 October - 2022
# Attribute Disclosure

## External knowledge

Consideration of the **adversary's background knowledge (or external knowledge)** is necessary when reasoning about privacy in data publishing

It can be exploited for inferring sensitive information

- Positive inference: a respondent **has** a given value (*focus*)
- Negative inference: a respondent **does not have** a given value

External knowledge may include: similar datasets, instance - level information...

Not possible to know a-priori what external knowledge the adversary possesses

## External knowledge modeling

An adversary has knowledge about an individual (target) represented in a released table and knows the individual's QI values
 $\rightarrow$ **predict the sensitive value of the target**

Modeled through a logical expression

Knowledge may be about:
- **the target individual**
- **others**: information about individuals other than the target
- **same-value families**: **genomic information** exposes also information about the relatives and descendants of the genome's owner

### Example

Released table is 4-anonymized but...
![[Pasted image 20221016162237.png]]

An adversary knows that **Harry, born in 64 and living in area 94139 is in the table**

![[Pasted image 20221016162337.png]]

The adversary can **infer that Harry belongs to the second group an that has aids with confidence** *1/4*

---

*From another dataset*, the adversary knows that **George (who is in the table, is born in 64, and lives in area 941*) has flu**

So the adversary can **now infer that Harry has aids with confidence** *1/3*

---

Finally, *from personal knowledge*, the adversary **knows that Harry does not have short breath**

$\rightarrow$ the adversary **infers that Harry has aids with confidence** *1/2*


## Multiple releases

Data may be subject to frequent changes and may need to be **published on regular basis**

The **multiple release** of a microdata table may cause **information leakage** since a malicious recipient can correlate the released datasets

### Example of independent releases

An adversary knows that **Alice, born in 1974 and living in area 94142, is in both releases**

![[Pasted image 20221016163208.png]]

The adversary can infer that since Alice belongs to the first group in $T_1$ and also to the first group in $T_2$, **she has aids because it is the only illness common to both groups**

---
An adversary **knows that Frank, born in 1964 and living in area 94132, is in $T_1$ but not in $T_2$**, thus he can infer that **Frank suffers from short breath** as it is the only patient in the orange set of time $t_1$ who left

---

**Multiple (i.e. longitudinal) releases** cannot be independent
$\rightarrow$ need to ensure multiple releases are safe with respect to **intersection attacks**

## Extended scenarios

k-anonymity, l-diversity and t-closeness different variations
- Multiple tuples per respondent
- Release of multiple tables
- Multiple quasi-identifiers
- Non-predefined quasi-identifiers
- Release of data streams
- Fine-grained privacy preferences

---


# Applications of k-anonymity

## Social networks

**Neighborhood attack**: given a de-identified graph $G'$ of a social network graph $G$, exploit knowledge about the neighbors of user $u$ to re-identify the vertex representing $u$

![[Pasted image 20221016165055.png]]


## Data mining

It aims at ensuring that the data mining results do not violate the k-anonymity requirement over the original data

Threats to k-anonymity can arise from performing mining on a collection of data maintained in a private table PT subject to k-anonymity constraints:
- **association rule** mining
- **classification** mining

### Association rule mining
![[Pasted image 20221016165339.png]]

### Classification mining - Decision trees

![[Pasted image 20221016165450.png]]

### Approaches for combining k-anonymity and data mining

**Anonymize-and-Mine**
![[Pasted image 20221016165558.png]]

**Mine-and-Anonymize**
![[Pasted image 20221016165614.png]]

## Location-based services

Protect identity of people in locations by considering always locations that contain no less than $k$ individuals:

1. Enlarge the area to include at least other k-1 users (**k-anonymity**)

![[Pasted image 20221016165824.png]]

2. Protect the location of users (**location privacy**): obfuscate the area so to decrease its precision or confidence
![[Pasted image 20221016165923.png]]

3. Protect the location path of users (**trajectory privacy**) [ALS-12]: block tracking by mixing/modifying trajectories
![[Pasted image 20221016170044.png]]

