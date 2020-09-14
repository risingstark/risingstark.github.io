---
layout: post
title: Database - 2. RDBMS VS NoSQL
date: 2020-09-14 00:00:00 +0300
description:  # Add post description (optional)
img:  Knowledge/Database/2020-09-14-rdbms-nosql/Database-Main.jpg
fig-caption: # Add figcaption (optional)
category: [Knowledge,Database]
tags: [Database,RDBMS, NoSQL]
---

### 1. 들어가며
흔히 데이터베이스를 공부하는 개발자라면 RDBMS(관계형)와 NoSQL(비관계형)의 차이점에 대해 정확히 알고 있어야한다. 서로의 개념과 사용처에대해 잘 이해하고 있다면, 개발하는데에 있어 큰 도움을 줄것이다. 이 글에서는 RDBMS와 NoSQL의 정의, 구조, 작동방식, 차이점 및 어디에 사용되어 지는지 등에대해 알아보자.

<br>

### 2. RDBMS & NoSQL 정의
- ***RDBMS***
: **관계형 데이터베이스 모델(relational database)을 기반으로 하는 데이터베이스 관리 시스템**이다. 여기서 관계형 데이터베이스(relational database)는 상호 관련된 데이터 포인트에 대한 액세스를 저장하고 제공하는 데이터베이스의 한 형태이다. 데이터를 테이블에 직관적으로 간단하게 나타내는 관계형 모델을 기반으로, 테이블의 각 열은 키(key)라고 하는 고유 ID를 가진 레코드이다. 테이블의 컬럼(column)은 해당 데이터의 속성을 가지며, 각 레코드는 각 속성에 대한 값을 가지므로 데이터 포인트 간 관계를 손쉽게 구축할 수 있습니다.
- ***NoSQL***
: 기존의 관계형 데이터베이스의 한계를 뛰어넘기 위해 만들어진 새로운 형태의 **비관계형 데이터베이스**로, Not Only SQL(SQL 뿐만이 아닌. 이라는 뜻)의 줄임말이다. 관계형 데이터베이스보다 더 **융통성 있는 데이터 모델을 사용**하며, **데이터의 저장 및 검색에 특화된 메커니즘을 제공**한다. **NoSQL은 분산 환경에서의 데이터 처리를 더욱 빠르게 하기 위해 개발**되었다.

<br>

### 3. RDBMS & NoSQL 비교

기능         |***RDBMS***                          |***NoSQL***
**데이터모델**     |관계형 모델은 데이터를 **행과 열로 구성된 테이블**로 정규화합니다. **스키마는 테이블, 행, 열, 인덱스, 테이블 간 관계, 기타 데이터베이스 요소를 정확하게 규정**합니다. 데이터베이스는 테이블 사이의 관계에서 참조 무결성을 실현합니다.|**NoSQL 데이터베이스는 키-값, 문서, 그래프 등 성능과 규모 확장에 최적화된 다양한 데이터 모델**을 제공합니다.
**ACID 속성**    |관계형 데이터베이스는 원자가, 일관성, 격리성 및 지속성(**ACID, atomicity, consistency, isolation, and durability**)의 속성을 제공합니다.|NoSQL 데이터베이스는 흔히 **수평으로 확장할 수 있는 보다 유연한 데이터 모델**을 위해 관계형 데이터베이스의 일부 ACID 속성을 완화함으로써 조정합니다. 이로써 NoSQL 데이터베이스는 단일 인스턴스의 한계를 넘어 **수평으로 확장해야 하는 사용 사례에서 높은 처리량, 낮은 지연 시간을 위한 탁월한 선택**이 됩니다.
**성능**        |성능은 일반적으로 디스크 하위 시스템에 따라 다릅니다. 최고 성능을 달성하기 위해서는 **쿼리, 인덱스 및 테이블 구조를 자주 최적화**해야 합니다.|성능은 일반적으로 **기본 하드웨어 클러스터 크기, 네트워크 지연 시간 및 호출 애플리케이션의 기능**입니다.
**확장**         |관계형 데이터베이스는 일반적으로 **하드웨어의 계산 성능을 높이거나 읽기 전용 워크로드의 복제물을 추가함으로써 확장**됩니다.|NoSQL 데이터베이스는 일반적으로 거의 **무제한적인 범위에서 일관된 성능을 제공하는 처리량 제고를 위해 분산형 아키텍처를 사용**해 액세스 패턴이 확장 가능하기 때문에 분할성이 있습니다.
**API**         |데이터를 저장 및 검색하기 위한 요청은 **SQL(구조화 질의 언어)을 준수하는 쿼리를 사용하여 전달**됩니다. 쿼리는 관계형 데이터베이스에 의해 구문 분석되고 실행됩니다.|객체 기반 API를 통해 앱 개발자가 데이터 구조를 쉽게 저장 및 검색할 수 있습니다. 파티션 키를 사용하면 앱에서 **키-값 페어, 열 세트 또는 일련의 앱 객체 및 속성을 포함하는 반정형 문서를 검색**할 수 있습니다.

<br>

### 4. RDBMS & NoSQL 장단점
- ***RDBMS***
    - **장점** 
        1. 다양한 용도로 사용이 가능하고, 일반적으로 높은 성능을 가지고 있다.
        2. DATA의 일관성을 보증한다.
        3. **정규화에 따른 갱신 비용을 최소화 할 수 있다.**
        4. SQL(Structured Query Language) 지원한다.
    - **단점**
        1. 상대적으로 덜 유연하며, 데이터 **스키마는 미리 알고 계획**해야한다. 즉, 기존에 작성된 스키마를 수정하기가 어렵다.
        2. **JOIN문이 많은 매우 복잡한 쿼리**가 만들어 질 수 있다.
        3. **수평 확장이 어렵고, 보통 수직 확장**만 가능하다. 즉 어느 시점에서 처리량/처리 능력과 관련하여 약간의 성장 한계에 직면하게 될 수 있다.
        4. **빅데이터를 처리하는데 매우 비효율적**이다.

