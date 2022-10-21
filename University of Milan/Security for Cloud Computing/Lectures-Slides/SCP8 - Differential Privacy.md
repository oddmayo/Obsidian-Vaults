# October 14 - 2022

# Examples of re-identification

## Re-identification with any information

**Any information** can be used to re-identify anonymous data
$\rightarrow$ ensuring proper privacy protection is a difficult task since the amount and variety of data collected about individuals is increased

Two examples: AOL and Netflix

## AOL data release

In 2006, AIL publicly posted to a website 20 million search queries for 650.000 users of AOL's search engine summarizing three months of activity

AOL suppressed identifying information and replaced these identifiers with **unique identification numbers** and made searches by the same user **linkable**
![[Pasted image 20221021204717.png]]

She was re-identified by two New York Times reporters
![[Pasted image 20221021204758.png]]

## Netflix prize data study

In 2006, Netflix provided 100 millions records revealing how nearly 500.000 of its users had rated movies from 1998 to 2005

Identifying information was removed, but a **unique user identifier** was assigned to preserve rating-to-rating continuity

Release was not $k$-anonymous for any $k>1$

Very little information is needed to de-anonymize and average subscriber record

**Movies may reveal your political orientation, religious views, or sexual orientations**


## Examples for privacy issues

### Privacy and genomic data

**Genomic information** is an opportunity for medicine but there are several **privacy** issues to be addressed

E.g., human genome
- **identifies** its owner
- contains information about **ethnic heritage**, **predisposition** to several **diseases**, and other **phenotypic traits**
- discloses information about the **relatives** and **descendants** of the genome's owner

![[Pasted image 20221021231601.png]]

### Sensitive inference from data mining

**Target case**

Second-largest discount retailer in the U.S.

![[Pasted image 20221021231928.png]]

Mining data reveals customers' **major life events**

## Inferences from social networks

People tend to **connect with others with **similar interests/activities/experiences

What one discloses **exposes** not only him but also **others**
![[Pasted image 20221021233000.png]]





# Privacy in data publication - Differential Privacy

## Our world is guided by data
![[Pasted image 20221016185144.png]]

## Data are invaluable

The *Big Data* concept has been adopted by many companies: entered the public vocabulary

Data are mostly about **individuals** whose **privacy** must be ensured

How can we work on private data?
$\rightarrow$ **anonymize** them and **share**

But...

## Anonymity is not enough

![[Pasted image 20221016185526.png]]

## Basic scenario
![[Pasted image 20221016185556.png]]

## Classic intuition for privacy
I would feel safe being in a database $D$ if:
- I knew that my data had no impact on the released results
$\rightarrow$ **computation over "D without me" = computation over "D"**
- I knew that the information **learned** about an individual by the published results $R$ is **no more** than the information we can learn about that individual **without** access to $R$

![[Pasted image 20221016185914.png]]




## Intuition

With or without including Alice in the database, her privacy risk **should not change much**
$\rightarrow$ the privacy of an individual is protected whenever the result $R$ **does not depend on her specific information**

Inferences about an individual from a differentially private computation are (**essentially**) limited to what could be inferred from everyone else's data **without her own data being included in the computation**

![[Pasted image 20221016190205.png]]

### Example

![[Pasted image 20221016190236.png]]

## Differential privacy and randomness

Differentially private analyses add **random noise** to the result

- Noise **masks** the differences between the **real-world computation** and the **opt-out scenario** of each individual in the database
- The outcome of a differentially private analysis is not exact but an **approximation**
- It may if performed twice on the same dataset, return **different results**
	- It is often possible to calculate **accuracy bounds** for the analysis

## Definition

Let databases $D$ and $D'$ be two **neighbors** database

An algorithm $A$ satisfies $\epsilon$-**differential privacy** if for all pairs of neighbor databases $D$, $D'$ and for all outputs $o$:

$$P[A(D) = o] \leq e^\epsilon P[A(D') = o]$$
An adversary should not be able to use $o$ to distinguish between any $D$ and $D'$

## The privacy budget $\epsilon$
Determine **how much noise** is added to the computation: trade-off between privacy and accuracy

The **smaller (larger)** the $\epsilon$ the **more (less)** the noise
- **small** $\epsilon \rightarrow$ **more** privacy, **less** utility
- *large* $\epsilon$ $\rightarrow$ *less* privacy, *more* utility

![[Pasted image 20221016191211.png]]

## Differential privacy and accuracy
![[Pasted image 20221016191247.png]]

