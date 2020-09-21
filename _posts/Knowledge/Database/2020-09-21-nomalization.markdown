---
layout: post
title: Database - 3. Normalization
date: 2020-09-21 00:00:00 +0300
description:  # Add post description (optional)
img:  Knowledge/Database/2020-09-21-normalization/Database-Main.jpg
fig-caption: # Add figcaption (optional)
category: [Knowledge,Database]
tags: [Database,Nomalization]
---

### 1. 들어가며
데이터베이스의 효율을 증가시키는것은 너무나도 중요하다. 쓸모없는 데이터를 줄이고, 정리를 잘 한다면 서버가 여러대 있을 이유가 없을뿐더러 개발자 입장에서 데이터를 가져오고 사용하는데 도움을 많이 준다. 이 글에서는 데이터의 효율적인 관리방법 중에 하나인 정규화에 대해 알아보자.

<br>

### 2. 데이터베이스 정규화(Database normalization) 정의
- <ins>**관계형 데이터베이스(RDBMS)의 설계에서 중복을 최소화하게 데이터를 구조화하는 프로세스를 정규화**</ins>라고 한다. 

- 이론적으로 설명하자면 함수적 종속성을 이용해 연관성 있는 속성들을 분류하고, 각 릴레이션들에서 이상현상이 생기지 않도록 하는 과정을 말한다. 이때 정규화 된 정도를 **정규형(Normal Form)**으로 표현하는데, 정규형에는 **1NF, 2NF, 3NF, BCNF, 4NF, 5NF, 6NF** 까지 있다. 비공식적 표현으로는 3NF 가 되었으면 정규화 되었다고 말한다. 3NF 테이블의 대부분이 삽입, 변경, 삭제 이상이 없으며, 3NF 테이블의 대부분이 BCNF, 4NF, 5NF이다.
    - **함수 종속성**: 관계 스키마 중에서 어느 속성군의 값이 정해지면 다른 속성군의 값이 정해지는 것. A, B가 각각 관계 R의 속성인 경우, 임의 시점에서 A의 어떤 값도 반드시 B의 하나의 값에 대응되지만, B의 하나의 값이 A의 복수의 값에 대응되는 경우에 B는 A에 함수 종속이라고 하며 A→B와 같이 표기한다. 예를 들어, "직원" 테이블이 "직원 ID" 속성과 "직원 생일" 속성을 가질 때, {직원 ID}->{직원 생일} 또는 {직원 생일}은 {직원 ID}에 함수 종속이다. 실제로는 {직원 생일}이 null 이거나 어떤 {직원 생일}에도 대응되지 않을 수 있으므로 맞지 않을 수도 있으나, 여기에서는 {직원 ID}는 정확히 하나의 {직원 생일}만 갖는다고 가정한다. -위키-

<br>

### 3. 데이터베이스 정규화(Database normalization) 목적

- **불필요한 데이터를 제거**, **데이터의 중복을 최소화** 하기 위해서
- **데이터베이스 구조 확장 시 재디자인을 최소화**
- 다양한 관점에서의 **query를 지원**하기 위해서
- **무결성 제약조건**의 시행을 간단하게 하기 위해서
- 각종 이상 현상(Anomaly)을 방지하기 위해서
- **테이블의 구성을 논리적이고 직관적**으로 하기 위해서

<br>

### 4. 데이터베이스 정규화(Database normalization) 과정

#### 4.1 제 1정규화(First Normal Form, 1NF)
- 테이블(Relation)이 제 1정규형을 만족했다는 것은 아래 세 가지 조건를 만족했다는 것을 의미한다.
1. 어떤 Relation에 속한 모든 **Domain이 원자값(atomic value)**만으로 되어 있다.
2. 모든 **attribute에 반복되는 그룹(repeating group)**이 나타나지 않는다.
3. **기본 키**를 사용하여 관련 데이터의 각 집합을 **고유하게 식별**할 수 있어야 한다.

    즉, **모든 컬럼 값이 1개씩만 있어야 한다**

