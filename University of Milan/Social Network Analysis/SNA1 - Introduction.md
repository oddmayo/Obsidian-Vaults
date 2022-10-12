# September 29 - 2022
# Introduction
## Program

- Basic notions for networks from graph theory
- Networks models: Random model, Erdos Renyi model, scale free networks,
- small world networks
- Connected components
- Node centrality
- Link strength and reciprocity
- Transitivity, Triadic closure and Clustering coefficient
- Ego networks
- Node similarity
- Node assortativity
- Dense subgraphs and Community detection
- Information diffusion

Network visualization and basic analysis with Gephi
Social Network analysis with Python: the NetworkX library


## Final examination

A small project on the visualization and analysis of a network from publicly available datasets (Gephi and/or Python)

Questions about definitions, methods, algorithms, concepts and calculations on the topic covered in the course, as well as discussions on real-data case studies

---

# Social Network Analysis

## Sociological analysis

In 1974, Blau defined the field of *sociology* as follows:

...Social structures are defined by their parameters - the criteria underlying the differentiation among people and governing social interaction...

The initial focus on the individual

## A network perspective

In the 1930s, a new perspective on human data was developed: *sociometry*

Instead of only looking at attributes of single persons or aggregating measures of group of persons

Take into account who is connected to whom

## Early social network analysis

Dr. Jacob Levy Moreno is considered the pioneer of SNA. In 1993 he displays the first sociogram at a meeting of the Medical Society of the state of New York

![[Pasted image 20221012200933.png]]

Four features found in moderns social network analysis:
- motivated by a structural intuition based on ties linking social actors
- grounded in systematic empirical data
- heavily on graphic imagery
- relied on the use of mathematical and/or computational models


## Social network analysis

Wasserman-Faust:

"
Focus on relationships among social entities, and on the patterns and implications of these relationships...

...**Fundamental difference**: inclusion of concepts and information on **relationships among units in a study**. Views characteristics of the social units as rising out of **structural or relational processes** or focuses on properties of the relational systems themselves

Relational ties among factors are primary and attributes of actors are secondary
"

**Definition**

It is the process of *investigating social structures through the use of networks and graph theory*

It is both an approach to understanding social structure and a method of analysis which can be applied to other domains.

Focus on Complex Networks: the heart of complex systems

---

Behind each complex system there is a network that defines interactions between the components

We will never understand complex systems unless we map out and understand the networks behind them

At the end, **networks permeate science, technology and nature**

---

Most networks observed in nature, society and technology are driven by *common organizing principles*

networks appear to be more similar than different from each other


## Network science

We have known graphs for centuries (1735) but network science has emerged only in the twenty-first century

Two forces helped the emergence of network science:

### Network maps

Used to **describe the behavior of a system** consisting of hundreds to billions of interacting components

In the past we either lacked the tools or it was difficult to keep track the amount o data. The emergence of the internet changed this


### The universality of network characteristics

The architecture of networks emerging in various domains of science, nature and technology are similar to each other, a consequence of being governed by the same organizing principles

**We can use a common set of mathematical tools to explore these systems**

---

# Networks and Graphs

**Network**: finite set of actors (nodes, vertices) and the **relations** (links, ties, edges) defined on them

In network science *relation ties among actors are primary* and attributes of actors are secondary

## From complex systems to networks

The choice of the proper network representation determines our ability to use network theory successfully

In some cases there is a unique representation, in other cases not

For example, the way we assign the links between individuals will determine the nature of the question we can study

![[Pasted image 20221012205020.png]]

## Graphs
The **mathematical representation** of a network is a graph

![[Pasted image 20221012205125.png]]

$$G(N,L) \ or \ G(V,E)$$

A graph is an ordered pair $G=(V,E)$ comprising a set of $V$ vertices, with a set of $E$ edges, which are 2-element subsets of $V$ 
![[Pasted image 20221012205408.png]]

We will use the following notation to denote both the network and the relative graph: $G = (N,L)$ where $N = {n_1,n_2,...,n_N}$ is the set of $N$ nodes of the network and $L={l_1,l_2,...,l_L}$ is the set of $L$ link of the network

![[Pasted image 20221012205832.png]]


### Undirected graph

In an undirected graph, a link is an unordered pair of vertices $(n_i,n_j)$. Note that $(n_i,n_j)$ and $(n_j,n_i)$ are the same edge

Two nodes $n_i$ and $n_j$ are *adjacent* if $(n_i,n_j)$ exists in $L$

Two links are *consecutive* if they share and end-point

### Directed graph or digraph

Edges can have directions. A directed edge is sometimes called and *arc*. In a directed graph a relation from node $n_i$ to node $n_j$ is an ordered pair of nodes $l_k=(n_i,n_j)$ 

The two links $(n_i,n_j)$ and $(n_j,n_i)$ are different

A directed graph is a graph whose links are directed
$n_i$ is called *origin, sender*
$n_j$ is called *terminus, receiver*

## Graph drawing

Represented visually by **drawing a dot or circle for every vertex**, and **drawing an arc between two vertices if they are connected by an edge**. If the graph is directed, the directions is indicated by drawing an arrow

### Example
![[Pasted image 20221012211021.png]]
![[Pasted image 20221012211056.png]]

## Networks and graphs

Different networks, same graph representation $N=4$ nodes and $L=4$ links

![[Pasted image 20221012211332.png]]

![[Pasted image 20221012211342.png]]


Complex system $\rightarrow$ Network $\rightarrow$ Graph $\rightarrow$ Wiring diagram


## Graph mathematical representation

- Edge list
- Adjacency list
- Adjacency matrix

### Edge list
![[Pasted image 20221012211603.png]]

### Adjacency list

![[Pasted image 20221012211619.png]]

### Adjacency matrix

![[Pasted image 20221012211641.png]]

### Directed graphs

![[Pasted image 20221012211733.png]]


![[Pasted image 20221012211814.png]]

### Adjacency
![[Pasted image 20221012211834.png]]

### Simple undirected (and directed) networks

A *loop* is and edge between the same node $(n_i,n_i)$

A simple graph is an undirected graph containing no graph loops or multiple edges

![[Pasted image 20221012212109.png]]

### Weighted networks

A weighted graph is one where **edges are associated with weights**

For example, in a graph with nodes as cities and edges as routes, the weighted associated with each edge could represent the distance between these cities

![[Pasted image 20221012212259.png]]

