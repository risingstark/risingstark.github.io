---
layout: post
title: Database - 4. Transaction
date: 2020-10-05 00:00:00 +0300
description:  # Add post description (optional)
img:  Knowledge/Database/2020-10-05-transaction/Database-Main.jpg
fig-caption: # Add figcaption (optional)
category: [Knowledge,Database]
tags: [Database,Transaction]
---

### 1. 들어가며
트렌섹션은 기본적으로 하나의 거래 혹은 처리 등으로 은행에서 사용하는 용어이다. 예를 들어 친구에게 만원이라는 금액을 계좌이체를 해야할 경우 나의 은행잔고에서만 돈이 나가고 친구 통장에는 돈이 들어가지 않는다면, 여러분들은 어떻게 할 생각인가? 이런 상황이 일어나는 경우는 극히 드물다. 그 이유는 하나의 트랜젝션의 특징과 연관이 되는데, 데이터 베이스상에서의 트렌젝션도 이와 일맥상통하는 부분이 많다. 이 글을 통해 데이터베이스에서의 트랜젝션의 의미와 특징, 예시, 기타등등에 대해 알아보자.

<br>

### 2. Database Transaction 정의
: **<ins>데이터베이스 트랜잭션(Transaction)은 데이터베이스의 상태를 변환시키는 하나의 논리적 기능을 수행하기 위한 작업의 단위</ins>** 또는 한꺼번에 모두 수행되어야 할 일련의 연산들을 의미한다.

<br>

### 3. Database Transaction 성질(ACID)

#### 3.1 원자성(Atomicity)
- 트랜잭션의 작업이 부분적으로 실행되거나 중단되지 않는 것을 보장하는 것이다.
- 즉, All or Noting의 개념으로서 작업 단위를 일부분만 실행하지 않는다는 것을 의미한다.

#### 3.2 일관성(Consistency)
- 트랜잭션이 성공적으로 완료되면 일관적인 DB상태를 유지하는 것이다.
- 여기서 말하는 일관성이란, 위의 송금 예제에서 금액의 데이터 타입이 정수형(integer)인데, 갑자기 문자열(string)이 되지 않는 것을 말한다. 즉, 송금 전후 모두 금액의 데이터 타입은 정수형이여야 한다는 것이 일관성이다.

#### 3.3 격리성(Isolation)
- 트랜잭션 수행시 다른 트랜잭션의 작업이 끼어들지 못하도록 보장하는 것이다.
- 즉, 트랜잭션끼리는 서로를 간섭할 수 없다.

#### 3.4 지속성(Durability)
- 성공적으로 수행된 트랜잭션은 영원히 반영이 되는 것이다.
- commit을 하면 현재 상태는 영원히 보장된다.

<br>

