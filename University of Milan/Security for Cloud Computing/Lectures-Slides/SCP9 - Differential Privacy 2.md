# October 20 - 2022

# Differential Privacy part II

## How to achieve differential privacy

Need to **calibrate the noise** to the **influence** an **individual** can have on the result

**Global sensitivity**: **characterizes** the scale of the influence of one individual (*worst case*), and hence **how much noise** we must add

### Examples

Database $D$ of patients

<u>How many</u> patients suffer from <u>diabetes</u>?

| Real world (D) | Opt-out (D') |
| ---------- | ------- |
| 50         | **49**        |


**GS(A)=1**

---

<u>How many</u> males and females are in the database?

| Real world (D) | Opt-out (D') |
| ---------- | ------- |
| 50         | **49**        |

| Real-world (D) | Opt-out (D') |
| -------------- | ------------ |
| M, F           | M, F         |
| 22, 34         | **21**, 34       |

$GS(A)=2$

## Laplace mechanism with sensitivity

Result $R$ is sampled from a **Laplace distribution** with **mean** the **true result** and some **scale** $\lambda$ (determined by $\epsilon$ and the global sensitivity of the computation)

$$R=A(D)+Z$$

$Z$ is a random variable drawn from the Laplace distribution
![[Pasted image 20221021192834.png]]


# Properties of Differential Privacy

## Closure under post-processing

Differential privacy is **resilient** to **post-processing**
$\rightarrow$ the computation of a function over the result of a **differentially private** computation cannot make it **less** differentially private
![[Pasted image 20221021193137.png]]
![[Pasted image 20221021193212.png]]
![[Pasted image 20221021193232.png]]

## Sequential and parallel composition

Differential privacy **composes** well **with itself**. But what does it mean?
- **Sequential composition**: sequence of $m$ computations over database $D$ with overlapping results
$$\epsilon_1+\epsilon_2+...+\epsilon_m$$
- **Parallel composition**: sequence of $m$ computations over disjoint subsets of a database $D$
$$\max(\epsilon,\epsilon,...,\epsilon_m)$$

### Sequential composition - example

**Privacy budget** $\epsilon$
Ask for count of female patients **and** count of patients suffering from diabetes

| **No. Females** | **No. Males** |
| --------------- | ------------- |
| 34              | 23              |

Cells can be overlapping (e.g. a female who suffers from diabetes)

Each count must be released in such a way that $\epsilon_1$ (first count) + $\epsilon_2$ (second count) be equal to $\epsilon$

### Parallel composition - example

**Privacy budget** $\epsilon$
Ask for count of people broken down by handedness, hair color
![[Pasted image 20221021194957.png]]

Each cell is a disjoint set of individuals

Each cell can be releases with $\epsilon$-**differential privacy**

## Group privacy

Differential privacy has been introduced for reasoning about the privacy of a **single individual** but allows also reasoning about the privacy of **groups**

Privacy guarantees that apply yo an **individual** with $\epsilon$ apply to a **group** of size $n$ with the privacy parameter becoming $n\epsilon$

# Differential Privacy Models

## Non interactive vs interactive
![[Pasted image 20221021195700.png]]

## Global vs local differential privacy

![[Pasted image 20221021195804.png]]

## Basic idea behind local differential privacy

**Each user** runs a differential private algorithm on her data

An external party (**not** necessarily **trusted**) combines all the (noised) data received from the users to get a final result

Noise can **cancel out** or be **subtracted**

True answer plus noise; noise is typically **larger than** in the global case

## Local differential privacy - Definition

A randomized algorithm $A$ satisfies $\epsilon$-**local differential privacy** iff for all input $x,x'$ and output $o$ of A:
$$P[A(x)=0]<=e^\epsilon \ P[A(x')=0]$$
$\rightarrow$ any output should not depend on user's secret

# Differential Privacy in the Real World

## Privacy in practice

In 20 United States Census Bureau deployed **OnTheMap**, a web based application that shows where workers are employed and where they live

Based on a variation of $\epsilon$-differential privacy, called **approximate differential privacy** (($\epsilon,\delta$)-**differential privacy**):
- $\epsilon$ is the privacy budget
- $\delta$ is related to the confidence ($1-\delta$) that the result satisfies $\epsilon$-differential privacy
![[Pasted image 20221021201105.png]]

![[Pasted image 20221021201130.png]]

Internal experiments confirmed that confidential microdata from the 2010 census can be reconstructed quite accurately

Since 2020 a new differentially private mechanism was adopted

Differential privacy based on **coin tossing** is widely deployed
- Google Chrome browser to collect browsing statistics (**Rappor**)
- **Apple iOS** and **MacOS** to collect typing statistics

All deployments are based on **randomized response**
![[Pasted image 20221021201448.png]]

### How Rappor works

Each user has one value $v$ out of a very large set of possibilities

Rappor solution is based on:
- *Bloom filter*
- two levels of randomized response: **permanent** and **instantaneous**

**Compression**: use **h hash functions** to hash input string to **k-bit** vector (bloom filter)
![[Pasted image 20221021201658.png]]

---

**Permanent randomized response**: from $B$ to $B'$ permanent randomized response is created with (user tunable) probability parameter $f$

$B'$ is memorized and will be used for all future reports

![[Pasted image 20221021201926.png]]

---

**Instantaneous randomized response**: send a report to the server of size $k$ bit generated from $B'$
- Flip bit value $1$ with probability $1-q$
- Flip bit value $0$ with probability $p$

![[Pasted image 20221021202213.png]]

---

### Apple at work

Apple collects data from iOS and OS X users:
- Popular emojis
- 'New' words
- Which websites to mute or auto-play on
![[Pasted image 20221021202354.png]]

## What is the privacy budget $\epsilon$?
![[Pasted image 20221021202433.png]]

## Problems with differential privacy

Sensitivity of computations

- **Count, histogram** computations: differential privacy works well
- **Sum** computation: the application of differential privacy can be a problem: what is the total income earned by men vs women? A single very high income $\rightarrow$ **lot of noise for this worst-case individual**
- How to **set** $\epsilon$? What happens when the **privacy budget** has been **exhausted**?