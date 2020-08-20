---
layout: post
title: 버블정렬(BubblesSort)
date: 2020-08-20 00:00:00 +0300
description:  # Add post description (optional)
img:  Knowledge/Algorithms/2020-08-20-bubblesort/Algorithms-BubbleSort-Main.jpg
fig-caption: # Add figcaption (optional)
category: [Knowledge,Algorithms,Sorting,BubbleSort]
tags: [Algorithms,Sorting,BubbleSort]
---

### 들어가며
정렬! 필자가 신병교육대대 조교일때 가장 많이 사용했던 단어 중 하나이다. 병장쯤 되니 훈련병들 정렬 속도가 **Mergesort급** 정도 되는 기억이...(이병때는 bubblesort보다 더 느렸다). 컴퓨터 과학에서 <ins>**정렬(Sorting)은 한 집단에 속해있는 데이터를 일련의 순서 혹은 기준에따라 차례대로 정리하는 방법**</ins>이다. 이러한 정렬은 대용량 데이터를 관리하고 처리하는데 큰 도움을 준다. 효율적인 정렬 알고리즘을 사용한다면 그 가치는 배가 된다. 이 글에서는 기본적인 버블정렬 알고리즘의 정의와 구현방법, 시간 복잡도에 대해 알아보자.

<br>

### 버블 정렬(BubbleSort) 정의
: **서로 인접한 두 원소를 비교하여 정렬하는 알고리즘이다**. 1번째와 2번째를 비교하여 큰 수를 2번째로 옮기고, 다시 2번째와 3번째를 비교해서 큰 수를 3번째에 옮긴다. 이런식으로 n-1번째와 n번째까지를 비교하여 n번째에 저장하면 1~n개의 숫자중에 제일 큰 수가 n번째에 저장이된다. 똑같은 방식으로 다시 1번째에서 n-1까지 비교하여 저장한다.  

<br>

### 버블정렬(BubbleSort)의 예시
![Algorithms-Bubblesort-Example]({{site.baseurl}}/assets/img/Knowledge/Algorithms/2020-08-20-bubblesort/Algorithms-Bubblesort-Exmaple.png#center)

위 그림은 버블정렬을 사용하여 간단한 데이터를 오름차순으로 정리한 예시이다. 1회전부터 4회전까지 버블정렬이 어떤식으로 작동하는지 알아보자.

- **1회전** 
    - **step1**: 첫번째 숫자 **7**과 두번째 숫자 **2**를 비교하여 큰 수인 **7**을 **2**와 교환
    - **step2**: 두번째 숫자 **7**을 세번째 숫자 **8**과 비교하여 큰 수인 **8**을 세번째 자리에 배치
    - **step3**: 세번째 숫자 **8**과 네번째 숫자 **5**를 비교하여 큰 수인 **8**을 **5**와 교환
    - **step4**: 네번째 숫자 **8**을 마지막 숫자 **4**와 비교햐여 큰 수인 **8**을 **4**와 교환
    - **step5**: **1회전** 결과로 배열 안의 제일 큰 숫자인 **8**이 제일 마지막에 위치

2회전, 3회전, 3회전 역시 1회전과 동일한 방식으로 진행이 된다. 그러므로 4회전이 끝날때 주어진 초기 배열 **[7,2,8,5,4]**이 오름차순으로 정리가 된 **[2,4,5,7,8]**로 정렬 된다

<br>

### 시간 복잡도(Time complexity)
버블 정렬은 한번 **순회 할때마다 비교 대상이 하나씩 줄어든다는 특징**을 가지고 있다. 전체 개수를 n개라 가정했을때, 제일 큰 수를 찾아서 비교하고 마지막번째 자리로 옮기는게 n-1이 걸리고, 그 다음은 n-2가 걸린다. 이러한 방식을 수식으로 정리 하면,

    (n-1) + (n-2) + ... + 2 + 1 = n*(n-1)/2

자리 교환이 이루어지든 이루어지지 않든 n개의 원소를 정렬하려면 버블정렬은 **O(n^2)**이 소요된다.

<br>

### 버블정렬(BubbleSort) 구현

간단하게 **Python**으로 버블정렬을 구현해보았다.
``` python
def bubbleSort(l):
    '''(list) -> (list)
    Given l is unordered list and return ordered list using bubbleSort Algorithm 
    '''
    for i in range(len(l)):
        for j in range(len(l)-i-1):
            if l[j] > l[j+1]:
                l[j],l[j+1] = l[j+1], l[j]
    return l
```

### 마치며
버블 정렬은 너무나 **간단하고 구현하기가 쉽다는 장점**이 있지만, **정렬 시간이 오래걸린다는 단점**이 있다. 즉, 알고리즘 정렬 자체의 효율성이 많이 떨어진다. 실제로 많이 쓰이지는 않지만 개념에 대해서는 알아두도록하자.  


### reference
[\[Picture-of-Algorithms-Bubblesort-Example/Medium/Esswhy91\]](https://medium.com/@Esswhy91/what-the-heck-is-bubble-sort-25ee0b374b51) <br>
[\[Image-of-Algorithms-Bubblesort-Main/sciencenews/article\]](https://www.sciencenews.org/article/physicists-find-atomic-nucleus-bubble-middle) <br>
[\[Algorithms-Bubblesort-Definition/namuwiki\]](https://namu.wiki/w/%EC%A0%95%EB%A0%AC%20%EC%95%8C%EA%B3%A0%EB%A6%AC%EC%A6%98) <br>
[\[Algorithms-Bubblesort-Concept-General/wiki\]](https://en.wikipedia.org/wiki/Bubble_sort) <br>