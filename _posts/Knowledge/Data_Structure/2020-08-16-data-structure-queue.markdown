---
layout: post
title: Q->u->e->u->e?
date: 2020-08-16 00:00:00 +0300
description:  # Add post description (optional)
img:  Knowledge/Data_Structure/2020-08-16-queue/Data-Structure-Queue-Main.jpg
fig-caption: # Add figcaption (optional)
category: [Knowledge,Data Structure,Queue]
tags: [Data Structure,Queue] # add tag
---

### 들어가며
살면서 새치기를 해본적이 있는가? 아니면 당해본적이 있는가? 필자는 법과 도덕을 중시하는 사람이라 새치기를 볼때마다 마음이 불편하고 한편으로 아프다. 그럴때마다 줄 서는것을 **Queue**로 구현하면 좋을텐데 라고 생각한다(실제로는 **Queue** 형태이지만, 안지켜진다...) 이 글에서는 자료구조에서 중요한 역할을 하고 있는 **Queue**에 대해 알아보겠다. 개인적으로 이 **Queue**가 <ins>**민주적인 놈?!**</ins>이라 그런지 참 좋아한다. 그 이유는 먼저 들어온놈이 먼저 나가기 때문이다. 

<br>

### Queue 정의
기본적으로 **Queue**는 먼저 들어온 data가 먼저 나가는(**FIFO- First in First out**)형식으로 되어있다. 즉, **<ins>한쪽 끝에서는 삭제 연산만 이루어지고 다른 한쪽에는 삽입 연산</ins>**만 이루어진다.