### 4. Database Transaction 상태
![Database-Transaction-Status-Example]({{site.baseurl}}/assets/img/Knowledge/Database/2020-10-05-transaction/Database-Transaction-Status-Example.png#center)

- **Active** : 트랜잭션이 실행 중에 있는 상태, 연산들이 정상적으로 실행 중인 상태
- **Failed** : 트랜잭션이 실행에 오류가 발생하여 중단된 상태
- **Aborted** : 트랜잭션이 비정상적으로 종료되어 Rollback 연산을 수행한 상태
- **Partially Committed** : 트랜잭션이 마지막 연산까지 실행했지만, Commit 연산이 실행되기 직전의 상태 
- **Committed** : 트랜잭션이 성공적으로 종료되어 Commit 연산을 실행한 후의 상태

<br>

### 5. Commit VS Rollback

#### 5.1 Commit
: **트랜잭션의 커밋(commit)이란 지금까지 트랜잭션 안에서 수행한 모든 SQL 문장들의 결과를 데이터베이스에 영구적으로 반영하면서 해당 트랜잭션을 종료하는 연산**이다. 트랜잭션의 커밋으로 다음과 같은 작업을 수행한다.

- 로그 파일에 **커밋 로그**를 기록한다.
- 트랜잭션의 수행으로 발생된 해제 가능한 자원들의 정보를 **가비지 콜렉터(Garbage Collector)**에게 넘겨준다.
- 트랜잭션의 상태를 **커밋 상태로 변경**시킨다.
- 트랜잭션 수행 중에 할당 받은 **자원들을 반환**한다. (잠금, 임시 메모리 등)

#### 5.2 Rollback
: 트랜잭션의 수행 도중에 치명적인 오류가 있어 더 이상 **진행할 수 없는 경우**에는 지금까지 수행해 왔던 모든 SQL 문장들을 다시 되돌려서, **데이터베이스를 트랜잭션 수행 이전상태로 변경**시켜야 한다. 이를 트랜잭션의 롤백이라고 하는데, 트랜잭션의 롤백은 트랜잭션 수행 중에 기록한 각 로그들에 대한 보상(compensation) 연산을 수행함으로써 구현된다. 

<br>

### 6. 마치며
Transaction에 대해 아주 간단히 알아보았다. ACID 특성은 데이터베이트 관련 면접기술에도 자주 등장하는 질문이기때문에 숙지를 잘하고 공부하자! 

<br>

### reference
[\[Image-of-Database-Main/blogs-oracle/database\]](https://blogs.oracle.com/database/autonomous-database-what-does-it-mean) <br>
[\[Image-of-Database-Transaction-Status-Example/tistory/limkydev\]](https://limkydev.tistory.com/100) <br>
[\[Definition-of-Transaction-General/wiki\]](https://ko.wikipedia.org/wiki/%EB%8D%B0%EC%9D%B4%ED%84%B0%EB%B2%A0%EC%9D%B4%EC%8A%A4_%ED%8A%B8%EB%9E%9C%EC%9E%AD%EC%85%98) <br>
[\[Definition-of-Transaction-Properties/tistory/coding-factory\]](https://coding-factory.tistory.com/226#:~:text=%ED%8A%B8%EB%9E%9C%EC%9E%AD%EC%85%98(Transaction)%EC%9D%80%20%EB%8D%B0%EC%9D%B4%ED%84%B0%EB%B2%A0%EC%9D%B4%EC%8A%A4%EC%9D%98,%EC%9D%98%20%EC%97%B0%EC%82%B0%EB%93%A4%EC%9D%84%20%EC%9D%98%EB%AF%B8%ED%95%9C%EB%8B%A4.&text=1.%20%ED%8A%B8%EB%9E%9C%EC%9E%AD%EC%85%98%EC%9D%80%20%EB%8D%B0%EC%9D%B4%ED%84%B0%EB%B2%A0%EC%9D%B4%EC%8A%A4%20%EC%8B%9C%EC%8A%A4%ED%85%9C,%EC%9E%91%EC%97%85%EC%9D%98%20%EB%85%BC%EB%A6%AC%EC%A0%81%20%EB%8B%A8%EC%9C%84%EC%9D%B4%EB%8B%A4.) <br>
[\[Definition-of-Transaction-Status/tistory/coding-factory\]](https://coding-factory.tistory.com/226#:~:text=%ED%8A%B8%EB%9E%9C%EC%9E%AD%EC%85%98(Transaction)%EC%9D%80%20%EB%8D%B0%EC%9D%B4%ED%84%B0%EB%B2%A0%EC%9D%B4%EC%8A%A4%EC%9D%98,%EC%9D%98%20%EC%97%B0%EC%82%B0%EB%93%A4%EC%9D%84%20%EC%9D%98%EB%AF%B8%ED%95%9C%EB%8B%A4.&text=1.%20%ED%8A%B8%EB%9E%9C%EC%9E%AD%EC%85%98%EC%9D%80%20%EB%8D%B0%EC%9D%B4%ED%84%B0%EB%B2%A0%EC%9D%B4%EC%8A%A4%20%EC%8B%9C%EC%8A%A4%ED%85%9C,%EC%9E%91%EC%97%85%EC%9D%98%20%EB%85%BC%EB%A6%AC%EC%A0%81%20%EB%8B%A8%EC%9C%84%EC%9D%B4%EB%8B%A4.) <br>
[\[Definition-of-Commit-and-Rollback/tistory/pjh3749\]](https://pjh3749.tistory.com/225) <br>
