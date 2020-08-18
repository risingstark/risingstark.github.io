---
layout: post
title: Hash, Hash Map, Hash Table, Hash Function, Hash Brown?!
date: 2020-08-18 00:00:00 +0300
description:  # Add post description (optional)
img:  Knowledge/Data_Structure/2020-08-18-hash-table/Data-Structure-Hash-Table-Main.jpg
fig-caption: # Add figcaption (optional)
category: [Knowledge,Data Structure, Hash Table]
tags: [Data Structure, Data Structure, Hash Table, Hash Function]
---

### 들어가며
- 앞서 **자료구조(Data Structure)**는 데이터의 관계, 저장, 처리 및 함수들의 집합이라고 설명했다. 자료구조를 얼마나 잘 활용을 하느냐에 따라, 사용해야하는 메모리를 줄일 수 있으며, 한정적인 컴퓨터의 저장공간을 효율적으로 사용 할 수 있다. 마치 도서관에 책을 잘 정리해두면 단순 컴퓨터 검색만으로 원하는 책을 쉽게 찾을 수 있듯이 말이다. 이 글에서는 **Hash Table** 이라는 중요한 자료구조에 대해서 알아보자.

<br>

### 1. Hash Table 정의
: 해시 테이블은 <ins>**연관배열구조(associative array)를 이용하여 키(key)에 상응하는 결과값(value)을 저장하는 자료구조**</ins>이다. 원리는 해시 함수(**hash function**)에 키(**key**)를 대입해 해시(**hash**)값으로 변경시켜 저장소에 결과값(**value**)을 저장하는 하는것이다.
<br>

- 여기서 연관배열은 **<ins>1개의 key가 1개의 value가 쌍으로 1:1연관되어 있는 자료구조</ins>**라고 생각하면 된다. 그러므로 key값으로 value값을 도출 할 수 있다. 파이썬의 경우 **dictionary**라고 생각하면 이해하는데 도움이 될것이다. 간단하게 **연관배열**의 특징은 아래 사항을 만족한다.
    1. 주어진 **key**와 **value**를 연관배열에 **저장**한다.
    2. 주어진 **key**를 이용해 **value**를 연관배열에서 **검색하고 도출** 할 수 있다.
    3. 주어진 **key**에 새로운 **value**가 들어올 경우, 이전의 **value**를 **수정** 할 수 있다.
    4. 주어진 **key**에 상응하는 **value**를 **삭제** 할 수 있다.

**note: 위와 같은 사항들은 Hash table에서도 변함없이 적용된다.**

<br>

