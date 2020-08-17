---
layout: post
title: 연결 리스트(Linked-List)에 대해서..
date: 2020-08-17 00:00:00 +0300
description:  # Add post description (optional)
img:  Knowledge/Data_Structure/2020-08-17-linked-list/Data-Structure-Linked-List-Main.jpg
fig-caption: # Add figcaption (optional)
category: [Knowledge,Data Structure,Linked List]
tags: [Data Structure,Linked List] # add tag
---

### 들어가며
연결 리스트(**linked list**)는 면접 문제로 자주 출제되는 자료구조 중에 하나이다. 그 만큼 실제 코딩에서 중요한 역할을 하고 있다는 뜻이다. 이 글에서는 연결 리스트의 정의, 종류, 구현 및 중요성에 대해 알아보자!

<br>

### 연결 리스트(Linked-List) 정의
연결리스트는 <ins>**Node를 기반으로 서로 연결되어 데이터를 저장하는 자료구조**</ins>이다. **Node**는 데이터의 값과 포인터 혹은 노드를 이어주는 링크로 구성되어 있다. 이러한 연결구조는 일반적인 배열과 비교했을때 데이터의 삽입과 삭제가 빠르다. 

이해를 돕기 위해 간단한 예시를 들자면, 회사에 근무하는 직장인으로 생각해보자. 새로운 신입이 회사에 취직을 했을때 일반적인 배열은, 최근에 들어온 막내 옆자리 새로운 신입을 앉혀야 한다. 하지만 연결리스트는 회사 내에 아무 빈자리나 새로운 신입에게 줄 수 있다. 그러나 새로운 신입 이전의 막내는 새로운 신입의 자리가 어디인지 기억해야 한다. 

기본적인 노드를 **Python**과 **C**로 구현해보았다.
``` python
# Node class in Python 
class Node:
# Function to initialize the node object
   def __init__(self, data):
       self.data = data # Assign data
       self.next = None # Initialize next as null
```
```c
// Node in C
typedef struct Node{
    int data;
    struct Node* next;
}node;
```
<br>
**시간 복잡도**

|                |**single-linked-list**|**Doubly-Linked-List**|**Single-Circular-Linked-List**|
|**삽입(Insert)** |     **O(1)**         |        **O(1)**      |            **O(1)**           |
|**삭제(Delete)** |     **O(1)**         |        **O(1)**      |            **O(1)**           |
|**검색(Search)** |     **O(n)**         |        **O(n)**      |            **O(n)**           |

- **장점**
1. 삽입과 삭제가 **O(1)**에 이루어진다
2. 삽입과 삭제를 할 때마다 **동적으로 링크드 리스트의 크기가 결정**되므로 전통적인 배열(<ins>**C언어와 같이 초기 배열 생성에 메모리를 할당 해야하는 경우**</ins>)에 비해 처음부터 큰 공간을 할당할 필요가 없어진다.
3. 메모리 관리가 용이하다(이 또한 C언어가 여기에 해당된다.)
- **단점**
1. **Random Access**, 즉 일반적인 배열처럼 **index를 통한 탐색이 불가능**하다.
2. 탐색이 **O(n)**만큼 걸린다.(worst case = from Head to Tail)
3. 실질적으로 Head 노드, Tail 노드 혹은 특정한 노드를 가리키는 포인터가 있지 않는 이상 결국 처음부터 탐색을 하여 노드를 삭제해야 하기 때문에 **O(k)**에서 **O(n)**만큼의 시간이 걸린다.(1\<=k\<\=n)
<br>

**Note**: C언어와 같이 초기 배열 설정에 메모리를 할당해줘야하는 경우에는 연결리스트(**Linked-List**)가 메모리 관리면에서 효율적이지만 **Python**과 같은 언어는 배열 자체를 알아서 동적으로 관리하기 때문에 연결리스트의 의미가 많이 퇴색된다. 또한 Python에서는 list에 튜플이나 문자열, 심지어는 리스트를 넣을 수 도 있기 때문에 일반적인 리스트를 쓰지 않을 이유가 없다. 한마디로 Python **리스트**가 짱이다... 

<br>

### 연결 리스트(Linked-List) 종류
연결 리스트(**Linked-List**)는 크게 총 3가지 종류로 나눌 수 있다.
1. **단순 연결 리스트(Single-Linked-List)** 
2. **이중 연결 리스트(Doubly-Linked-List)**
3. **단순 원형 연결리스트(Single-Circular-Linked-List)** 