- ***NoSQL***
    - **장점** 
        1. **대용량 데이터 처리를 하는데 효율적**이다.
        2. **읽기 작업보다 쓰기 작업이 더 빠르고 관계형 데이터베이스에 비해 쓰기와 읽기 성능이 빠르다**
        3. 데이터 모델링이 유연하다.
        4. **뛰어난 확장성**으로 검색에 유리하다.
        5. 최적화된 **키 값 저장 기법을 사용하여 응답속도나 처리효율 등에서 성능**이 뛰어나다.
        6. 복잡한 데이터 구조를 표현할 수 있다.
    - **단점**
        1. 쿼리 처리시 데이터를 파싱 후 연산을 해야해서 큰 크기의 document를 다룰 때는 성능이 저하된다.
        

<br>

### 4. RDBMS 와 NoSQL의 사용 
- RDBMS 사용이 적합한 경우
    - **데이터의 업데이트가 자주 일어날때**(RDB는 특정한 데이터의 테이블에 위치한것만 업데이트하면 되지만, NoSQL일경우 여러 컬렉션을 수정해야 한다)
    - **명확한 스키마가 중요할때** 혹은 **데이터구조가 극적으로 변경되지 않을 때** 사용이 용이하다.

- NoSQL 사용이 적합한 경우
    - 정확한 데이터 요구사항을 알 수 없거나 **관계를 맺고 있는 데이터가 자주 변경(수정)되는 경우**. 
    - **읽기(read)처리를 자주하지만, 데이터를 자주 변경하지 않는 경우** (즉, 한번의 변경으로 수십 개의 문서를 수정 할 필요가 없는 경우)
    - **데이터베이스를 수평으로 확장**해야 하는 경우( 즉, 막대한 양의 데이터를 다뤄야 하는 경우, 읽기/쓰기 처리량이 큰 경우)


<br>

### 5. RDBMS 와 NoSQL 종류
- **RDBMS**
    - **Amazon Aurora, Oracle, MS-SQL server, MySQL, PostgreSQL,MariaDB**
- **NoSQL**
    1. **Document Store, Document Database** : 테이블이 스키마가 유동적이다. 즉 레코드마다 각각 다른 스키마를 가질 수 있습니다. XML, JSON과 같은 Document를 이용해 레코드를 저장합니다. 트리형 구조로 레코드를 저장하거나 검색하는데 좋은 Database입니다.
        - **MongoDB, Azure Cosmos DB, CouchDB, MarkLogic, OrientDB**
    2. **Wide Column Store, Wide Column Database** : 행마다 키와 해당값을 저장할 때마다 각각 다른값의 다른 수의 스키마를 가질 수 있습니다. 사용자 이름(Key)에 해당하는 값에 스키마들이 각각 다르다는 것을 알 수 있고. 이러한 구조를 갖는 Wide Column Database는 대량의 데이터의 압축, 분산처리, 집계 처리(sum, count, avg 등) 및 쿼리 동작 속도 그리고 확장성이 뛰어난 것이 그 대표적인 특징입니다.
        - **Cassandra, HBase, Google BigTable, Vertica, Druid, Accumulo, HyperTable**
    3. **Key Value Store, Key Balue Database** : 기본적인 패턴으로 Key,value가 하나의 묶음으로 저장되는 구조로 단순한 구조이기에 속도가 빠르며 분산 저장 시 용이하다. Key 안에 (Column, Value) 형태로 된 여러개의 필드를 갖습니다.. 주로 Serverconfig, Session Clustering등에 사용되고 엑세스 속도는 빠르지만, Scan에는 용이하지 않습니다.
        - **Redis, Oracle NoSQL Database, Voldmorte, Oracle Berkeley DB, Memcached, Hazelcast**
    4. **Graph Database** : 데이터를 노드로 표현하며, 노드 사이의 관계를 엣지로 표현, ,RDBMS 보다 Performance가 좋고 유연하며 유지보수에 용이한것이 특징. Social networks, Network diagrams 등에 사용할 수 있다고 합니다
        - **Neo4j, Blazegraph, OrientDB , AgensGraph(국내솔루션)**

<br>

### 6. 마치며
이 글은 단순 RDBMS VS NoSQL에 대한 차이점등을 알아보는 글이다. RDBMS와 NoSQL의 자세한 점들은 차후에 따로 다룰 예정이니 follow up을 통해 차근 차근 알아가자.

<br>

### 7. reference
[\[Definition-of-RDBMS-NoSQL/academind\]](https://academind.com/learn/web-dev/sql-vs-nosql/) <br>
[\[Pros-and-Cons-of-RDBMS-NoSQL/tistory/newehblog\]](https://newehblog.tistory.com/38?category=834445) <br>
[\[Definition-and-Types-of-NoSQL/tistory/bestpractice80\]](https://bestpractice80.tistory.com/66) <br>
[\[Definition-and-Types-of-RDBMS/mongodb\]](https://www.mongodb.com/nosql-explained/nosql-vs-sql) <br>
[\[Difference-between-RDBMS-NoSQL/guru99\]](https://www.guru99.com/sql-vs-nosql.html) <br>