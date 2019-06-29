# Peg

## Backgrounds

### Peg
본래 페그(peg) 또는 페그제(peg system)는 어느 나라의 통화 가치를 특정 국가의 통화에 고정시켜 정해진 환율로 교환하는 것 또는 그러한 고정환율제를 의미한다. 마찬가지로 어느 블록체인의 가치를 다른 블록체인으로 전달하는 것을 페그라 한다.

### Relay
릴레이는 타 블록체인의 **읽기(read)**와 **검증**을 수행하는 블록체인상에 구현된 시스템이다.[2]

### Bridge
브릿지는 서로 다른 두 블록체인간 상호작용을 수행한다. *브릿지가 릴레이를 포괄하는 개념.* paritytech에서는 이더리움 메인넷(mainnet) PoA 사이드체인을 연결하는 Parity Bridge를 개발했다. Parity Bridge는 두 이더리움 기반 블록체인간에 임의의 메시지를 전송할 수 있도록 한다.[4]

### Sidechain
Blockstream이 정의한 사이드체인은 "다른 블록체인의 데이터를 검증하는 블록체인"이다. 그러나 일반적으로 사이드체인은 pegged sidechain의 의미로 혼용된다. pegged sidechain은 다른 블록체인의 데이터를 읽어 체인간 교차(cross-chain) 자산 이식성을 용이하게 한다.[5]

위 용어들은 자주 혼용되지만, 본 글에서는 위와같이 정의해 엄밀히 구분한다.

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
  * Symmetric two-way peg

* smart contract를 이용
* collateralized peg

### Relay를 기준으로 분류
* (가제) centralized-peg
* federate-peg (federated?)
  * Hub
  * multi-sig
  
### 방법에 대한 분류
* add new opcode
* SPV proof
  * 모든 blocks
  * superblock
  
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


# References
[1] https://medium.com/blockchain-musings/pegged-sidechains-cafe1d8c7023   
[2] https://medium.com/cryptronics/blockchain-interoperability-moving-assets-across-chains-e5203357d949   
[3] https://wiki.polkadot.network/en/latest/polkadot/learn/bridges/   
[4] https://github.com/paritytech/parity-bridge   
[5] http://blockstream.com/sidechains.pdf   
