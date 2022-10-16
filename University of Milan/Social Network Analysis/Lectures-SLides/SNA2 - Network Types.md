# September 30 - 2022

# Affiliation and Bipartite networks
We will consider networks which have:
- No loops
- No multiple edges

Also:
- Directed and undirected networks
- Weighted and unweighted networks

## A special case: Affiliation networks

They have two types of nodes:
- Actors
- Groups

Representation by bipartite (two-mode) networks

Links connect actors to groups
- No links between actors
- No links between groups

Actors are connected via comembership of groups

![[Pasted image 20221016201936.png]]

The incidence matrix is a rectangular matrix $g$x$n$
![[Pasted image 20221016202010.png]]

## One-mode projections
![[Pasted image 20221016202048.png]]

## One-mode weighted projection
![[Pasted image 20221016202333.png]]

## Human disease network
Connects diseases to the genes whose mutations are known to cause or effect the corresponding disease

![[Pasted image 20221016204703.png]]

---

The first projection is the *disease network*, whose nodes are diseases. Two diseases are connected if the same genes are associated with them, indicating that the two diseases have common genetic origin

The second projection is the *gene network*, whose nodes are genes, and where two genes are connected if they are associated with the same disease

![[Pasted image 20221016204911.png]]

---

The full *Human Disease Network* connecting 1283 disorders via 1777 shared disease genes

![[Pasted image 20221016205011.png]]

## Tripartite networks
Construction of the tripartite recipe-ingredient-compound network, in which one set of nodes re recipes, like Chicken Marsala; the second set corresponds to the ingredients each recipe has (like flour, sage,...); the thirds set captures the flavor compounds, or chemicals that contribute to the taste of each ingredient
![[Pasted image 20221016211217.png]]

The *ingredient network* represents a projection of the tripartite network. Each node denotes an ingredient; the node color indicating the food category and node size indicates the ingredient's prevalence in recipes.

Two ingredients are connected if they share a significant number of compounds. Link thickness represents the number of shared compounds

![[Pasted image 20221016211441.png]]

---

# Density and Average Degree

## Density of networks
Does the network have few/many links given the number of nodes? The density is related to the number of links built by the nodes

## Undirected networks
### Node degree
**Number of links connected to a node**

Notation: $d_i$ or $k_i$

![[Pasted image 20221016212145.png]]

Given the set of nodes $N$ and the set of links $L$ of a network $G(N,L)$, we can compute the degree $d_i$ of each node $i$ of the network

![[Pasted image 20221016212234.png]]

### Average degree
Given $G(N,L)$ we compute the degree of each node $i$ of the network

Then we can compute the average degree

**It is the average number of links per node**
![[Pasted image 20221016212500.png]]

### Degree
Suppose to know $N$ and $L$ only: we know the total number of nodes and links but we don't know where they are

Do we know the degree of each node of the network? $\rightarrow$ No
Do we know anything about node degree from $N$ and $L$ $\rightarrow$ **Average degree**

Writing the formula as a function of $N$ and $L$ only
![[Pasted image 20221016212820.png]]

$<d> = \frac{2L}{N}$
It is a **local property** mediated on the global network
No need to know where the links are in the networks

### Density
Is the **fraction of all possible links that are actually present**

The density of a network is the **ratio of the number of links $L$ to the number of possible links in a network with $N$ nodes** and is given by:

Numerators: $L$
Denominator: the maximum possible number of links in a network of $N$ nodes is:
![[Pasted image 20221016220143.png]]

Therefore:

![[Pasted image 20221016220230.png]]

### Density and average degree in summary
![[Pasted image 20221016222520.png]]

**Local**: the *degree* is related to the number of links of a *single node*
**Global**: the *density* is related to the number of links of the *whole network*

Relation between the density and the average degree:
![[Pasted image 20221016222832.png]]

## Directed networks
### Degree, in-degree and out-degree
**In-degree**: number of in-going links of a node $(j,i)$
**Out-degree**: number of out-going links of a node $(i,j)$
![[Pasted image 20221016223144.png]]

### Average in-degree and out-degree
![[Pasted image 20221016223221.png]]

The average in-degree is **equal** to the average out-degree

Writing the formula as a function of nodes $N$ and the number of links $L$
![[Pasted image 20221016223454.png]]

## Comparison
![[Pasted image 20221016223609.png]]

## Real networks are sparse
![[Pasted image 20221016223729.png]]

## Graph densification

"...Most of real networks densify over time, with the number of edges growing super-linearly in the number of nodes..."