### 1.2 Hash Table의 구조
![Data-Structure-Hash-Table]({{site.baseurl}}/assets/img/Knowledge/Data_Structure/2020-08-18-hash-table/Data-Structure-Hash-Table.png#center)

- **Hash table**은 기본적으로 키(**key**), 해시 함수(**hash function**), 해시(**hash**), 값(**value**), 저장소(**bucket**), 저장공간(**slot**)으로 구성되어 있다. 

    - **키(key)**: 해시함수의 중요한 **input**이며 고유한 값이다. 키의 종류는 정수, 문자열 등 길이와 크기가 다양한 값이 올 수 있다. <ins>**고유한 값**</ins>이기 때문에 그 값 자체를 해시로 취급하여 저장할 수 있으나, <ins>**한정적인 저장 공간의 효율성과 보안성을 고려하여 해시함수에 적용한 뒤 특정한 길이의 값으로 바꾸어 저장**</ins>한다.

    - **해시함수(Hash Function)**: <ins>데이터의 효율적 관리를 위해 임의의 길이인 키(**key**)를 고정적인 길이의 해시(**hash**)로 매핑하는 함수</ins>이다. 해시함수는 해쉬값의 개수보다 대개 많은 키값을 해쉬값으로 변환(**many-to-one**)하기 때문에, 서로 다른 키(**key**)가 같은 해시(**hash**)가 되는 경우가 발생한다. 이를 해시 충돌(**Hash Collision**)이라고 하는데, 해시 충돌을 방지하기위해 좋은 해시 함수를 작성하는게 중요하다.

    - **해시(Hash)**: 해시 함수(**hash function**)로 도출된 결과값이며, 이것을 이용해 저장소(**bucket**)의 저장공간(**slot**)에 값(**value**)을 저장한다.

    - **값(Value)**: 저장소(**bucket**)의 저장공간(**slot**)에 최종적으로 저장되는 값으로 키와 매칭되어 저장, 삭제, 검색, 접근이 가능하다.

    - **저장소(Bucket)**: 저장공간의 집단 혹은 모임을 나타내며, 메모리, 하드드라이브, 나아가서는 cloud까지 포함할 수 있다. 저장소의 크기 할당은 사용자에 의해 정의된다.

    - **저장공간(Slog)** : 키(**key**)와 해시(**hash**)에 상응하는 결과값(**value**)를 저장하는 최소 단위의 저장공간이다. 

<br>

### 1.3 해시 충돌(Hash Collision)
![Data-Structure-Hash-Collision]({{site.baseurl}}/assets/img/Knowledge/Data_Structure/2020-08-18-hash-table/Data-Structure-Hash-Collision.png#center)

- 위의 표를 보면 키 값인 **\'John Smith\'**와 **\'Sandra Dee\'**의 hash값이 **\'02\'**를 가리키고 있다. 흔히 말하는 **Hash Collision**이 발생한 것이다. 전문적으로 설명하자면 서로 **다른 key가 똑같은 하나의 해시값을 반환할때 해시충돌**이 일어난다. 그렇다면 왜 이러한 현상이 나타나는가? 그 이유는 <ins>**다양한 종류, 크기 및 길이를 가진 무한한 data들을 고정된 길이와 크기를 가진 유한한 수의 hash값**</ins>으로 변환시키기 때문이다.

- 그렇다면 이 해시충돌을 해결할 수 있는 대표적인 방법 2가지를 알아보자

    - #### 1.3.1 체인(chaining)
    : 이름에서 알 수 있듯이 체인을 만들어 연결하는것이다. 즉, 저장소(**bucket**)에서 똑같은 해시값으로의 충돌이 일어나면 해당 값에 존재하고 있던 기존 값과 체인을 만들어 연결시키는 기법이다. 이 체인은 연결리스트(**Linked-List**)를 사용하여 구현한다. 각각의 **Node**가 하나의 슬롯의 데이터값을 저장하는 매개체로 이용되는것이다. 아래의 예시를 살펴보자.

    ![Data-Structure-Hash-Collision-Chaining]({{site.baseurl}}/assets/img/Knowledge/Data_Structure/2020-08-18-hash-table/Data-Structure-Hash-Collision-Chaining.png#center)

    - 위 그림에서도 키 값인 **\'John Smith\'**와 **\'Sandra Dee\'**가 똑같은 **hash**값인 **\'152\'**를 가리키고 있다. 하지만 연결 리스트를 활용하여 **\'John Smith\'**의 Value값이 **\'Sandra Dee\'**의 Value값을 가리키고 있다.

    - **Chaining의 장점과 단점**
        - **장점**
            - 한정된 저장소(**Bucket**)을 효율적으로 사용 가능하다. **Hash Collision** 문제를 해결 할 수 있다.
            - **해시 함수의 의존도**를 낮출 수 있다.(해시 충돌이 일어나지 않도록 극도의 해시 함수를 작성하지 않아도 된다는 뜻이다)
        - **단점**
            - 하나의 <ins>**hash**값에 많은 결과값이 몰릴 수</ins>가 있다.(**worst-case**: 모든 key의 해시값이 똑같을 경우)
            - 저장소(**bucket**)이 아닌 **외부 저장공간**을 따로 확보하고 사용해야한다.

    <br>

    - #### 1.3.2 개방 주소법(Open Addressing)
    :**Open Addressing**은 chaining과 달리 <ins>**하나의 저장공간(slot)에는 오직 하나의 데이터만 들어갈 수 있도록 저장하는 기법**</ins>이다. 만약, **해시 충돌이 일어날 경우 해당하는 해시값의 주소가 아닌 다른 비어있는 주소의 저장공간(slot)에 데이터를 저장**한다.

    ![Data-Structure-Hash-Collision-Open-Addressing]({{site.baseurl}}/assets/img/Knowledge/Data_Structure/2020-08-18-hash-table/Data-Structure-Hash-Collision-Open-Addressing.png#center)

    - 위 그림을 보면 키 값인 **\'John Smith\'**와 **\'Sandra Dee\'**가 똑같은 hash값인 **\'152\'**를 가리키고 있지만, **Open Addressing**으로 **\'Sandra Dee\'**를 그 다음 hash값인 **\'153\'**을 가리켰고, **\'Ted Baker\'**는  그 다음 hash값인 **\'153\'**을 가리키고 있다.

    - 여기서 중요한 점은 <ins>**충돌이 일어 났을경우 비어있는 Hash값의 주소를 찾는 방식**</ins>이다. 이 **방식은 충돌이 일어날 경우 동일하게 작동**해야한다. 이렇게 비어있는 Hash값의 주소를 찾는 방법을 **탐사(Probing)**를 통해 찾을 수 있다. 탐사하는 방법은 대표적으로 3가지가 있다.

        1. **선형 탐색(Linear Probing)**: 바로 다음 Hash값의 주소를 가져오거나(이 경우 +1), +2,...+n을 적용해서 찾는다.
        2. **제곱 탐색(Quadratic Probing)**: 충돌이 일어난 해시값을 제곱한다. 그 결과값에 해당하는 해시에 데이터를 저장한다.
        3. **이중 해시(Double Hashing)**: 다른 해시함수를 한 번 더 적용한 해시에 데이터를 저장한다. 즉 해시함수를 2개 이상 사용한다.

    - **Open Addressing의 장점과 단점**
        - **장점**
            - 해시 테이블 내에서 모든 데이터를 처리할 수 있다. 즉 **외부 저장공간이 필요하지 않고**, 초기에 설정한 bucket으로만으로 데이터를 관리할 수 있다. 
        - **단점**
            - **해시함수의 중요성**이 커진다.(hash값이 몰리지 않도록 해시함수 작성에 신중함을 기해야한다)
            - 데이터의 양이 늘어나면 그에 해당하는 저장소(bucket)의 크기를 늘려주어야한다. 

<br>

### 1.4 해시 테이블의 기본 연산과 시간 복잡도
해시 테이블의 기본 3가지 연산은 **삽입, 삭제, 검색**이며 각각의 시간복잡도는 해시 충돌이 있을 경우와 없을 경우로 나뉜다.
**n** 은 데이터의 총 개수를 나타난다. 

|              |해시 충돌이 없을 경우|해시 충돌을 chaining으로 해결할때|해시 충돌을 Open Addressing으로 해결할때|
|삽입(Insertion)|   **O(1)**     |**O(k),(1<=k<=n)**         |       **O(k),(1<=k<=n)**         |
|삭제(Deletion) |   **O(1)**     |**O(k),(1<=k<=n)**         |       **O(k),(1<=k<=n)**         |
|검색(search)   |   **O(1)**     |**O(k),(1<=k<=n)**         |       **O(k),(1<=k<=n)**         |

<br>

### 1.5 해시 함수(Hash Function)의 종류

앞서 설명했듯이 해시 함수는 해시 테이블의 효율을 극대화시키고 해시 충돌(**Hash Collision**)문제의 처리를 위해 중요한 역할을 담당한다. 잘 <ins>**작성된 해시 함수는 해시 충돌을 예방하고 방지하는것이 아닌, 특정 hash값으로 몰리는것을 방지하고 균형잡힌 갯수의 hash값을 도출**</ins>하는 것이다. 여기서는 기본적으로 잘 알려진 해시 함수 3가지를 알아보자

1. **나누기분산방법(Division Method)**
    : 나눗셈법은 간단하면서도 빠른 연산이 가능한 해시함수이다. 정수로 된 키의 값을 해시테이블의 크기인 **m**으로 나눈 나머지를 해시값으로 반환합니다. **m**은, 보통 소수(**prime number**)를 쓰는것이 일반적이며 특히 2의 제곱수와 거리가 먼 소수를 사용하는 것이 효율적이다. 즉, 해시함수 특성 때문에 해시테이블 크기가 정해진다는 단점이 있다는 뜻이다.

2. **곱셈분산방법(Multiplication Method)**
    : 키의 값 정수 **K**이고 **A**는 **0**과 **1**사이의 **실수**를 전제로 곱셈분산방법을 정의해보자. **m**은 **2의 제곱수**로 두고 계산을 하였을 경우 나눗셈범보다는 다소 느리지만 2진수 연산에 최적화된 컴퓨터의 구조를 고려한 해시함수이다.

                                    h(k) = (kA mod 1) × m

3. **Universal hashing**
    : 다수의 해시함수를 만들고, 이 <ins>**해시함수 집합 H에서 무작위로 해시함수를 선택해 해시값을 만드는 기법**</ins>이다. **H**에서 무작위로 뽑은 해시함수 **h(n)**이 주어졌을 때 임의의 키값을 임의의 해시값에 매핑할 확률을 **1/m**로 만드려는 것이 목적이다. 여기서 **m**은 해시 **테이블의 크기**이며 **소수**임을 전제한다.

<br>

### 1.6 해시 테이블(Hash Table)의 장점과 단점
- **장점**
    - 적은 자원(**Resource**)으로 **많은 데이터를 효율적으로 관리하기 용이**하다. 해시함수로 하드디스크나 클라우드에 존재하는 무한에 가까운 데이터(키)들을 유한한 개수의 해시값으로 매핑함으로써 작은 크기의 캐쉬 메모리로도 프로세스를 관리할 수 있다.
    - **해시값을 Index로 사용**하기 때문에 **삽입, 검색, 삭제 연산을 빠르게 수행**할 수 있다(시간 복잡성 O(1)).
    - **key**와 **hash**값 사이의 직접적인 연관이 없기때문에 **보안성이 뛰어**나다(hash값만 가지고는 key의 값을 복윈하기 어럽다.)

- **단점**
    - <ins>**해시 함수에 대한 의존도**</ins>가 높다. **기본 연산인 Insertion, Deletion, Search는 상수시간에 수행이 가능하지만 이것은 해시함수의 연산 시간을 교려하지 않은 결과**이다.
    - **저장되지도 않은 데이터를 위한 저장공간을 미리 마련**해야하기 때문에 **저장공간의 효율성은 떨어지는 편**이다.
    - 데이터의 **상하관계 혹은 순서**가 중요한 경우에는 **해시 테이블을 사용하기에 적합하지 않다**.(순서에 관계없이 key의 hash값에 의해서만 데이터를 저장하기 때문이다.)

<br>

### 마치며
모든것을 다 cover하기는 쉽지 않다. 마치 Hash Collision이 일어나지 않게 hash Function을 작성하려고 하는것처럼.. 문제가 무엇인지 정확히 파악하고 해결하려고 하는 자세, **포기하지 않는것이 중요하다.** <br> 
**기본에 충실하고 집착하자.** 

### reference
[\[Image-of-Data-Structure-Hash-Table-Main/google/UofT-library\]](https://www.google.com/search?q=u+of+t+library&sxsrf=ALeKk00fcNabeybbrqdwnYpoVfVgf0SiEw:1597717716224&source=lnms&tbm=isch&sa=X&ved=2ahUKEwiG5rSn2qPrAhUYE4gKHXRyBKIQ_AUoAXoECBgQAw&biw=1280&bih=616#imgrc=9-MEP329Pbqy2M) <br>
[\[Image-of-Data-Structure-Hash-Table/imgur/EMW1YZP \]](https://imgur.com/EMW1YZP) <br>
[\[Image-of-Data-Structure-Hash-Collission/naverblog/chodahi\]](https://m.blog.naver.com/PostView.nhn?blogId=chodahi&logNo=221406239782&proxyReferer=https:%2F%2Fwww.google.com%2F) <br>
[\[Data-Structure-Hash-Table-Collision/dbehdrhs/tistory \]](https://dbehdrhs.tistory.com/70) <br>
[\[Data-Structure-Hash-Table-Collision-Chaining-&-Open-Addressing/dayzen1258/tistory\]](https://dayzen1258.tistory.com/entry/%ED%95%B4%EC%8B%9C%ED%85%8C%EC%9D%B4%EB%B8%94%EC%9D%B4%EB%9E%80) <br>
[\[Data-Structure-Hash-Table-Hash-Functions/luyin/tistory \]](https://luyin.tistory.com/191) <br>
[\[Data-Structure-Hash-Table-Composition/adam2/velog\]](https://velog.io/@adam2/%EC%9E%90%EB%A3%8C%EA%B5%AC%EC%A1%B0%ED%95%B4%EC%8B%9C-%ED%85%8C%EC%9D%B4%EB%B8%94) <br>
[\[Data-Structure-Hash-Table-Time-Complexity-&-Definitions\]](https://ratsgo.github.io/data%20structure&algorithm/2017/10/25/hash/) <br>
[\[Data-Structure-Hash-Table-Definitions/wiki\]](https://en.wikipedia.org/wiki/Hash_table) <br>