![Data-Structure-Queue]({{site.baseurl}}/assets/img/Knowledge/Data_Structure/2020-08-16-queue/Data-Structure-Queue.png#center)

**Queue**를 구성하는 함수는 기본적으로 4가지가 된다. **Queue()**를 간단히 **q**로 가정했을때,
- **q.add(item)** or **q.enqueue(item)**: item을 **큐의 끝부분에 삽입**한다. 큐가 꽉 차서 더이상 item을 넣을 수 없는 경우 <ins>***overflow***</ins>가 발생한다
- **q.remove()** or **q.dequeue()**: q의 첫번째 item을 **반환 및 제거**한다. q가 비어 있을경우 반환 및 삭제할 item이 없기 때문에 <ins>***underflow***</ins>가 발생한다.
- **q.peek()**: q의 첫번째 item을 반환한다(**삭제는 하지 않는다!!**). q가 비어 있을경우 역시 <ins>***underflow***</ins>가 발생한다.
- **q.isEmpty()**: q가 비어 있을 경우 **'1'** 혹은 **'True'**를 반환하고 그 반대는 **'0'** 혹은 **'False'**를 반환한다. 

<br>

### Queue의 종류

#### 1. **직선큐**(***Linear-Queue***)
:일반적인 **Array**로 **Queue**를 구현할 경우이다. 위 **Queue** 정의에 정리된 그림과 똑같은 형태이다.
- **장점**: **Array**를 사용하기 때문에 **구현하기 쉽다**.
- **단점**: 직선큐에서 **remove()** 혹은 **dequeue()** 연산을 시행할때, 배열에 있는 <ins>**2번째부터 마지막까지 존재하는 data를 앞쪽으로 다 당겨주여야하는 치명적인 단점**</ins> 있다. 단순히 data가 작을경우는 문제가 되지 않지만 단순한 연산 하나때문에 엄청난 양의 데이터를 앞으로 움직여야할때는 효율적이지 않다.
<br>

**note**: 만약 이것을 보완하기 위해 전단(**Front**,큐에서 첫번째 원소의 위치를 기억하는 포인터)과 후단(**Rear**,다음 원소가 들어올 위치를 기억하는 포인터, 여기에서는 제일 마지막 원소)의 위치를 기억하고 관리한다면 굳이 배열의 원소를 옮길 이유가 없다. 하지만 이것의 단점은 **데이터를 앞으로 옮겨주지 않아 후단에 데이터가 들어올 곳이 없어진다(dequeue를 하면 할 수록 큐의 가용 용량이 줄어든다는 것)** 즉, <ins>**배열로 큐를 선언할시 큐의 삭제와 생성이 계속 일어났을때, 마지막 배열에 도달후 실제로는 데이터 공간이 남아 있지만 오버플로우**</ins>가 발생함.

<br>

#### 2. 원형큐(Circled-Queue)
:**순환큐**라고도 불리는 이 형태는 배열의 **처음과 끝을 이어놓은 형태**이다. 즉, <ins>**물리적으로는 일직선이나 논리적으로는 원형**</ins>을 나타낸다.
![Data-Structure-Circled-Queue]({{site.baseurl}}/assets/img/Knowledge/Data_Structure/2020-08-16-queue/Data-Structure-Circular-Queue.png#center)
- **장점**: 직선큐의 단점을 보완할 수 있다. 
- **단점**: 이것 또한 **Array**로 구성되기때문에 **용량의 제한**을 받는다. 또한 전단(**front**)와 후단(**rear**) 포인터를 주어진 연산에 따라 이리 저리 옮겨다녀야 하기 때문에 **구현의 복잡성**이 따라온다.

<br>

#### 3. 링크드 큐(linked-Queue with sinled-linked-List)
:***Linked-List***의 기본 단위인 **node**를 기반으로 만들어진 **Queue**이다. 원형큐의 원리와 비슷하게 각각의 노드들은 다음 노드의 주소값을 가지고 있고 노드의 방향은 **전단(front)**에서 **후단(rear)**으로 이루어져 있다.
<br> **note**: 이 글에서는 간단히 **singled-linked-list**로의 예로만 제시하겠다. **Doubled & Circular-Linked-List**는 **knowledge - Data Structure**를 참고하자)

![Data-Structure-Linked-Queue]({{site.baseurl}}/assets/img/Knowledge/Data_Structure/2020-08-16-queue/Data-Structure-Linked-Queue.gif#center)
-**장점**: 구현이 간단하고 용량에 제한이 없어 효율적이다.

아래는 ***Python***으로 간단하게 **Linked-Queue**를 구현해보았다.

```python
# Node class 
class Node:
# Function to initialize the node object
   def __init__(self, data):
       self.data = data # Assign data
       self.next = None # Initialize next as null
       self.prev = None # Initialize prev as null
 
# Queue class contains a Node object
class Queue:
   def __init__(self):
       self.head = None
       self.last=None
     
   def enqueue(self, data):
       if self.last is None:
           self.head =Node(data)
           self.last =self.head
       else:
           self.last.next = Node(data)
           self.last.next.prev=self.last
           self.last = self.last.next
             
   def dequeue(self):
       if self.head is None:
           return None
       else:
           temp= self.head.data
           self.head = self.head.next
           self.head.prev=None
           return temp
 
   def peek(self):
       return self.head.data
 
   def size(self):
       temp=self.head
       count=0
       while temp is not None:
           count=count+1
           temp=temp.next
       return count
           
   def isEmpty(self):
       if self.head is None:
           return True
       else:
           return False
 
   def printqueue(self):
       print("queue elements are:")
       temp=self.head
       while temp is not None:
           print(temp.data,end="->")
           temp=temp.next
```
#### 4. 우선순위 큐(Priority Queue)
: 컴퓨터 과학에서는 우선순위 큐(**Priority Queue**)는 평범한 큐와 스택과 비슷한 축약 자료형이라고 할 수 있다. 다만 <ins>**각각의 원소들은 우선순위**</ins>를 가지고 있다는게 차이점일뿐이다. 우선순위는 설명할것이 많이 있기 때문에 따로 자세한 내용은 **Knowledge - Data Structure** 섹션에 있는 **Priority Queue**를 참고하자 

<br>

### Queue의 사용 예시
**Queue**는 자료구조의 기본인만큼 여려 영역에서 쓰이고 있다. 그 예시를 간단히 알아보자.

- **너비우선탐색(BFS)**
- **Cache**
- **우선순위가 같은 작업 예약(인쇄 대기열)**
- **Ticket counter**
- **Call center waiting**
- **Managing process**


### 마치며
큐 또한 스택과 마찬가지로 자료구조의 중요한 역할을 담당하고 있다. 큐와 스택은 기본이니 만큼 무조건 자세히 알고 있어야한다.
<br>**어제보다 더 성장할 나를 위해**

### reference
[\[Definition-of-Data-Structure-Queue/wiki\]](https://en.wikipedia.org/wiki/Queue_(abstract_data_type))) <br>
[\[Definistion-of-Data-Structure-Queue/namuwiki\]](https://namu.wiki/w/%ED%81%90
(%EC%9E%90%EB%A3%8C%EA%B5%AC%EC%A1%B0))) <br>
[\[Data-Structure-Queue/exynoa/tistory\]](https://exynoa.tistory.com/213?category=431859) <br>
[\[Data-Structure-Queue-Circular-Queue/logonluv/blogspot\]](http://logonluv.blogspot.com/2015/02/datastructure-queue.html) <br>
[\[Data-Structure-Queue-Linked-Queue/hexabrain/blog\]](https://blog.hexabrain.net/213) <br>
[\[Example-of-Queue/devuna/tistory\]](https://devuna.tistory.com/22) <br>
[\[Picture-of-Data-Structure-Queue/medium/songjaeyoung92/blog\]](https://medium.com/@songjaeyoung92/%EC%9E%90%EB%A3%8C%EA%B5%AC%EC%A1%B0-javascript-queue-%EB%9E%80-dbd8b2fffeac) <br>
[\[Picture-of-Data-Structure-Queue-Main/getlevelten/ian-whitcombswih/blog\]](https://getlevelten.com/blog/ian-whitcomb/whats-wrong-project-application-queue) <br>
[\[Picture-of-Data-Structure-Queue-Circular-Queue/studytonight/\]](https://www.studytonight.com/data-structures/circular-queue) <br>
[\[Picture-of-Data-Structure-Queue-Linked-Queue/cs.grinnell/\]](https://www.cs.grinnell.edu/~walker/courses/195.fa01/lab.queues.html) <br>