![Database-Normalization-1NF-Example]({{site.baseurl}}/assets/img/Knowledge/Database/2020-09-21-normalization/Database-Normalization-1NF-Example.png#center)

<br>

#### 4.2 제 2정규화(Second Normal Form, 2NF)
- 제 2정규화를 수행 했을 경우 테이블의 **모든 컬럼이 완전 함수적 종속을 만족**한다. 
    - 함수적 종속은 간단하게 다시 설명하자면 **릴레이션에서 속성들의 부분 집합을 X, Y라 할 때 특정 튜플에서 X의 값이 Y의 값을 함수적으로 결정 한다면 Y가 X에 함수적으로 종속** 되었다한다.
        - **재귀 규칙** : **Y가 X의 부분 집합이면 X → Y** 이다.
        - **증가 규칙** : **X → Y 이면 WX → WY 이고 WX → Y** 이다.
        - **이행 규칙** : **X → Y 이고 Y → Z 이면 X → Z** 이다.
        - **유니온 규칙** : **X → Y 이고 X → Z 이면 X → YZ** 이다.
        - **분해 규칙** : **X → YZ 이면 X → Y와 X → Z** 이다.
        - **가이행 규칙** : 만일 **W → X 이고 XY → Z 이면 WY → Z** 이다.
    - 함수적 종속에서 X의 값이 여러 요소일 경우, 즉, **{X1, X2} -> Y일 경우, X1와 X2가 Y의 값을 결정할 때 이를 완전 함수적 종속 이라고 하고, X1, X2 중 하나만 Y의 값을 결정할 때 이를 부분 함수적 종속** 이라고 한다

![Database-Normalization-2NF-Example]({{site.baseurl}}/assets/img/Knowledge/Database/2020-09-21-normalization/Database-Normalization-2NF-Example.png#center)  

<br>

#### 4.3 제 3정규화(Third Normal Form, 3NF)
- 테이블(Relation)이 제 3정규형을 만족한다는 것은 아래 두 가지 조건을 만족하는 것을 의미한다.
1. **Relation이 제 2정규화 되었다**.(The relation is in second normal form)
2. **기본 키(primary key)가 아닌 속성(Attribute)들은 기본 키에만 의존**해야 한다.

![Database-Normalization-3NF-Example]({{site.baseurl}}/assets/img/Knowledge/Database/2020-09-21-normalization/Database-Normalization-3NF-Example.png#center)

<br>

### 5. 마치며
실제 데이터를 가지고 이론적으로 배운 정규화 과정을 시도해보길 바란다. 정규화만이 데이터베이스의 속도 혹은 효율을 높여주는것이 아니라, 때로는 비정규화를 하는것도 도움이 된다. 이것의 차이는 실제 데이터를 가지고 시도해보고 시간을 비교해가며 개발하길 바란다.

<br>

### reference
[\[Image-of-Database-Main/blogs-oracle/database\]](https://blogs.oracle.com/database/autonomous-database-what-does-it-mean) <br>
[\[Image-of-Database-Normalization-1NF-Example/velog-house1217\]](https://velog.io/@house1217/%EB%8D%B0%EC%9D%B4%ED%84%B0%EB%B2%A0%EC%9D%B4%EC%8A%A4-%EC%A0%95%EA%B7%9C%ED%99%94-5ik2uh15ow) <br>
[\[Image-of-Database-Normalization-2NF-Example/tistory-Victorydntmd\]](https://victorydntmd.tistory.com/132) <br>
[\[Image-of-Database-Normalization-3NF-Example/tistory-Victorydntmd\]](https://victorydntmd.tistory.com/132) <br>
[\[General-Definition-of-Database-Normalization/wiki\]](https://en.wikipedia.org/wiki/Database_normalization) <br>
[\[Database-Normalization-Rule-and-Form/studytonight\]](https://www.studytonight.com/dbms/database-normalization.php) <br>
[\[Database-Normalization-Purpose/wkdtjsgur100-blog\]](https://wkdtjsgur100.github.io/database-normalization/) <br>
