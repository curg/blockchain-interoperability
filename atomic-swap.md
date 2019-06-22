# Atomic Swap
Atomic Swap이란? 
(구) - 서로 다른 블록체인 기반 암호화폐의 투명하고 신뢰할 수 있는 교환 방식 
- 서로 다른 블록체인 기반의 암호화폐를 소유한 사람이 서로 신뢰를 확보할 필요 없이 안전하게 자산을 교환할 수 있도록 하는 기술
## 왜?
(구) - 서로 다른 블록체인 간의 신뢰할 수 있는 통신 방법이 필요. 
(구) - 등장배경 : 2013년 비트코인 포럼에서 Tier Nolan에 의해 처음으로 제안됨. 
- 중앙화된 거래소의 높은 수수료.
- 중앙화된 거래소를 포함한 모든 형태의 중개자를 신뢰할 수 없음.
- 2013년 비트코인 포럼에서 Tier Nolan이 아이디어를 제안.
## 어떻게? (기술)
핵심 기술 두 가지 
1. Hash Time Lock Contract(HTLC)
- 
2. multisig
알고리즘 
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

### 3. SC-to-SC
Ethereum-Stellar 

### 언제?
TBA

### 누가?
TBA

## 문제점
프로젝트별?

### 문제점에 대한 개선
TBA
