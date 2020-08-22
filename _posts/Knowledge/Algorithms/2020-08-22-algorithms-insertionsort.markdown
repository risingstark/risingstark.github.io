---
layout: post
title: 삽입정렬(InsertionSort)
date: 2020-08-22 00:00:00 +0300
description:  # Add post description (optional)
img:  Knowledge/Algorithms/2020-08-22-insertionsort/Algorithms-InsertionSort-Main.jpg
fig-caption: # Add figcaption (optional)
category: [Knowledge,Algorithms]
tags: [Algorithms,InsertionSort]
---

### 들어가며
버블정렬, 선택정렬과 같이 붙어다닌다고 할 수 있는 삽입 정렬이다. 이 글에서는 삽입정렬의 정의, 예시, 시간복잡도, 간단한 파이썬으로 구현하는것까지 해보자!

<br>

### 삽입정렬(InsertionSort)정의
삽입 정렬(**insertion sort**)은 **<ins>자료 배열의 모든 요소를 앞에서부터 차례대로 이미 정렬된 배열 부분과 비교하여, 자신의 위치를 찾아 삽입함으로써 정렬을 완성하는 알고리즘</ins>**이다. 즉 삽입정렬로 **k번째 반복 후의 결과배열**은 **앞쪽부터 k+1번째까지 정렬**이 되어 있다.

- 삽입정렬(**오름차순**) 구현 순서
    1. 임의의 값 **key**를 설정한다. (**key값은 두번째 요소부터 시작하여 배열의 크기 n까지의 수**이다.)
    2. 배열에서 **key값**이 위치한 자리의 이전 요소들과 key값을 비교해 들어갈 자리는 찾는다. 이때 key의 값이 그 이전 요소보다 작다면 key의 자리에 바로 그 전 요소를 이동시킨다.
    3. key의 값이 들어갈 자리를 찾았으면 그 자리에 삽입하고, key의 값을 증가시킨다.
    4. 2~3번째 과정을 **배열이 끝날때까지 반복**한다.

<br>

### 삽입정렬(InsertionSort) 예시

![Algorithms-Insertion-Sort-Example]({{site.baseurl}}/assets/img/Knowledge/Algorithms/2020-08-22-insertionsort/Algorithms-Insertion-Sort-Example.gif#center)

- 위 그림은 초기배열 **[5,2,4,6,1,3]**을 삽입정렬 알고리즘을 이용하여 **오름차순**으로 정렬한것이다. 편의상 **원안의 숫자들을 key값**으로 정하자. 
    - **첫번째 줄**: 초기배열에서 **\'2\'**가 **Key**의 값이므로 그 전 요소인 **\'5\'**와 비교한다. **\'5\'**가 크기때문에 **key**의 자리에 **\'5\'**를 이동시키고 **\'2\'**를 제일 처음 자리에 삽입한다.
    - **두번째 줄**: **key**의 값인 **\'4\'**를 그 바로 전 요소인 **\'5\'**와 비교한다. **\'4\'**가 작기때문에 **key**의 위치로 **\'5\'**를 이동시키고 그 다음 전 요소인 **\'2\'**와 키값 **\'4\'**를 비교한다. **\'4\'**가 **\'2\'**보다 크기때문에 그 자리에 **key**값인 **\'4\'**를 삽입한다.
    - ...(위 차례를 반복)
 
<br>

### 삽입정렬 구현

아래는 삽입정렬을 **Python** 언어로 간단하게 구현해보았다. 
``` python
def insertionSort(l):
    '''(list) -> (list)
    return sorted list using insertionSort algorithm given unordered list, l
    '''
    for i in range(1,len(l)):
        j = i - 1
        key = l[i]
        while l[j] > key and j >= 0:
            l[j+1] = l[j]
            j-=1
        l[j+1] = key
    return l
```

<br>

### 삽입정렬 시간 복잡도(Time Complexity)
- 삽입 정렬의 시간 복잡도는 간단하다.
    - **Worst-case: O(n^2) 비교, O(n^2) 교환**
    - **best-case: O(n) 비교, O(1) 교환 (이미 배열이 정렬되어 있는 경우, 1번의 비교만 필요하고 외부 순환 n-1번의 비교만 이루어진다.)**

<br>

### 마치며
선택정렬과 헷갈려 하는 사람들이 많은것 같다. 선택정렬은 요소가 들어갈 위치는 정해져 있는거고, 그 자리에 들어갈 요소를 찾는것이다. 하지만 삽입정렬은 요소는 정해져 있고, 그 요소가 들어갈 자리를 찾는것이다. 버블정렬, 삽입정렬, 선택정렬은 항상 같이 붙어 다니기 때문에 구현하는 방법과 정의, 예시들을 잘 알아두도록 하자!

<br>

### reference
[\[Image-of-Insertion-Sort-Example/google-image \]](https://www.google.com/search?q=%EC%83%88%EC%B9%98%EA%B8%B0&tbm=isch&ved=2ahUKEwjDhKSl563rAhUM62EKHWnzDu8Q2-cCegQIABAA&oq=%EC%83%88%EC%B9%98%EA%B8%B0&gs_lcp=CgNpbWcQAzIECCMQJzIECCMQJzICCAAyAggAMgQIABAYMgQIABAYMgQIABAYMgQIABAYMgQIABAYMgQIABAYOgUIABCxA1CcnAFY1KEBYOSiAWgCcAB4AoABcogBkQWSAQMwLjaYAQCgAQGqAQtnd3Mtd2l6LWltZ8ABAQ&sclient=img&ei=nohAX8O9MIzWhwPp5rv4Dg&bih=616&biw=1280#imgrc=qFQi0xYywEZd8M) <br>
[\[Image-of-Insertion-Sort-Example/hongku/tistory\]](https://hongku.tistory.com/148) <br>
[\[General-Concept-of-Insertion-Sort/gmlwjd9405/github\]](https://gmlwjd9405.github.io/2018/05/06/algorithm-insertion-sort.html) <br>
