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

## An ensemble of networks

The model is defined as an ensemble, not in terms of a single randomly generated network

Properties of random networks usually means the **average properties of the ensemble**

Some properties can be calculated analytically (as the average number of links), others generating an ensemble of networks with the same parameters and **computing the average of the property** on them

---

This models are very useful to compare with real-world network behavior

While studying a phenomenon at the real network, **we can use a random model to realize if the phenomenon carries information or it is random**

## Random directed networks

The Erdos-Renyi network model
Directed networks

$p = \Delta$

