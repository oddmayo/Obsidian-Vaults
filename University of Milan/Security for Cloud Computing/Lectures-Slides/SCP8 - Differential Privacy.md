# October 14 - 2022
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

