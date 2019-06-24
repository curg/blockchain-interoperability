# Atomic Swap
Atomic Swap이란?
- 서로 다른 블록체인 간 안전한 무신뢰(trustless) 자산 교환 방법
- 2013년 비트코인 포럼에서 아이디어 제안됨 (Tier Nolan)
## 왜?
- 중앙화된 거래소의 높은 수수료
- 서로 다른 블록체인 간 신뢰할 수 있는 통신 방법 필요
- 중앙화된 거래소를 포함한 모든 형태의 중개자를 신뢰할 수 없음
## 어떻게?
#### 핵심 기술
1. Hash Time Lock Contract(HTLC) - Hashlock + Timelock
- Hashlock - 두 거래 당사자는 H(x)를 만족하는 x로 상대방이 작성한 거래의 output을 소비할 수 있음
```
Ex. sig x OP_HASH160 H(x) OP_EQUAL pubKey OP_CHECKSIG
```
- Timelock - 두 거래 당사자 중 x를 제시하는 쪽이 상대방이 작성한 거래의 output을 소비함과 동시에 자신이 작성한 거래를 refund하는 것을 방지
```
Ex. sig pubKey t OP_CHECKLOCKTIMEVERIFY OP_DROP OP_DUP OP_HASH160 pubKeyHash OP_EQUALVERIFY OP_CHECKSIG
```
2. Multisignature
```
Ex. sigA sigB 2 pubKeyA pubKeyB 2 OP_CHECKMULTISIG
```
#### 알고리즘 (by Tier Nolan)
``` A picks a random number x
 
 A creates TX1: "Pay w BTC to <B's public key> if (x for H(x) known and signed by B) or (signed by A & B)"
 
 A creates TX2: "Pay w BTC from TX1 to <A's public key>, locked 48 hours in the future, signed by A"
 
 A sends TX2 to B
 
 B signs TX2 and returns to A
 
 1) A submits TX1 to the network
 
 B creates TX3: "Pay v alt-coins to <A-public-key> if (x for H(x) known and signed by A) or (signed by A & B)"
 
 B creates TX4: "Pay v alt-coins from TX3 to <B's public key>, locked 24 hours in the future, signed by B"
 
 B sends TX4 to A
 
 A signs TX4 and sends back to B
 
 2) B submits TX3 to the network
 
 3) A spends TX3, revealing x
 
 4) B spends TX1 using x
 
 This is atomic (with timeout).  If the process is halted, it can be reversed no matter when it is stopped.
 
 Before 1: Nothing public has been broadcast, so nothing happens
 Between 1 & 2: A can use refund transaction after 72 hours to get his money back
 Between 2 & 3: B can get refund after 24 hours.  A has 24 more hours to get his refund
 After 3: Transaction is completed by 2
 - A must spend his new coin within 24 hours or B can claim the refund and keep his coins
 - B must spend his new coin within 72 hours or A can claim the refund and keep his coins
 
 For safety, both should complete the process with lots of time until the deadlines.
```
## 분류

### 1. Script-to-Script

### 2. Script-to-Smart Contract(SC) / SC-to-Script

### 3. SC-to-SC


## 주요 프로젝트
### 1. Script-to-Script
Bitcoin-Litecoin
### 2. Script-to-Smart Contract(SC) / SC-to-Script
Bitcoin-Ethereum
### 3. SC-to-SC
Ethereum-Stellar 

## 문제점
- (Tier Nolan의 알고리즘에서) A가 Tx1과 Tx2를 작성하였으나 B가 Tx3과 Tx4를 작성하지 않을 경우 A의 자산만 묶이는 결과로 이어짐
- 자산 간 교환 비율을 어떻게 결정하면 좋은가에 대한 과제가 남음

### 문제점에 대한 개선 사항
TBA
