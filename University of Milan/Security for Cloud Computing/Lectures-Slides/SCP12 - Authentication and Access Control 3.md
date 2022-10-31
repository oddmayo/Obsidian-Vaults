# Access Control

---

Continuation of previous lesson

---

#### Semantics of security classifications

Each user is assigned a security class: **clearance**
A user can connect to the system at any class dominated by his clearance

**Secrecy classes**:
- assigned to *users* reflect user's trustworthiness not to disclose sensitive information to individuals who do not hold appropriate clearance
- assigned to *subjects* reflect the sensitivity of information contained
**Categories** define the area of competence of users and data

#### Bell La Padula

Defines mandator policy for secrecy
**Goal**: prevent information flow to lower or incomparable security classes

#### Information flow for secrecy
![[Pasted image 20221031213603.png]]

#### Exceptions to axioms

Real-world requirements may need mandatory restrictions to be bypassed
- **Data association**: a set of values seen together is to be classified higher than the value singularly taken
- **Aggregation**: may have higher classification than its individual items
- **Sanitization and downgrading**: data may need to be downgraded after some time

#### Coexistence of DAC and MAC
They are not mutually exclusive
DAC provides directionality within the **boundaries** of MAC

#### Limitation of mandatory policies

Only **overt** channels of information
Remain vulnerable to **covert** channels (leak information)

Every resource or observable of the system shared by processes of different levels can be exploited to create a covert channel

#### Covert channel analysis

Usually done in the **implementation** phase
**Interface models** attempt to rule out such channels in the modeling phase
- **Non interference**: the activity of high level processes must not have any effect on processes at lower levels

#### Integrity mandatory policy

Mandatory policies do not safeguard integrity $\rightarrow$ information can be tampered
**Integrity classes**
- assigned to *users'* trustworthiness
- assigned to *objects* reflect degree of trust
**Categories** define the area of competence of users and data

#### Biba model for integrity
**Goal**: prevent information flow to higher or incomparable security classes
**Limitations**: restrictions may result too restrictive

#### Integrity

Ensuring that no resource has been modified in an **unauthorized or improper** way and that data stored in the system correctly reflect the real world they are intended to represent

Data management system functionalities: **concurrency** and **recovery** techniques


### Role-based (RBAC) policies

**Role** named set of privileges
- **Roles** $\rightarrow$ access objects
- **Users** $\rightarrow$ activate roles
![[Pasted image 20221031215155.png]]

Role hierarchy defines **specialization** relationships
![[Pasted image 20221031215222.png]]

Hierarchical relationship $\rightarrow$ authorization propagation

#### Advantages
- Easy management
- Role hierarchy
- Restrictions
- Least privilege
- Separation of duty

#### Role based models
- Relationships beyond hierarchical
- Enriched **administrative policies**
- Relationships with user **identifiers**
- Additional **constraints**

#### Roles in SQL

*Privileges* can be grouped in **roles** that can be assigned to users or to other roles (nested)
![[Pasted image 20221031215842.png]]
Roles can be granted to users with grant option


## Administrative policies

Define who can grant and revoke authorizations
- **Centralized**: a privileges authority is in charge of auth specification
- **Ownership**: the creator of an object is its owner and as such can administer access authorization on the object
Authority to specify authorizations can be **delegated**

### Separation of duty

No user should have enough privileges to be able to abuse the system
- **static** who specifies the authorizations must make sure not to give *too much privileges* to a single user
- **dynamic** the control on limiting privileges is enforces at runtime: a user cannot use *too many* privileges

## Expanding authorizations (DAC)

Traditionally supported:
- **User groups**: users collected in groups and authorizations specified for groups
- **Conditional**: validity of authorizations dependent on satisfaction of some conditions
Relatively easy to implement un simple systems

Specifications for single entities too heavy: support **abstractions** (grouping them). Usually hierarchical relationships

### Hierarchical data systems

Can be applied to all dimensions of authorizations
![[Pasted image 20221031221620.png]]

---

Usefulness of abstractions limited if **exceptions** are not possible: support **negative** authorizations

Presence of permissions and denials can bring **inconsistencies**

### Permissions and denials

Easy way to support exceptions via negative authorizations
- **open policy**: whatever is not explicitly denied can be executed
- **closed policy**: only accesses explicitly authorized can be executed
Hybrid policies can generate inconsistency and incompleteness

Possible conflict resolution policies
- **denials-take-precedence** negative authorizations wins
- **most-specific-takes-precedence** the authorization is more specific wins
- **most-specific-along-a-path-takes-precedence** the authorization that is more specific wins only on the paths passing through it