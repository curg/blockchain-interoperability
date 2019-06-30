# Peg

## Backgrounds

Blockchain interoperability actually comes from connecting two or more different chains and validating each other's information. There are various ways to prove it, but among that pegging is one of the most basic and widely used methodology for implementing blockchain-interoperabiltiy. 

### Peg

The definition of Peg, the word itself has been used even before blockchain, is 'A short pin or bolt, typically tapered at one end, that is used for securing something in place, hanging things on, or marking a position.'[1] Following after, the word 'pegged' is used as stable and mostly used in currencies. 

But in the blockchain, peg is used among the two or more different blockchains. 

There are several ways of pegging way but typically it can be differentiated by 2 ways : One-way peg, Two-way peg. And it's differentiated by the way chains got pegged. 

### One-way peg

### Two-way peg

### Relay



### Bridge



### Sidechain
사이드체인이란 부모 체인(parent chain)과 대비해 사용하는 용어다. 관심을 가지고 지켜보는 체인을 부모 체인 또는 그냥


## 왜?
TBA

## 어떻게? (기술)

### block header validation
* issue: memory hard (script) PoW validation의 문제
  * 평가
  * 방법
     * Truebit
     * BulletProof <- 추가 조사 필요
* issue: 다른 consensus는 어떻게 구현하나, 검증하나
  * 가령 경제학적인 구조에 기반을 둔 consensus
* privacy coin 류 검증은 어떻게 하는가?

## 분류

### 방향성으로 분류
* one-way-peg
* two-way-peg
  * smart contract를 이용
  * collateralized peg

### Relay를 기준으로 분류
* (가제) centralized-peg
* federate-peg (federated?)

Federate peg is more de-centralized than centralized-peg. Its process is mostly similar with those of multi-signature transaction. As you can see in the term itself, the federation exists in federate-peg. Federation is composed of several different entities and each of them has sort of private keys. They all together mutli-signatuer wallet , which deposit exists.

Federated Peg is a mechanism that uses functionaries to move assets between two chains.[4] 

* Hub

For COSMOS Hub is the genesis Zone of its ecosystem. Basically, Hub is connected with all the other zones. Imagine that zone A and B is trying to exchange sort of coins or information. The coin comes out from zone A and go to Hub. Then it goes to zone B. So everytime when two or more than two different zones are trying to interact they have to pass through the Hub. 
  
* multi-sig

For making a transaction, the sender and owner have to use their own keys. Sender has to use their private key to proof the ownership of coins that will be sent and Reciever has to use its public key that will be used as a address. Only the keys of sender and receiver will be used in the transaction. But when it comes Multi-signature transaction some sort of parts will be changed. Most of part is still same, but the signature and ownership part. Ownership of coin or wallet is not belongs to single entity but more than one. And more than certain number of entities who have the ownership must sign to make transaction. M of N multisignature must be signed by at least M entities and the number of entities who have ownership is N. 

For example, 3 of 5 multisignature wallet needs at least 3 signs to finish the transaction. And the ownership of wallet belongs to 5 entities. At least 3 signatures are need every single time when transaction occurs. 
  
### 방법에 대한 분류
* add new opcode

* SPV proof

* 모든 blocks

* superblock

Superblock first and mostly mentioned at the paper named 'Using Superblocks to Bridge Dogecoin to Ethereum'. The basic concept of Superblock is almost same as that of Merkle hash from Merkle Tree and structure is also almost same with regular block. Superblock act its as the Root hash of several other blocks. 

Structure of Superblock that it is proposed will contain : 

- The root hash of a Merkle tree built from the block hashes.
- The blocks’ accumulated difficulty.
- The hash of the last block of the superblock.
- The timestamp of the last block of the superblock.
- The hash of the parent superblock data.

Superblock was proposed for being used as a Bridge that connects Dogecoin and Ethereum. 
  
## 주요 프로젝트
TBA

### 언제?
TBA

### 누가?
TBA

## 문제점
프로젝트별?

### 문제점에 대한 개선
TBA


[1] : https://www.lexico.com/en/definition/peg
[2] : 
[3] : Enabling Blockchain Innovations with Pegged Sidechains
[4] : Strong Federations: An Interoperable Blockchain Solution to Centralized Third-Party Risks




