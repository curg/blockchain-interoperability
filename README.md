# [working title] A blockchain interoperability over time

## 논의사항
"over time"이 적절한가? 시간에 따라 정리하는 것인가?
  * 연도가 나오지는 않지만 기술제안->문제점제시->개선의 시간흐름에 따라 정리하기는 함.
  
## 키워드
블록체인 상호운용성, 평가(측정), 분류 등.

# Atomic Swap

## 왜?
TBA

## 어떻게? (기술)
TBA

## 분류
TBA
### ex) multi-sig를 쓰는~
### ex) ~~~

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

# Peg

Peg, Bridge, Relay 등 자주 등장하고 혼용되는 용어 정리

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
