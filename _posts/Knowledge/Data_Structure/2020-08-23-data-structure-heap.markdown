---
layout: post
title: Heap-Heap-Heap...
date: 2020-08-23 00:00:00 +0300
description:  # Add post description (optional)
img:  Knowledge/Data_Structure/2020-08-23-heap/Data-Structure-Heap-Main.jpg
fig-caption: # Add figcaption (optional)
category: [Knowledge,Data Structure]
tags: [Data Structure, Heap]
---

### 들어가며
에베레스트산은 그 자체만으로도 경이롭다. 누군가 쌓아올린 이 거대한 산은 언제부터인지 지구상 최대 높이를 자랑한다. 이 글에서 소개하고자하는 heap은 영어로는 **\'쌓아올리다\'** 라는 뜻을 가지고 있고, 최대값 혹은 최소값을 구하기위해 고안된 완전이진트리 자료구조이다. 자세한 정의와 예시, 종류, 연산등에 대해 알아보자.

<br>

### Heap 정의
: **<ins>완전이진트리(Completed-binary-tree)를 기본으로 최대값 혹은 최소값을 빨리 찾아내기 위해 고안된 자료구조</ins>**이다.(우선순위 큐를 위해 고안된 자료구조라고 표현 할 수도 있다.) Heap은 최대힙과 최소힙으로 분류 할 수 있으며, Heap은 아래와 같은 특성을 가진다.

- **A가 B의 부모노드**이면, **A노드의 key값과 B노드의 key값 사이에는 대소관계**가 성립한다.(최대힙일 경우 Root가 Max Value, 최소힙은 그 반대이다.)
- 키값은 부모노드의 자식노드간에만 대소관계가 형성되고, **형제노드는 성립하지 않는다**.
- 힙트리에서는 **중복된값을 허용**한다(이진탐색트리 **Binary Search Tree에서는 중복값이 불가**하다)

<br>

### Heap 예시

- 힙의 기본적인 저장 구조는 **배열**이다. 즉, 실질적으로는 배열을 이용하여 요소들을 저장하지만 논리적으로는 완전이진트리 형식을 가지고 있다.
- Heap 구현의 편의성을 위해 **첫번째 Index인 0은 사용하지 않는다**. 
- **Heap-list**로 표현할때 부모노드와 자식노드의 관계는 아래와 같은 특성을 가지고 있다. **임의의 노드 i**에 대해서,
    - **왼쪽 자식** =  **2i** 번째에 위치한다
    - **오른쪽 자식**= **2i+1** 번째에 위치한다.
    - **부모노드**= **i/2** 번째에 위치한다 

- 예시로 아래 그림을 자세히 살펴보자

![Data-Structure-Heap-Max-Heap]({{site.baseurl}}/assets/img/Knowledge/Data_Structure/2020-08-23-heap/Data-Structure-Heap-Max-Heap.bmp#center)

- i의 값이 2인 key의 값 \'C\'를 예시로 들어보겠다.
    - \'C\'의 왼쪽 자식노드의 값은 \'D\' => 2i = 2*2 = 4(배열의 4번째 요소이다)
    - \'C\'의 오른쪽 자식노드의 값은 \'G\' => 2i + 1 =2*2 + 1 = 5(배열의 5번째 요소이다)
    - \'C\'의 부모노드 값은 \'A\' => i/2 = 2/2 = 1(배열의 첫번째 요소이다)

<br>

### Heap의 종류
- Heap의 종류는 2가지, **최대힙(Max-Heap)**과 **최소힙(Min-Heap)**으로 나눌 수 있다.

![Data-Structure-Heap-Exmaple]({{site.baseurl}}/assets/img/Knowledge/Data_Structure/2020-08-23-heap/Data-Structure-Heap-Example.png#center)

- **최대힙(Max-Heap)**
    1. root 노드를 제외한 모든 노드들은, **KEY(T.parent(V)) >= KEY(V)** 이다(내림차순). 즉, 부모노드는 자식노드보다 항상 크거나 같다.
- **최소힙(Min-Heap)**
    1. root 노드를 제외한 모든 노드들은, **KEY(T.parent(V)) <= KEY(V)** 이다.(오름차순). 즉, 부모노드는 자식노드보다 항상 작거나 같다.

<br>

### Heap 연산
:Heap에서는 기본적으로 삽입과 제거 연산이 있다. 이 두가지 기본 연산을 구현하기 위해선 Heapify라는 연산을 구현해 이용하는것이 효율적이다. **Heapifiy**는 쉽게말해 **<ins>삽입과 제거 연산이 일어났을때, Heap특성을 유지해주는 연산</ins>**이다. 편의를 이용해 Max-Heap을 예시로 들어서 설명하겠다.

- #### 삽입(Insert)-(Max-Heap)
    1. Heap에 새로운 요소가 들어오면 일단 제일 마지막 노드(배열의 마지막)에 삽입한다.
    2. Heap특성을 유지를 위해 새로운 노드의 위치를 찾아 부모노드와 비교하며 교환해 위치를 찾아간다(Heapify연산 이용).

- #### 제거(Delete)-(Max-Heap)
    1. Heap에서의 제거는 항상 루트노드 최대값을 제거하는 것이다. 이때 루트노드와 제일 마지막 노드의 위치를 바꾼뒤 루트 노드를 제거한다.
    2. 마지막 노드가 루트노드로 온뒤, Heap의 특성을 유지해야하기 때문에 루트노드를 자식노드와 비교해 그 위치를 찾아간다(Heapify연산 이용). 

**note**: 이 글은 Heap 자료구조를 중점적으로 설명하기 때문에 Heap 연산의 구현, 시간 복잡도 및 사용법등은 **Knowledge-Algorithms** 파트에 있는 **힙 정렬(HeapSort) Post**를 참고하자.
<br>

### 마치며
힙은 실제 많이 쓰이는 자료 구조이다. 그 이유는 우선순위 큐(**Priority Queue**)를 구현하기에 가장 효율적인 자료구조이기 때문이다. 그러므로 우선순위큐를 이해하기 위해선 힙을 완벽히 알고 있어야 한다. 하나부터 차근 차근 알아가보자!

<br>

### reference
[\[Image-of-Data-Structure-Heap-Main/mindgil-chosun/article\]](http://mindgil.chosun.com/client/board/view.asp?fcd=F1030&nNewsNumb=20191268613&nCate=C04&nCateM=M1003) <br>
[\[Image-of-Data-Structure-Heap-Example/geeksforgeeks\]](https://www.geeksforgeeks.org/heap-data-structure/) <br>
[\[Image-of-Data-Structure-Heap-Max-Heap/cs.cmu.edu/adamchik\]](https://www.cs.cmu.edu/~adamchik/15-121/lectures/Binary%20Heaps/heaps.html/) <br>
[\[Definition-of-Data-Structure-Heap/hackerearth\]](https://www.hackerearth.com/ja/practice/data-structures/trees/heapspriority-queues/tutorial/#:~:text=A%20heap%20is%20a%20tree,be%20followed%20across%20the%20tree.) <br>
[\[General-Definition-of-Max-and-Min-Heap/personalblog-github/gmlwjd9505\]](https://gmlwjd9405.github.io/2018/05/10/data-structure-heap.html) <br>
