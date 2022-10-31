# October 25 - 2022

## Data Security

Taking into account:
- the **state of the art**
- **costs of implementation**
- **nature**
- **scope**
- **context**
- **purposes**

The controller and processor shall implement **appropriate technical and organizational measures** to ensure a level of security appropriate to the risk.

## 'Appropriate' technical and organizational measures

They rely on Data Controller *accountability*:

Pseudonymization and encryption, ensure confidentiality, restore availability and regularly testing the effectiveness of measures for ensuring the security of the processing

### Measure that allows the quality of personal data to be lost

**Anonymization** techniques applied on personal data, but **could be invalidated** by technology and cause non-personal data to regain the status of personal data

There is no such thing as *absolute* anonymity, but it is a relative quality of the data

### Pseudonymization

The personal data can no longer be attributed to a specific data subject

## Distinguishing

The GDPR's definition differs profoundly from how the term has been used in other contexts

**Definition**: pseudonymization consists in replacing an attribute, usually **unique**, of a data with another, equally unique and usually not intelligible
![[Pasted image 20221031144200.png]]


## Risks

The less data that is pseudonymized or the smaller the degrees of separation, the easier it will be to overcome the security measure (susceptible to record linkage attack)

## Lessons learned

It is possible to reidentify persons from film preferences

It is not efficient in the case of data from geolocation

## Pseudonymization techniques

- Hash encryption
- Linking the unique identifier to a hash
- Linking the pseudo-identifier to the hash
- The addition of *noise* in the data

## ENISA and pseudonymization

![[Pasted image 20221031144839.png]]

Choose a technique or method depends on several factors, primarily the level of data protection and the functionality of the pseudonymized data

In terms of protection, RNG, Message Authentication Code, and encryption are more effective

## Restoration

Since the use of additional information is critical to pseudonymization, the entity must implement a recovery mechanism

This may occur when the entity detects an **anomaly** (data breach) in its system and need to contact the appropriate entity

## Pseudonymization secret protection

The entity must always protect the pseudonymization secret by appropriate technical and organizational measures

## Further reading
![[Pasted image 20221031145523.png]]

## Pseudonymization vs anonymization

*Pseudonymization has a diametrically opposed result with respect to anonymization*, because while **pseudonymization does not change the biunivocal association between data and person**, with the adoption of anonymization techniques the referability of data to the person becomes as likely as a random attribution.

**Pseudonymous data retains the nature of personal data** while anonymous data falls outside the scope of the GDPR

### Panta rei

The principles of data protection should therefore not apply to anonymous information, namely information which does not relate to an identified or identifiable natural person

## Progressive anonymity

Pseudonymization aa a step in a larger anonymization process. Will always be the basis on which data will be made more and more anonymous.