-------------------------------------------------------------

#### 1. 단순 연결 리스트(Single-Linked-List)
: 기본적인 연결 리스트이며 **Head Node**가 존재하고 **Head Node**는 그 다음 노드를 가르킨다. 그러므로 한방향에서 연결되어 배열의 형태를 지니고 있다.

![Data-Structure-Single-Linked-List]({{site.baseurl}}/assets/img/Knowledge/Data_Structure/2020-08-17-linked-list/Data-Structure-Single-Linked-List.png#center)

아래는 ***Python***으로 간단하게 **Singled-Linked-List**를 구현해보았다.
``` python
# node class
class Node:
    # initialize
    def __init__(self, data):
        self.data = data
        self.next = None

    def __str__(self):
        return str(self.data)

# single-linked-list
class SingleLinkedList:
    # initialize
    def __init__(self):
        self.head = None

    def __str__(self):
        if self.head == None:
            return
        new_node = self.head
        result = '['
        while new_node:
            result += str(new_node) + ' '
            new_node = new_node.next
        return result.strip() + ']'

    def insert(self, data):
        # first element is added into Linked List
        if not self.head:
            self.head = Node(data)
        # insert new data into Linked List
        else:
            node = self.head
            while node.next:
                node = node.next
            new_node = Node(data)
            node.next = new_node

    def delete(self, data):
        if not self.head:
            return
        node = self.head
        # deleted node is a head node
        if node.data == data:
            self.head = node.next
            node = None
            return
        while node.next:
            if node.next.data == data:
                # deleted node is not at the end of linked list
                if node.next.next:
                    node.next = node.next.next
                # deleted node is at the end of linked list
                else:
                    node.next = None
            node = node.next

    def search(self,data):
        if self.head == None:
            print("Linked list is empty")
            return
        node = self.head
        while node.next:
            if node.data == data:
                print(node.data)
                return
            node = node.next
        print("Given data, ", data, " is not in the linked list")
        return
```
<br>

#### 2. 이중 연결 리스트(**Doubly-Linked-List**)
: 이중 연결 리스트는 **Head Node**가 존재하고 그 노드는 다음 노드를 가리킨다. **Head Node**를 제외한 모든 노드들은 이전 노드의 다음노드를 가리킨다. 그러므로 삽입, 검색, 삭제 연산을 할 경우 양쪽 노드 모두 신경 써줘야한다.

![Data-Structure-Doubly-Linked-List]({{site.baseurl}}/assets/img/Knowledge/Data_Structure/2020-08-17-linked-list/Data-Structure-Doubly-Linked-List.png#center)

아래는 ***Python***으로 간단하게 **Doubly-Linked-List**를 구현해보았다. **Single-Linked-List**와의 차이점은 주석에 그 차이점을 달아놓았으니 참고하기 바란다.
``` python
# node class
class Node:
    # initialize
    def __init__(self, data):
        self.data = data
        self.next = None
        # only different than Singled-Linked-List
        self.prev = None

    def __str__(self):
        return str(self.data)

# doubly-linked-list
class DoublyLinkedList:
    # initialize
    def __init__(self):
        self.head = None

    def __str__(self):
        if self.head == None:
            return
        new_node = self.head
        result = '['
        while new_node:
            result += str(new_node) + ' '
            new_node = new_node.next
        return result.strip() + ']'

    def insert(self, data):
        # first element is added into Linked List
        if not self.head:
            self.head = Node(data)
        # insert new data into Linked List
        else:
            node = self.head
            while node.next:
                node = node.next
            new_node = Node(data)
            new_node.prev = node
            node.next = new_node

    def delete(self, data):
        if not self.head:
            return
        node = self.head
        # deleted node is a head node
        if node.data == data:
            self.head = node.next
            node = None
            return
        while node.next:
            if node.next.data == data:
                # deleted node is not at the end of linked list
                if node.next.next:
                    node.next = node.next.next
                    # only Difference than Singled-Linked-List
                    node.next.next.prev = node
                # deleted node is at the end of linked list
                else:
                    node.next = None
            node = node.next

    def search(self,data):
        if self.head == None:
            print("Linked list is empty")
            return
        node = self.head
        while node.next:
            if node.data == data:
                print(node.data)
                return
            node = node.next
        print("Given data, ", data, " is not in the linked list")
        return
```

<br>

#### 3. 단순 원형 연결리스트(**Single-Circular-Linked-List**)
: 단순 연결리스트와 구성상 동일하지만 제일 마지막 노드가 None을 아닌 **Head Node**를 가리키고 있는게 차이점이다.

![Data-Structure-Circular-Linked-List]({{site.baseurl}}/assets/img/Knowledge/Data_Structure/2020-08-17-linked-list/Data-Structure-Circular-Linked-List.png#center)

아래는 ***Python***으로 간단하게 **Circular-Linked-List**를 구현해보았다.
``` python
# node class
class Node:
    # initialize
    def __init__(self, data):
        self.data = data
        self.next = None

    def __str__(self):
        return str(self.data)

# Circular-linked-list
class CircularLinkedList:
    # initialize
    def __init__(self):
        self.head = None

    def __str__(self):
        if self.head == None:
            return
        new_node = self.head
        result = '['
        while new_node:
            result += str(new_node) + ' '
            if new_node.next == self.head:
                break
            new_node = new_node.next
        return result.strip() + ']'

    def insert(self, data):
        # first element is added into Linked List
        if not self.head:
            node = Node(data)
            self.head = node
            node.next = node
        # insert new data into Linked List
        else:
            node = self.head
            #only different than singled-linked-list
            while node.next != self.head:
                node = node.next
            new_node = Node(data)
            node.next = new_node
            new_node.next = self.head

    def delete(self, data):
        if not self.head:
            return
        node = self.head
        # different than singled-linked-list
        head = self.head
        # deleted node is a head node
        if node.data == data:
            last_node = self.lastNode()
            self.head = node.next
            last_node.next = self.head
            return
        # different than singled-linked-list
        while node.next and node.next != head:
            if node.next.data == data:
                # deleted node is not at the end of linked list
                if node.next.next:
                    node.next = node.next.next
                # deleted node is at the end of linked list
                else:
                    node.next = head
            node = node.next

    def search(self,data):
        if self.head == None:
            print("Linked list is empty")
            return
        node = self.head
        # only different than single-linked-list
        head = self.head
        while node.next and node.next != head:
            if node.data == data:
                print(node.data)
                return
            node = node.next
        print("Given data, ", data, " is not in the linked list")
        return

    def lastNode(self):
        node = self.head
        while node.next != self.head:
            node = node.next
        return node
```

<br>

### 마치며
연결 리스트는 기본적인 동적 자료구조이면서 **Queue**와 **Stack**을 구현함에 있어 필 수 적이다. 앞으로 풀어볼 문제들에서 다용도로 많이 쓰일 것이기 때문에 이해를 정확히 하고 넘어가자.
**당장 눈앞에 보지이 않는다고 포기하기엔 너무 이르다.**

### reference

[\[Definition-of-Data-Structure-Linked-List/opentutorial\]](https://opentutorials.org/module/1335/8821) <br>
[\[Definition-of-Data-Structure-Linked-List/wayhome25/github\]](https://wayhome25.github.io/cs/2017/04/17/cs-19/) <br>
[\[Pros-and-Cons-of-Data-Structure-Linked-List/underflow101/tistory\]](https://underflow101.tistory.com/3#recentComments) <br>
[\[Classification-of-Data-Structure-Linked-List/mycsh1094/naver-blog \]](https://m.blog.naver.com/PostView.nhn?blogId=mycsh1094&logNo=80117881737&proxyReferer=https:%2F%2Fwww.google.com%2F) <br>
[\[Image-of-Data-Structure-Linked-List-Main/wcwonline/WCW-Blog-Women-Change-Worlds\]](https://www.wcwonline.org/WCW-Blog-Women-Change-Worlds/Connected-teaching-an-approach-for-classrooms-communities-and-the-workplace) <br>
[\[Image-of-Data-Structure-Single-Linked-List/GeeksforGeeks\]](https://www.geeksforgeeks.org/difference-between-a-static-queue-and-a-singly-linked-list/) <br>
[\[Image-of-Data-Structure-Doubly-Linked-List/GeeksforGeeks\]](https://www.geeksforgeeks.org/doubly-linked-list/) <br>
[\[Image-of-Data-Structure-Circular-Linked-List/GeeksforGeeks\]](https://www.geeksforgeeks.org/circular-linked-list/) <br>





