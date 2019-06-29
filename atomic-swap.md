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

--------------------------------
# Paper (raw)

블록체인 산업이 발전함에 따라 비트코인의 뒤를 이어 유의미한 규모의 시가총액과 생태계를 형성한 수많은 알트코인이 등장하였고, 이러한 암호화폐를 거래할 수 있는 중앙화된 거래소가 성행하게 되었다. 그러나 중앙화된 거래소는 항상 해킹, 횡령과 같은 위험에 노출되어 있었고, 사람들은 중앙화된 거래소를 거치는 일 없이 블록체인 상에서 안전하게 자산을 교환할 수 있는 방법을 고민하게 되었다.

애석하게도 각 블록체인 생태계는 서로 고립되어있다. 이를테면 비트코인 메인넷 상의 어떤 주소로 비트코인을 보내는 것은 가능하지만 라이트코인을 보내는 것은 불가능하다. 여기서 서로 다른 분산원장을 사용하는 두 암호화폐를 교환할 수 있는 새로운 방법의 필요성이 제기된다. 어떻게 하면 비트코인과 라이트코인을 신뢰 가능한 제3자를 배제한 상태에서 안전하게 교환할 수 있을까?
<br></br>

아토믹 스왑에서 ‘아토믹’하다는 것은, 거래 당사자의 자산 ‘스왑’이 모두 진행되거나 모두 진행되지 않음을 의미한다. 지금부터 비트코인을 보유한 A와 라이트코인을 보유한 B가 어떻게 각자의 자산을 ‘아토믹’하게 맞바꾸게 되는지 살펴보자. A의 비트코인 주소로 B의 라이트코인을 전송할 수 없고, 그 반대의 경우도 마찬가지이기 때문에, A는 라이트코인을, B는 비트코인을 수취할 주소(즉, 공개키)를 사전에 생성해 두어야 한다.

교환 성사를 위해 필요한 것은 A가 B에게 비트코인을 보내는 트랜잭션과 B가 A에게 라이트코인을 보내는 트랜잭션이 생성되어 네트워크에 전파되는 것이다. 그런데 A와 B가 서로를 신뢰하지 않는 상태에서는, 가령 A가 작성한 트랜잭션을 전파하여도 B가 자신의 트랜잭션을 정직하게 전파할 것이라는 보장이 없기 때문에 서로가 자신이 먼저 트랜잭션을 전파하는 것을 꺼리게 된다.

이에 대한 해결책으로 A와 B가 각자 생성하는 트랜잭션의 출력(output)을 소비(spend)하기 위해 어떤 해시값 H(x)를 만족하는 x가 필요하도록 조건을 붙일 수 있다, A와 B 중 한 사람이 임의로 x를 선정한 뒤에 트랜잭션을 작성하고 네트워크에 전파하면, 이 트랜잭션을 통해 H(x)가 무엇인지 알 수는 있지만 x를 알 길이 없기 때문에 x를 모르는 상대방이 트랜잭션의 출력을 소비하지 못하게 된다.
<br></br>

A가 임의의 값 x를 선정한 뒤, B에게 비트코인을 지불하는 트랜잭션 Tx1을 작성하였다고 가정하자. 이때 B가 Tx1을 소비하기 위해 필요한 것은 H(x)를 만족하는 x와 B의 서명이다. 그런데 Tx1이 네트워크에 전파된 상태에서 B가 침묵한다면 어떻게 될까?

이러한 상황에서 A가 Tx1에 담긴 비트코인을 돌려받기 위해 Tx1의 소비 조건에 ‘A의 서명과 B의 서명’이라는 분기를 추가하고, Tx1으로부터 A에게 비트코인을 반환하는 트랜잭션 Tx2를 작성하는 것이 필요해진다. A가 B로부터 라이트코인을 수령하는 즉시 비트코인을 반환하는 것을 방지하기 위해 Tx2는 충분한 시간 동안 실행되지 못하도록 잠겨 있어야 하며, A는 Tx1을 네트워크에 전파하기 이전에 B의 서명을 미리 받아 두어 이후 B가 침묵하여도 자신의 비트코인을 안전하게 반환할 수 있도록 해야 한다.
<br></br>

Tx1이 네트워크에 전파된 시점에서 H(x)가 공개되면 B는 Tx1이 전파되었음을 확인한 뒤 A에게 라이트코인을 지불하는 트랜잭션 Tx3를 작성할 수 있으며, 이때 A가 Tx3을 소비하기 위해 필요한 것은 A의 서명과 x이다. 또한 Tx1이 전파된 시점에 B가 침묵하는 것을 대비하는 것과 마찬가지로 Tx3이 전파된 시점에 A가 침묵하는 것을 대비하기 위해 Tx3의 소비 조건에 ‘B의 서명과 A의 서명’이라는 분기를 추가하고, Tx3으로부터 B에게 라이트코인을 반환하는 트랜잭션 Tx4를 작성하는 것이 필요하다. Tx2의 경우와 마찬가지로 Tx4는 충분한 시간 동안 실행되지 못하도록 잠겨 있어야 하며, B는 Tx3을 네트워크에 전파하기 이전에 A의 서명을 미리 받아 두어야 한다.

Tx4의 잠금 시간이 Tx2보다 길 경우 A가 Tx2의 잠금 해제 시간을 노려 Tx3을 소비함과 동시에 비트코인을 반환하는 것이 가능하므로 Tx4의 잠금 시간은 Tx2의 그것보다 짧아야 한다.

Tx3이 네트워크에 전파되고 A가 자신의 서명과 x를 사용하여 Tx3을 소비, 즉 B의 라이트코인을 수령하면 x값이 네트워크에 공개되고, B 또한 자신의 서명과 x를 사용하여 Tx1을 소비, 즉 A의 비트코인을 수령할 수 있게 된다.


