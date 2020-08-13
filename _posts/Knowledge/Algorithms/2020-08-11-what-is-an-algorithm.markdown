---
layout: post
title: 알고리즘이란 무엇인가?
date: 2020-08-12 00:00:00 +0300
description:  # Add post description (optional)
img: Knowledge/Algorithms/2020-08-12/algorithms_main.jpg # Add image post (optional)
fig-caption: # Add figcaption (optional)
category: [Knowledge,Algorithms]
tags: [Algorithms] # add tag
---

### 들어가며
<br>
살면서 알고리즘이라는 단어를 들어본적이 있을것이다. 들어본적이 없다면 이 글을 읽고 있는 바로 지금 알고리즘에 대해 배워보자. 필자는 컴퓨터 과학을 전공으로 알고리즘이란 단어를 수도 없이 듣고 공부했다. 하지만 막상 다른이에게 알고리즘을 설명하려고 한다면 전문적인 지식만 늘어 놓을뿐 정확한 설명은 해줄 수 가 없었다. 이 글을 토대로 알고리즘에 대한 정의를 명확하게 정리하고, 알고리즘을 공부하는 모든이에게 도움이 되길 바린다.

<br>

### 알고리즘의 정의(Definition of Algorithm)
인터넷에 "알고리즘이란?" 문장을 검색해보면 다양한 정보들이 존재한다. 간단하게 위키피디아에서 정의하는것은 
<br>
>알고리즘(라틴어, 독일어: Algorithmus, 영어: algorithm 알고리듬[*], IPA: [ǽlɡərìðm])은 수학과 컴퓨터 과학, 언어학 또는 관련 분야에서 어떠한 문제를 해결하기 위해 정해진 일련의 절차나 방법을 공식화한 형태로 표현한 것, 계산을 실행하기 위한 단계적 절차를 의미한다.

<ins>**주어진 문제를 단계별로 나누어 해답을 찾는 것!**</ins> 예를 들어, 서울에서 부산으로 최단시간 혹은 최단거리를 찾는 알고리즘을 생각해보자. KTX를 타거나, 비행기, 자동차, 자전거 혹은 걸어서 갈 수 있다. 차를 타고 간다면 국도나 고속도로와 같은 선택지들도 있다. 이러한 예시를 알고리즘으로 풀때 여러가지 전제 조건이 붙는다.
<br> 
- **입력** : 외부에서 0개 이상의 자료가 제공된다.
- **출력** : 서로 다른 결과물이 적어도 2개이상이다. (즉, 모든 입력값의 결과값이 하나가 되면 안된다.)
- **명확성** : 수행 과정은 명확하고 모호하지 않은 명령어로 구성되어야 한다.
- **유한성(종결성)** : 유한 번의 명령어를 수행 후(유한 시간 내)에 종료한다.
- **효율성** : 모든 과정은 명백하게 실행 가능(검증 가능)한 것이어야 한다.

<br>

### 알고리즘의 종류(Varification of Algorithms)

![Algorithms-classification]({{site.baseurl}}/assets/img/Knowledge/Algorithms/2020-08-12/algorithms_classification.png#center)
<br>

알고리즘을 분류하는 방법에는 여러가지가 존재한다. 표에서는 당장 생각나는 알고리즘을 정리해놓았다. 이것 말고도 현재 존재하는 알고리즘은 수십,수백가지가 달하며 우주항공, 생명공학, 핵원자, 의료산업등 분야별로 알고리즘을 선택해서 개발하고 사용한다. 표에 적힌 알고리즘은 앞으로 하나 하나 자세하게 풀어서 설명할 계획이니 해당 블로그의 ***Knowledge - Algoritms*** 섹션을 찹고하자.

<br>


### 복잡성(Time & Space Complexity)
알고리즘의 핵심이라고 할 수 있는 부분이다. 알고리즘 정의에서도 보았듯이, 효율적이여야한다. 즉, 알고리즘을 통해 내가 시간적으로  공간적으로 자유로운가? 알고리즘이 나에게 도움을 주는가? 이게 최선인가? 하는 궁금증을 풀 수 있어야한다. 

<ins>**컴퓨터과학에서의 시간복잡도는 입력하는 값에 따라 알고리즘이 걸리는 최대시간**</ins>을 나타낸다. 모든 알고리즘의 소요시간을 정확히 평가 할 수는 없으므로, 입력되는 값의 수(간단하게 **n**이라 표현하겠다), **n**이 증가할 때 시간이 늘어나는 대략적인 패턴을 시간 복잡도라고 부른다. 표기법은 ***Big-O notation, O(n)*** 으로 나타낸다. 이때 중요한점은 계수와 낮은 차수항을 제외 시키는 방법이다. 예를 들어 알고리즘이 **f(n) = 5n^2 + 2n + 1** 일 경우, 이 알고리즘, **f(n)**의 시간 복잡도는 **O(n^2)**라고 할 수 있다. 즉, 최대 계수만 활용한다.

공간 복잡도는 쉽게말해 얼마나 많은 자원이 필요한가. **n**개의 입력값을 받았으나, 출력되는 값을 구하기 위해 메모리를 얼마나 활용했느냐를 수치로 나타낼 수 있다. 알고리즘마다 필요로하고 처리하는 공간이 다르기때문에 다른 알고리즘 파트에서 자세히 다루겠다. 지금은 단순히 입력값, **n**에 대한 최대 공간이라고만 알아두자.

#### 시간 복잡도(Time Complexity)

![Algorithms-Time-Complexity]({{site.baseurl}}/assets/img/Knowledge/Algorithms/2020-08-12/algorithms_time_complexity.png#center)
- **O(1)** : 입력 자료의 수에 관계없이 일정한 실행 시간을 갖는 알고리즘
- **O(log N)** : 입력 자료의 크기가 **N**일경우 **log N** 번만큼의 수행시간을 가진다.
- **O(N)** : 입력 자료의 크기가 **N**일경우 **N** 번만큼의 수행시간을 가진다.
- **O(N log N)** : 입력 자료의 크기가 **N**일경우 **N(log N)** 번만큼의 수행시간을 가진다.
- **O(N^2)** : 입력 자료의 크기가 **N**일경우 **N^2** 번만큼의 수행시간을 가진다.
- **O(N^3)** : 입력 자료의 크기가 **N**일경우 **N^3** 번만큼의 수행시간을 가진다.
- **O(2^n)** : 입력 자료의 크기가 **N**일경우 **2^N** 번만큼의 수행시간을 가진다.
- **O(n!)** : 입력 자료의 크기가 **N**일경우 **n*(n-1)*(n-2)... * 1(n!)** 번만큼의 수행시간을 가진다.

<br>

### 마치며


### reference
[\[Definition-of-Algorithms/wiki\]](https://en.wikipedia.org/wiki/Algorithm) <br>
[\[Verification-of-Algorithms/inpages/tistory\]](https://inpages.tistory.com/85) <br>
[\[Verification-of-Algorithms/hsp1116/tistory\]](https://hsp1116.tistory.com/category/Algorithm) <br>
[\[Pics-AlgorithmGrowth/Time-Complexity\]](https://medium.com/@randerson112358/algorithm-analysis-time-complexity-simplified-cd39a81fec71) <br>
[\[Time-and-Space-Complexity/madplay/github\]](https://madplay.github.io/post/time-complexity-space-complexity) <br>

