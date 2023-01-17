---
title:  "데이터베이스와 Transaction" 
excerpt: "Transaction의 특징에 대해 알아보자"

categories:
  - CS
tags:
  - [데이터베이스, Transaction]

toc: true
toc_sticky: true
 
date: 2023-01-17
last_modified_at: 2023-01-17
---



# Transaction

## Transaction의 정의

데이터베이스의 상태를 변화시키기 위해 수행하는 작업의 단위. 보통 DBMS에선 초당 트랜잭션이 몇개가 실행되었는지로 측정한다. **`MySQL의 입력하는 모든 명령어들은 각각 하나의 트랜잭션이라고 할 수 있다.`**

------

### Transaction의 특징 4가지 (ACID)



 **`원자성(Atomicity)`**

**트랜잭션이 데이터베이스에 모두 반영되던가, 아니면 전혀 반영되지 않아야 한다는 것이다.** 트랜잭션은 사람이 설계한 논리적인 작업 단위로서, 일처리는 트랜잭션의 작업이 부분적으로 실행되다가 중단되지 않고 작업단위 별로 이루어져야 사람이 다루는데 무리가 없다.

 **`일관성(Consistency)`**

트랜잭션의 작업 처리 결과가 항상 일관성이 있어야 한다는 것이다. 즉, **데이터 타입이 반환 후와 전이 항상 동일해야 한다. **

 **`독립성(Isolation)`**

**하나의 트랜잭션은 다른 트랜잭션에 끼어들 수 없고 마찬가지로 독립적임을 의미한다.** 각각의 트랜잭션은 서로 간섭이 불가하기 때문에 하나의 특정 트랜잭션이 완료될때까지, 다른 트랜잭션이 특정 트랜잭션의 결과를 참조할 수 없다.

[독립성의 문제와 Isolation Level](https://parxism.github.io/cs/Transaction-isolation)은 추후 언급하겠다.

 **`지속성(Dutability)`**

**지속성**은 트랜잭션이 성공적으로 완료되었을 경우, **결과는 영구적으로 반영되어야 한다는 점이다.** 보통 Commit이 완료되면 지속성은 자연스럽게 충족된다.



### Transaction 의 상태 5가지

 **`Active`**: 트랜잭션이 현재 실행 중인 상태
 **`Failed`**: 트랜잭션 실행 중 오류가 발생해서 중단된 상태
 **`Aborted`**: 트랜잭션이 비정상 종료되어 Rollback이 수행된 상태
 **`Partially Committed`**: 트랜잭션의 연산이 모두 실행되고 Commit되기 전 상태
 **`Commited`**: 트랜잭션 성공적 종료, Commit을 실행한 후의 상태



### Local & Global Transaction

#### Local Transaction (지역)

1PC, 같은 리소스 내에서 일어나는 독립적인 일들을 하나로 묶으면 로컬 트랜잭션

일처리가 빠르다, Commit이 end와 Prepare 모두를 포함하고 있다.

#### Global Transaction (전역)

여러 독립적인 Transaction 중 하나 이상이 다른 리소스에서 일어나는 경우다.

2PC이상에서 진행되므로 여러 리소스 사이에서 처리되기에 **`'분산 트랜잭션'(Distributed Transaction)**`**

또는 **`XA`** 로 표기하기도 한다. JAVA는 XA를 기초로 한 환경에서 트랜잭션을 하며 이를 **JTS** 라고 한다.

이에 대한 JAVA API를 **JTA** 라고 부른다

#### Local & Global Transation + a

로컬 트랜잭션은 최적화할 알고리즘은 없다. 글로벌 트랜잭션을 로컬 트랜잭션 레벨에서 최적화 하는 방법은 나중에 WAS와 JDBC에서 다루도록 하겠다.

------

###### 추가할 내용

**`Dirty Read`**

**`Non-Repeatble Read`**

**`Pahntom Read`**



**`Read Uncommited`**

**`Read Committed`**

**`Repeatable Read`**

**`Serializable`**

**`Snapshot`**

<center> -- End of Log--  </center>

