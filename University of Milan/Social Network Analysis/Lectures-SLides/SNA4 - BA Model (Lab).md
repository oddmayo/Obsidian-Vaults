# October 7 - 2022

# BA Model

Hubs represent the most striking difference between a random and a scale-free network. Their emergence in many real systems raises several fundamental questions:

- Why does the random network model of Erdos and Renyi fail to reproduce the hubs and the power laws observed in many real networks?
- Why do so different systems as the WWW or the cell converge to a similar scale-free architecture? (different type of nodes, links, history and purpose)


Why are hubs and power laws absent in random networks?
There re **two hidden assumptions** of the Erdios-Renyi model, that are violated in real networks

## Growth and preferential attachment

**ER model**: the number of nodes, N, is fixed (static models)

networks expand through the addition of new nodes

In 1991 the www had a single node, today the Web has over a trillion (10^12) documents

The protein interaction network may appear to be static, yet it is not. The number of genes in a human cell has grown from a few to over 20000 in four billion years

If we wish to model these networks, we cannot resort to a static model. Our modeling approach must instead acknowledge that networks are the product of a steady growth process
![[Pasted image 20221019210734.png]]

ER model: links are added randomly to the network

**Growth**: while nodes in random network model assumes that the number of nodes is fixed (time invariant), real networks are the result of a growth process that continuously increases

---

**BA model**: New nodes prefer to connect to the more connected nodes (*Rich-gets-richer phenomenon*)

### Preferential attachment

As our knowledge is biased towards the more connected nodes, we are more likely to link to a hub that to a node with only few links

For example: the more cited is a paper, the more likely that we will notice it; the more movies an actor has played in, the higher are the chances that se/she will be considered for a new role

![[Pasted image 20221019213206.png]]

## The Barabasai-Albert model

![[Pasted image 20221019214201.png]]

![[Pasted image 20221019214229.png]]

It shows nine subsequent steps of the Barabasi-Albert model
Empty circles: newly added nodes deciding where to connect their two links using preferential attachment
A few nodes gradually turn into hubs

It leaves many mathematical details open:
- it does not specify the precise initial configuration of the first $m_0$ nodes
- it does not specify whether the $k$ links assigned to a new node are added one by one, or simultaneously. This leads to potential mathematical conflicts: If the links are truly independent, they could connect to the same node $i$, resulting in multi-links and loops

The first mathematical model was introduced by Bollobas et al: Linearized chord diagram model

## Time in networks

Real networks evolve over rather different time scales:

World wide web: The first webpage was created in 1991. Given its trillion documents, the WWW added a node each millisecond ($10^3$ sec)

Cell: With roughly 20000 genes in a human cell, on average the cellular network added a node every 20000 years ($\sim10^{13}$ sec)

In network theory we use **event time**, advancing our time-step by one each time when there is a change in the network topology
![[Pasted image 20221019221351.png]]

---

Do we need both growth and preferential attachment? **YES**

*The absence of preferential attachment* leads to a growing network with a stationary but exponential degree distribution

*The absence of growth* leads to the loss of stationarity, forcing the network to converge to a complete graph

The BA model is only a minimal model