---
layout: post
title: 자료구조(Data Structure)
date: 2020-08-14 00:00:00 +0300
description:  # Add post description (optional)
img:  Knowledge/Data_Structure/2020-08-15/Data-Structure-main.jpeg
fig-caption: # Add figcaption (optional)
category: [Knowledge,Data Structure]
tags: [Algorithm, Data Structure] # add tag
---

### 들어가며
자료구조(***Data Structre***)는 컴퓨터 프로그래밍에 있어서 너무나도 중요하다. 그 이유는 **다양한 프로그램을 설계하고 개발함에 있어 구현의 난이도나 최종 결과물의 성능이 자료구조에따라 크게 영향**을 미치기 때문이다. 그렇다면 이 글에서 자료구조는 어떤 것을 나타내며, 중요성 및 종류에 대해 살펴보자.  

<br>

### Data Structure 정의
컴퓨터 과학에서의 ***Data Strucutre***는 <ins>**효율적으로 테이터에 접근하고 수정, 관리 및 저장**</ins>을 뜻한다. 한마디로 <ins>**데이터들의 모임, 데이터의 관계 그리고 데이터에 적용할 수 있는 함수나 명령**</ins>을 의미한다. 

자료구조의 목적은 확실하다. **자료를 효율적으로 저장하고 관리하며, 한정적인 자원을 가지고 있는 컴퓨터를 좀더 실용적이게 사용**하려는 것이다. 잘 선택된 자료구조는 실행시간 및 메모리 용량을 줄여주어 컴퓨터의 과부화를 막고 프로그램의 성능을 향상 시킬 수 있다.

그럼 프로그램을 설계하고 개발할때, 자료구조의 선택 기준은 무엇인가? 아래를 살펴보자
- **데이터 처리시간**
- **데이터의 크기**
- **데이터 활용빈도**
- **데이터 수정 빈도 및 접근성**


<br>

### Data Structure 분류

자료구조를 분류하는 방식에따라 크게 2가지로 나눌 수 있다. <ins>**구현하는 방식에 따라 분류**</ins>를 하거나, <ins>**형태에 따라 분류**</ins>를 하거나이다. 자료구조들의 종류는 여러가지이다. 이 부분에서는 각각의 자료구조가 간단히 어떤것인지, 어디에 분류되어 있는지만 알아보자.

#### 1. 구현하는 방식에따라 분류
- **배열**(***Array***): 메모리 상에 같은 타입의 자료가 연속적으로 저장된다. 자료값을 나타내는 가장 작은 단위가 자료를 다루는 단위이다
- **튜플**(***Truple***): 둘 이상의 자료형을 묶음으로 다루는 구조이다.
- **연결리스트**(***Linked List***): 노드를 단위로 한다. 노드는 자료와 다음 노드를 가리키는 참조값으로 구성되어 있다. 노드가 다음 노드로 아무것도 가리키지 않으면 리스트의 끝이다.
- **원형 연결 리스트**(***Circle-Linked List***): 각 노드는 다음 노드를 가리키고, 마지막 노드가 처음 노드를 가리키는 연결 리스트이다.
- **이중 연결 리스트**(***Double Linked List***): 각 노드는 이전 노드와 다음 노드를 가리키는 참조값으로 구성된다. 처음 노드의 이전 노드와 마지막 노드의 다음 노드는 없다.
- **해시 테이블**(***Hash Table***): 개체가 해시값에 따라 인덱싱된다.

#### 2. 형태에따라 분류
![Data-Structure-Classificatino]({{site.baseurl}}/assets/img/Knowledge/Data_Structure/2020-08-15/Data-Structure-Classification.png#center)

위 표에서 볼 수 있듯이 형태에 따라 분류하는 Data Strucutre은 크게 2가지로 나뉜다.<br>

2.1 선형구조(***Linear Data Structure***)
- **배열**(***Array***): 위 내용 참고
- **스택**(***Stack***): 스택 자료구조에 먼저 저장된 것이 꺼내어 쓸 때는 제일 나중에 나온다. 반대로, 가장 최근에 저장된 것이 꺼내어 쓸 때는 제일 먼저 나온다. 만약, 자료들의 나열 순서를 바꾸고 싶다면 스택에 집어 넣었다가 꺼내면 역순으로 바뀐다.
- **큐**(***Queue***): 스택과 반대로 큐 자료구조에 먼저 저장된 것이 제일 먼저 나온다. 반대로, 가장 나중에 저장된 것이 꺼내어 쓸 때는 가장 나중에 나온다.
- **연결리스트**(***Linked-list***): 위 내용 참고

2.2 비선형구조(***Non-Linear Data Structure***)
- **그래프**(***Graph***): vertex와 vertext를 이어주는 변으로 구성된다.
- **트리**(***Tree***):root와, root 또는 다른 vertex를 단 하나의 부모로 갖는 vertex들로 이루어진 구조. 부모 자식 관계는 변으로 표현된다.

<br>

### 마치며
실제로 ***Data Structure***은 컴퓨터 과학의 기초분야이다. 더하기 빼기도 못하는데 미적분을 어떻게 하는가? 강조하고 강조하지만 항상 기본기가 제일 중요하다. 시간 날때마다 틈틈히 찾아보며, 공부했던 내용을 상기시키도록하자.

이 글에서는 자료구조의 개념에 대해서 설명을 했다. 각각 자료구조들의 구체적인 정의와 예시, 구현하는 방법은 ***Knowledge - Data Structure*** 섹션을 참고하자

### reference
[\[Definition-of-Data-Structure/wiki\]](https://en.wikipedia.org/wiki/Data_structure) <br>
[\[Definistion-of-Algorithm/ratsgo's-blog\]](https://ratsgo.github.io/data%20structure&algorithm/2017/11/22/greedy/) <br>
[\[Clssification-of-DSandrew0409/tistroy\]](https://andrew0409.tistory.com/148) <br>
[\[Def-of-Data-Structure-Linear-Non-Linear/islove8587\]](https://m.blog.naver.com/PostView.nhn?blogId=islove8587&logNo=220548856458&proxyReferer=https:%2F%2Fwww.google.com%2F) <br>
[\[Picture-of-Data-Structure/Nick-Mose/DEV\]](https://dev.to/snj/how-to-learn-data-structures-and-algorithms-an-ultimate-guide-for-beginners-2h9c) <br>
[\[Picture-of-Data-Structure-Classification\GeeksforGeeks\]](https://www.geeksforgeeks.org/difference-between-linear-and-non-linear-data-structures/) <br>

