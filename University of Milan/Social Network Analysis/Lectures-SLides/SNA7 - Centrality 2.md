# October 20 - 2022

# Centrality

## Eigenvector centrality

### Eigenvector centrality (undirected)

It is an extension of the degree centrality

Not all friends are equivalent. This having more friends does not by itself guarantee that someone is more important, but having more **important friends** provides a stronger signal

It tries to generalize degree centrality by incorporating the importance of the neighbors

---
Idea
- Degree centrality: awarding nodes just one point for each friend
- Eigenvector centrality: awarding nodes a score proportional to the sum of the scores of its friends

---

$\lambda C_e=AC_e$
This means that $C_e$ is an eigenvector of adjacency matrix $A$ and $\lambda$ is the corresponding eigenvalue

Which eigenvalue-eigenvector pair should we choose?

### Theorem

To have positive centrality values, we can compute the eigenvalues of $A$ an then select the largest eigenvalue

The corresponding eigenvector is $C_e$

Based on the Perron-Frobenius theorem, all the components of $C_e$ will be positive, and this vector corresponds to eigenvector centralities for the graph

### Example

![[Pasted image 20221020131523.png]]

### Eigenvector centrality (undirected)

It can be computed also for directed networks but some issues arise

The adjacency matrix is asymmetric $\rightarrow$ it has two sets of eigenvectors, the left eigenvectors and the right eigenvectors

Which of the two should we use? Usually the right eigenvectors because it accounts for the ingoing links

---

A major problem with eigenvector centrality arises when it deals with directed graphs

Centrality only passes over outgoing edges and in special cases such as when a node is in a weakly connected component centrality becomes zero even though the node can have many edges connected to it

![[Pasted image 20221020131915.png]]

Node 1 has only outgoing...

**pending**

## Katz centrality

To resolve this problem we add a bias term $\beta$ to the centrality values for all nodes
![[Pasted image 20221020132015.png]]


Where
![[Pasted image 20221020132040.png]]

Rewriting equation in a vector form
![[Pasted image 20221020132103.png]]

**Katz centrality**: **pending**



---

## PageRank

Problem with Katz centrality: in directed graphs, once a node becomes an authority (high centrality), it passes **all** its centrality along **all** of its out-links

This is less desirable **pending**
![[Pasted image 20221020132314.png]]


### Example
![[Pasted image 20221020132532.png]]



---


# Reciprocity

If you'll become my friends, I'll be yours

dyad: a pair of nodes and the links between them (for both undirected and directed)



