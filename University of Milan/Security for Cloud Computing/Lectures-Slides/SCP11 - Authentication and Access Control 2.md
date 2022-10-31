# October 27 - 2022

# Authentication and Access Control

## Causes of password vulnerability

First step to limit vulnerability is a good password management

Vulnerabilities: do not change password, share them, weak passwords

## Authentication based on possession

**Tokens**:
- Each token has a cryptographic *key*
- Tokens are *safer* than passwords

### Vulnerabilities of tokens

It proves only the **identity of the token**, not of the user. It can be lost, stolen, etc.

Token-based authentication is **combined** with authentication based on knowledge: two factor authentication

## Authentication based on user characteristics

Biometric characteristics: physical or behavioral
Requires an initial enrollment phase that **defines a profile**

Authentication succeeds if the characteristics corresponds, provided a **tolerance interval**

# Access Control

Evaluates access requests to the resources by the authenticated users and, based on some **access rules**, it determines whether they must be granted or denied

## Access control vs other services

Correctness rests on:
- **Proper user identification**: personal privileges
- **Correctness of the authorizations**: protected

## Access control and authentication

Necessary for **accountability**
No shared accounts
Credential-based access control

## Policies, models and mechanism

- **Policy**: defines *guidelines and rules* describing the accesses to be authorized
- **Model**: formally *defines the access control* specification and enforcement
- **Mechanism**: it *implements the policies* via low level functions

## Separation between policies and mechanism

Allow us to:
- Discuss access requirements **independent or their implementation**
- Compare different access control policies as well as **different mechanism that enforce the same policy**
- Enforce **multiple policies**

## Access control mechanism

Based on the definition of a **reference monitor**:
- tamper-proof
- non-bypassable
- security kernel
- small

It needs to cope with **storage channels** and **covert channels**

## Security policies

- **Access control policies**: define who can or cannot access the resources
	- Discretionary
	- Mandatory
	- Role-based
- **Administrative policies**: define who can specify authorizations/rules governing access control

### Discretionary (DAC) policies

Identity of the requestors and explicit access rules

User can be given the **ability of passing on their rights**

#### Access Matrix model

Provides a framework for describing protection systems
Abstract representation of protection system found in real systems 

**Protection state**: defined by triple SOA, where
- **S**: set of subjects
- **O**: set of objects
- **A**: access matrix

#### Example
![[Pasted image 20221031200947.png]]

#### Implementation

Generally large and sparse, so storing it is a waste of memory space
Alternatives: authorization table, access control lists and capability lists
![[Pasted image 20221031201136.png]]
![[Pasted image 20221031201148.png]]

#### ACL vs Capabilities

ACL require authentication of subjects, provide superior for access control and revocation on a **per-object basis**; most systems based on it

Capabilities do not require authentication of subjects but require *unforgeability*, provides superior for access control and revocation on a **per-subject basis**

#### DAC weaknesses

Constraint only **direct** access
No control on what happens to information once released: vulnerable to trojan horses
![[Pasted image 20221031202518.png]]

### Mandatory (MAC) policies

**Mandatory access control**: impose restrictions on information flow which cannot be bypasses by trojan horses

Makes a distinction **users** and **subjects**
- User: human being
- Subject: process in the system

While users may be trusted not to behave improperly, the programs they execute are not

The most common form is **multilevel**:
- Based on classification of subjects and objects
- Two classes of policies:
	- *Secrecy-based*
	- *Integrity based*

#### Security classification

Usually formed by two components:
- **Security level** element of a hierarchical set of elements
- **Categories** set of a non-hierarchical set of elements
The combination of the two introduces a partial order on security classes, called **dominates**

#### Classification lattice
![[Pasted image 20221031212519.png]]

#### Example
![[Pasted image 20221031212609.png]]

