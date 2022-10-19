# October 6 - 2022

# Network Models, Random Networks and Degree Distribution

## Network models

*Data-driven approach*: measure the structure of the network with mathematical, statistical and computational methods for making sense of the data we get

Why do we need network models?

### 1. Property effect

If we know a network has some particular **property**, what **effects** will that have on the overall behavior of the system?

To get a feel for these effects we build mathematical models so the properties of these networks can be **calculated analytically**, or at least numerically

### 2. Null model

A large part of understanding what properties measured in a network are interesting depends on having an **appropriate reference point**

**Random network models** represent the conventional reference point (*null model*)

Compare the network with the observed property to networks without it

### 3. Growing mechanism and prediction

Allow us to identify the mechanism of the system that produces an empirically **observed pattern**, and therefore to **better understand and predict** networks and to immediately understand the nature of a new network when we see that pattern

### Definition

A network (or graph) model is a mathematical model of a network in which some specific **parameters are fixed**, but is random in all other respects

The aim is to build models that **reproduce some or all properties of real-world networks**

## Random networks

The challenge is to decide **where to place the links** between the nodes so that we reproduce a system

We assume that this goal is best achieved by **placing the links randomly between the nodes**

### Models

Two definitions of a random network:

- $G(N,L)$: $N$ labeled nodes are connected with $L$ randomly placed links
model fixes the total number of links

The average degree of a node is simply $<d> = \frac{2L}{N}$


- $G(N,p)$: each pair of $N$ labeled nodes is connected with probability $p$
model fixes the probability $p$ that two nodes are connected

Here the average degree seems to be more complicated but asymptotically the two models are equivalent, plus other network characteristics are easier to calculate in this model

---

**A random network consists of $N$ nodes where each node pair is connected with probability $p$**

### Erdos-Renyi model

![[Pasted image 20221017092025.png]]

![[Pasted image 20221017092506.png]]

$P(L)$: the probability to have exactly $L$ links in a network of $N$ nodes and probability $p$:

![[Pasted image 20221017093230.png]]

#### Binomial distribution
![[Pasted image 20221017093314.png]]

---
The average number of links $<L>$ in a random graph
![[Pasted image 20221017093627.png]]

The variance
![[Pasted image 20221017093653.png]]

### How to choose $N$ and $p$ for comparison with the network under study

Real network: $N,L$
Random network: $N,p$ with $N$ as the real network

What about $p$?

$p$ such that $<L_{random}>$ in the random network is equal to the number of links in the real network

$<L_{random}> = L$

![[Pasted image 20221017094137.png]]
![[Pasted image 20221017094154.png]]

So $p = \Delta$

### An ensemble of networks

The model is defined as an ensemble, not in terms of a single randomly generated network

Properties of random networks usually means the **average properties of the ensemble**

Some properties can be calculated analytically (as the average number of links), others generating an ensemble of networks with the same parameters and **computing the average of the property** on them

---

This models are very useful to compare with real-world network behavior

While studying a phenomenon at the real network, **we can use a random model to realize if the phenomenon carries information or it is random**

### Random directed networks

The Erdos-Renyi network model
Directed networks

$p = \Delta$

## Degree distribution
![[Pasted image 20221019085551.png]]

As the network size increases, the distribution becomes increasingly narrow - we are increasingly confident that the degree of a node is in the vicinity of $<k>$ 

### Poisson distribution
![[Pasted image 20221019085915.png]]

For large **N** and small **k**, the degree distribution can be approximated by the Poisson distribution:
![[Pasted image 20221019090233.png]]

That's why it is also called Poisson random model
![[Pasted image 20221019090337.png]]

![[Pasted image 20221019090419.png]]

It **does not depend on N**

---

How big the differences are between the node degrees in a random network?
Can high-degree nodes coexist with small-degree nodes?
![[Pasted image 20221019090543.png]]

![[Pasted image 20221019090625.png]]

The number of friends a typical individual has is between 968 and 1032, a narrow window

---

We define $k_{max}$ such that in a network of $N$ nodes we have at most one node with degree higher than $k_{max}$
![[Pasted image 20221019090833.png]]

![[Pasted image 20221019091049.png]]

$\rightarrow$ the most connected individual has degree $K_{max}$ ~ 1185
$\rightarrow$ the least connected individual has degree $K_{min}$ ~ 816
$\rightarrow$ the number of friends a typical individual has is between 968 and 1032

The probability to find an individual with degree $k>2000$ is $10^{-27}$. Hence the chance of finding an individual with 2000 acquaintances is so tiny that such nodes are virtually inexistent in a random society

$\rightarrow$ a random society would consist a mainly average individuals with everyone roughly the same number of friends
$\rightarrow$ it would lack outliers, individuals that are either highly popular or recluse, no hubs

**This prediction blatantly conflicts with reality**

