# October 21 - 2022

# Authentication and Access Control

## Security strategies

- **Prevention**: take measures that prevent your system from being damaged
- **Detection**: take measures that detect when, how, and by whom your system has been damaged
- **Reaction**: take measures so that you can recover your system from damages

## Security objectives

- **Confidentiality**: prevent unauthorized disclosure of information
- **Integrity**: prevent unauthorized modification of information
- **Availability**: guarantee that information are always available to authorized users

# Authentication

## Identification and authentication

Provide the system with the ability of identifying its users and confirming their identity
- **Identification** by the parties to be authenticated
- **Authentication** by the system doing the authentication

Users authentication necessary for
- access control
- security logging

## Cryptography

It transforms a cleartext into a non intelligible text and vice verse

It is based on the use of a key to encrypt and decrypt messages

Classification of encryption algorithms
- **Symmetric encryption**
	- the same (private) key is used for encryption and decryption
	- the key is secret and known to both sender and receiver
	![[Pasted image 20221021234446.png]]
	
- **Asymmetric encryption**
	- each subject possesses a pair of keys (public, private), one for encryption, the other for decryption
	- the **private** key is known only to the owner of the key pair
	- the **public** key is known to everybody
![[Pasted image 20221021234506.png]]

## Authentication

Establishes the identity of a party to another party, where a party can be a user or a machine

Often **mutual** authentication is needed

It can be considered the **primary** security service

Correctness of the access control relies on a correct authentication

Correctness of intrusion/violation control relies on correct authentication

### User to computer authentication

Can be based on:
- something the user **knows**
- something the user **has**
- something the user **is**
or a combination the above (**multi-factor authentication**)

### Password-based authentication

Based on pairs
- **username**: the user identifies herself
- **password**: the user gives the proof of her identity

It is the oldest and most widely used authentication method
$+$ simple
$+$ cheap
$+$ easily implementable
$-$ weakest

## Vulnerabilities of passwords

Often passwords can be
- **guessing**
- **snooping**
- **spoofing**
- **masquerading**

One of the primary causes of password vulnerability is due to the **users** that do not choose or manage them properly
![[Pasted image 20221021235456.png]]


