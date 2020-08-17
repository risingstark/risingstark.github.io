---
layout: post
title: Stack
date: 2020-08-15 00:00:00 +0300
description:  # Add post description (optional)
img:  Knowledge/Data_Structure/2020-08-15-stack/Data-Structure-Stack-Main.jpg
fig-caption: # Add figcaption (optional)
category: [Knowledge,Data Structure,Stack]
tags: [Data Structure,Stack] # add tag
---

### 들어가며
자료구조의 기본인 ***Stack***에 대해 알아보자. 이 글에서는 스택의 정의와 구현방법 쓰임새에 대해 다룰것이다. 

<br>

### Stack 정의
컴퓨터 프로그래밍에서의 ***Stack***이 뜻하는 의미는 두가지로 나뉜다.
1. **메모리상의 Heap영역에서 휘발이 가능한 데이터를 저장는 Stack기능**.
2. **스택 영영 메모리에서 프로그램의 각 분기점에 변수와 같은 정보를 저장하기 위한 자료구조의 일종인** ***Stack***.

 이 글에서는 **Stack**의 두번째 의미를 가진 자료구조의 **Stack**을 알아보자.

스택은 **<ins>한쪽 끝에서만 Data를 삽입, 제거할 수 있는 선형구조(LIFO-Last in First Out)</ins>**로 되어 있다. data를 목록에 밀어 넣는다고 하여 **삽입과정**을 **Push**라고 하며, 반대로 Data를 끄집어 낸다고하여 제거하는 과정을 **Pop**이라고 한다. 

![Data-Structure-Stack]({{site.baseurl}}/assets/img/Knowledge/Data_Structure/2020-08-15-stack/Data-Structure-Stack.jpeg#center)

예를 들면 A,B,C의 자료들을 순서대로 push하여 스택에 넣을 경우. Pop연산은 그 반대인 C,B,A 순서로 Data를 반환한다.

기본적으로 스택을 S라고 할 경우 스택의 기본 함수는 아래와 같다.
- **S.top()**: 스택 제일 위쪽에 위치한 데이터를 반화한다(**<ins>삭제는 하지 않고 그냥 보여만 준다</ins>**). 만약 스택이 비어있다면 이 연산을 쓸 수가 없다.
- **S.pop()**: 스택 제일 위쪽에 위치한 데이터를 **반환하고 삭제**한다. 만약 스택이 비었다면 이것 또한 정의 불가상태이다.
- **S.push('A')**: 스택의 마지막에 A라른 데이터를 삽입한다. 
- **S.empty()**: 스택이 비어있는지 아닌지를 반환한다. 비어있으면 1을 그렇지 않다면 0를.

<br>

### Stack 구현

Stack의 정의와 함수들에 대해 알아보았다. 여기서는 **Stack**을 간단하게 ***Python***언어로 구현 해보자.

```python
class Stack:
     def __init__(self):
         self.items = []

     def isEmpty(self):
         return self.items == []

     def push(self, item):
         self.items.append(item)

     def pop(self):
         return self.items.pop()

     def peek(self):
         return self.items[len(self.items)-1]

     def size(self):
         return len(self.items)

```

<br>

### Stack의 사용 예시
Stack은 자료구조의 기본인만큼 여려 영영에서 쓰이고 있다. 그 예시를 간단히 알아보자.

- **재귀알고리즘(Recursion)**
- **웹 브라우저상에서의 뒤로가기**
- **실행 취소(Undo)**
- **역순 문자열 만들기**


### 마치며
이론적으로 스택을 이해했는가? 그러면 **Stack**을 활용해 여러가지 문제를 풀어보도록 하자. 문제를 풀어야 **Stack**을 완전히 이해하고 자신의 것으로 만들 수 있을것이다.



### reference
[\[Definition-of-Data-Structure-Stack/wiki\]](https://en.wikipedia.org/wiki/Stack_(abstract_data_type)) <br>
[\[Definistion-of-Data-Structure-Stack/namuwiki\]](https://namu.wiki/w/%EC%8A%A4%ED%83%9D(%EC%9E%90%EB%A3%8C%EA%B5%AC%EC%A1%B0)) <br>
[\[Example-of-Stack/gmlwjd9405/github\]](https://gmlwjd9405.github.io/2018/08/03/data-structure-stack.html) <br>
[\[Picture-of-Data-Structure-Stack/lokeshdhakar/bookstack\]](https://lokeshdhakar.com/my-book-stack/) <br>
[\[Picture-of-Data-Structure-Stack/medium/swih\]](https://medium.com/swlh/stacks-and-queues-simplified-ef0f838fc534) <br>
