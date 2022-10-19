# October 13 - 2022

# Connectivity

How nodes are connected via a sequence of links in a network

Two nodes are **adjacent** if they are connected via a link
![[Pasted image 20221019231320.png]]

Two links are **incident** if they share an end-point
![[Pasted image 20221019231513.png]]

An edge in a graph can be traversed when one starts at one of its end-nodes, moves along the edge, and stops at its other end-node

## Path

![[Pasted image 20221019231743.png]]

## Connected graph

A graph is **connected**, if there exist a path between any pair of node in it
![[Pasted image 20221019231909.png]]

A graph is **disconnected**, if it is not connected. It exist at least a pair of nodes which are not connected

## Connected components: intuition

Subgroup of nodes, with no connections
![[Pasted image 20221019232133.png]]

A connected component is a subgraph of a network such that there exists at least one path from each member of that subgraph to each other member, and no other vertex in the network can be added to the subgraph while preserving this property (*maximality*)

**Each node of the component is reachable from any other node of the component**

## Connected components in social networks

There is typically a very large component that fills most o the network, usually more than half and not infrequently over 90%, while the rest of the network is divided into a large number of small components
![[Pasted image 20221019232900.png]]

Can a network have two or more large components that fill a sizable fraction of the entire graph? Usually no, highly unlikely

## Connected components in directed networks

**A directed graph is strongly connected**: if there exists a directed path between any pair of nodes.

A strongly connected component is a *maximal* subset of nodes such that each can reach and is reachable from all the others along a directed path

**A directed graph is weakly connected**: if there exists a path between any pair of nodes, without following the edge directions

A weakly connected component is a *maximal* subset of nodes such that each can reach and is reachable from all the others along an undirected path

![[Pasted image 20221019233559.png]]


There is typically one large strongly connected component and a selection of small ones

The largest strongly connected component in the Web fills about a quarter of the network

---

# Random and Social Networks Connected Components

## Definitions

**Largest connected component**: the connected component compromising the *highest number of nodes*

**Giant component**: a connected component whose size (number of nodes) grows in proportion to the number of nodes $N$

## Connected components in social networks

Giant component and heavy-tail connected components size distribution

What about random networks?

## Growing a random network

Starting with $N$ isolated nodes, the links are added gradually through a random process

This corresponds to a gradual increase of $p$, with striking consequences on the network topology

To quantify this process, we first inspect how the size of the largest connected cluster within the network, $N_G$, varies with the average degree $<k>$
![[Pasted image 20221019234806.png]]

## Connected components in random networks

$N_G$: number of nodes in the giant component

Two extreme cases:
- $p=0 \rightarrow$ disconnected nodes, $<k> =0, N_G=1$
- $p=1 \rightarrow$ fully connected, $<k> =N-1, N_G=N$

One would expect that the largest component grows gradually from $N_G=1$ to $N_G=N$

## Size of the giant component
![[Pasted image 20221019235240.png]]

In other words, **we have a giant component if and only if each node has on average more than one link**

It is somewhat counterintuitive, however, that one link is sufficient for its emergence
![[Pasted image 20221019235605.png]]
![[Pasted image 20221019235706.png]]
![[Pasted image 20221019235731.png]]

---
1.
![[Pasted image 20221019235752.png]]

2.
![[Pasted image 20221020000102.png]]

3.
![[Pasted image 20221020000154.png]]

4.
![[Pasted image 20221020000215.png]]

## Summary
![[Pasted image 20221020000244.png]]

## Connected components
![[Pasted image 20221020000335.png]]

Supercritical: not fully connected
Internet: we should have routers that, being disconnected from the giant component, are unable to communicate with other routers
Power grid: some consumers should not get powered


Fully connected
Social media: no individual disconnected