---

# Scale-free property

## Introduction

The world wide web Network
Nodes: **WWWW documents**
Links: **URL links**

N: around $10^{12}$ the largest network, even larger than the human brain ($N^{11}$)
crawler: collects all URL's found in a documented and follows them recursively

![[Pasted image 20221019094350.png]]

## World wide web

If the WWW were to be a random network, the degrees of the Web documents should follow a Poisson distribution
![[Pasted image 20221019094450.png]]

The incoming **a** and outgoing **b** degree distribution of the WWW sample mapped in the 1999 study of Albert et al.
![[Pasted image 20221019094747.png]]

The distributions are shown on double logarithmic axis (log-log) in which a power law follow a straight line

The symbols correspond to the empirical data and the line corresponds to the power-law fit

We also show the degree distribution predicted by a Poisson function with the average degree $<kin> = <kout> = 4.60$ of the WWW sample

## Facing reality

Degree distribution of real networks

![[Pasted image 20221019095831.png]]

## 80/20 rule

80 percent of money is earned by only 20 percent of the population


![[Pasted image 20221019100011.png]]

Vilfredo Pareto and the 80/20 rule: **These kind of decisions are present in networks as well**, 80 percent of links on the web point to only 15 percent of webpages.

Typically all quantities obeying the 80/20 rule follow a power law distribution

## Discrete vs Continuum formalism
![[Pasted image 20221019100407.png]]

## The difference between a power law and an exponential distribution

![[Pasted image 20221019100655.png]]

- For **small** $k$ the power law is above the Poisson distribution
	- A scale-free network has a large number of small degree nodes, most of which are absent in a random network

- For $k$ in the **vicinity** of $<k>$ the Poisson distribution is above the power law
	- In a random network there is an excess of nodes with degree $k\approx<k>$


The main difference between a random and a scale-free network comes in the *tail* of the degree distribution, representing the high-k region

- For **large** $k$ the power law is again above the Poisson curve. The probability of observing a high-degree node, or hub, is several orders of magnitude higher in a scale-free than in a random network


**Definition**: a scale-free network is a network whose degree distribution follows a power law

### Hubs

**Let us use the WWW to illustrate the properties of the high-k regime**
The probability to have a node with $k$~100 is
- About $P_{100}\simeq10^{-30}$ in a Poisson distribution
- About $P_{100}\simeq10^{-4}$ in a power law distribution

Consequently, if the WWW (10^12 nodes) were to be a random network:
- According to the Poisson distribution we would expect $10^{-18}$ $k>100$ degree nodes
- According to the power-law prediction, we expect about $10^{8}$ $k>100$ degree nodes

### The size of the biggest hub

All real networks are finite $\rightarrow$ let us explore its consequences
$\rightarrow$ We have an expected maximum degree, $k_{max}$
![[Pasted image 20221019171804.png]]

![[Pasted image 20221019172618.png]]

## The meaning of scale-free

Networks with a power law tail in their degree distribution are called 'scale-free networks'

- Correlation length diverges at the critical point: the whole system is correlated
- **Scale invariance**: there is no characteristics scale for the fluctuation (scale-free behavior)
- **Universality**: exponents are independent of the system's details

## Divergence of the higher moments

![[Pasted image 20221019175600.png]]

![[Pasted image 20221019175800.png]]
![[Pasted image 20221019180542.png]]

## Universality

### Internet backbone

**Nodes**: computers, routers
**Links**: physical lines

![[Pasted image 20221019180713.png]]
![[Pasted image 20221019181504.png]]


### Science citation index

**Nodes**: papers
**Links**: citations
![[Pasted image 20221019181634.png]]

###  Science coauthor-ship
![[Pasted image 20221019181900.png]]

### Online communities
![[Pasted image 20221019181956.png]]

![[Pasted image 20221019193344.png]]

### Metabolic network

![[Pasted image 20221019193504.png]]


### Topology of the protein network
![[Pasted image 20221019194115.png]]

### Human interaction network
![[Pasted image 20221019194208.png]]

### Actor network
![[Pasted image 20221019200537.png]]

### Swedish se-web
![[Pasted image 20221019200605.png]]

### Timeline scale-free networks
![[Pasted image 20221019200734.png]]

## Not all networks are scale-free

Networks appearing in material science, like the network describing the bonds between the atoms in crystalline or amorphous materials, where each node has has exactly the same degree

The neural network of the C. elegans worm

The power grid, consisting of generators and switches connected by transmission lines

## Plotting power laws

![[Pasted image 20221019201012.png]]

## Drawback

The **random network** model is characterized by a **Poisson degree distribution**, in contrast to a *power-law distribution* as seen in *real networks*

In a random network all vertices are alike, while real networks are characterized by a small number of vertices with very large degree while most vertices maintain a very low degree



