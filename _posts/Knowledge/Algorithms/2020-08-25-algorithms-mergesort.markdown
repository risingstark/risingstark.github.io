---
layout: post
title: 합병정렬(MergeSort)
date: 2020-08-25 00:00:00 +0300
description:  # Add post description (optional)
img:  Knowledge/Algorithms/2020-08-25-mergesort/Algorithms-Merge-Sort-Main.jpg
fig-caption: # Add figcaption (optional)
category: [Knowledge,Algorithms]
tags: [Algorithms,Mergesort]
---

### 들어가며
합병정렬은 퀵정렬과 함께 실제 많이 쓰이고 있는 정렬이다. 둘다 분할 정복을 기초로 정렬하는 알고리즘이지만, 퀵정렬은 분할리스트를 비균등하게 나누지만 합병정렬은 항상 반으로 나누는 차이점이 있다. 뭔가 합병정렬은 학교에서 제일가는 모범생같은 느낌이 든다. 항상 반으로 나누라는, 교과서를 꼭 따라가야만 답을 정확히 얻을 수 있는... 퀵정렬은 반에서 공부를 조금하는 개구장이 같은 느낌이다. 항상 반으로 나누는 것이 아닌 자신이 원하는데로 나누지만 어떨 땐 이런 틀에 정해지지 않는 방법이 최선의 해답이 될 수 있기 때문이다.(실제로 이런 방법들이 잘 먹히는 경우가 살다보면 많다) 이 글에서는 합병정렬의 정의, 예시, 구현, 시간복잡도 등에 대해 알아보자. 

<br>

###  합병정렬(MergeSort) 정의
 
- **배열의 크기가 1이하로 될때까지 <ins>항상 반으로 나눈뒤</ins>, 분할된 부분 리스트들을 합쳐가며 정렬하는 알고리즘**이다. 
- 합병정렬은 퀵정렬과 마찬가지로 분할정복개념을 기초로한 안정된 정렬 알고리즘이다.
    - **분할(Divide)**: 주어진 Input 배열을 크기가 같은 두 배열로 분할한다.
    - **정복(Conquer)**: 분할된 두 리스트를 정렬시킨다. 이때 두 부분리스트의 크기가 크다면 순환호출(**Recursion**)을 이용해 다시 분할정복 시킨다
    - **결합(Combine)**: 정렬된 두 부분배열을 하나로 결합한다.

<br>

### 합병정렬(MergeSort) 예시

![Algorithms-Merge-Sort-Example]({{site.baseurl}}/assets/img/Knowledge/Algorithms/2020-08-25-mergesort/Algorithms-Merge-Sort-Example.png#center)

위 그림은 초기 배열 **[7,3,2,16,24,4,11,9]**를 합병정렬 알고리즘을 사용하여 **오름차순**으로 정리하는 예시이다. 각각 단계별로 어떻게 진행되는지 알아보자.

- **분할**
    - 초기 배열을 **크기가 같은 두개의 부분 배열로 분할**한다.
    - 분할된 크기가 1이하가 될때까지 **계속** 크기가 같은 두개의 부분 배열로 분할한다.
- **정복 & 결합**
    - 분할된 두 배열의 **첫번째 요소들**부터 서로 비교하며 정렬해 나간다. 만약 **한쪽 배열이 먼저 정렬되면 나머지 남은 부분배열은 그대로 정렬된 배열로 복사**한다.
    - 분할된 배열들을 합병한뒤, 합병된배열의 크기가 초기 배열의 크기가 될때까지 **순환호출(Recursion)**에 의해 정렬되고 합병이 계속 진행된다.


<br>

### 합병정렬(MergeSort) 구현
아래는 합병정렬을 **Python**언어로 구현해보았다.

``` python
def merge_sort(l):
    '''(list) -> (list)
    return sorted list using Merge Sort algorithm given unsorted list l
    '''
    if len(l) <= 1:
        return l
    mid = len(l)//2
    left_list = l[:mid]
    right_list = l[mid:]
    left_list = merge_sort(left_list)
    right_list = merge_sort(right_list)
    return merge(left_list, right_list)


def merge(left, right):
    '''(list, list) -> (list)
    return sorted list by comparing and merging given two lists, left and right
    '''
    sorted_list = []
    while len(left) > 0 or len(right) > 0:
        if len(left) > 0 and len(right) > 0:
            if left[0] <= right[0]:
                sorted_list.append(left[0])
                left = left[1:]
            else:  # left[0] < right[0]:
                sorted_list.append(right[0])
                right = right[1:]
        elif len(left) > 0 and len(right) == 0:
            sorted_list += left
            break 
        elif len(right) > 0 and len(left) == 0:
            sorted_list += right
            break
    return sorted_list
```

<br>

### 합병정렬(MergeSort) 시간 복잡도
- **합병정렬(MergeSort)**의 알고리즘 특성을 보면 항상 배열을 **반**으로 분할한 뒤 정렬한다. 이러한 점 때문에 합병정렬은 어떠한 배열이 주어지더라도 Best-case, Worst-case 그리고 Average-case가 모두 같다.
아래 그림으로 합병정렬의 시간복잡도에 대해 알아보자.

![Algorithms-Merge-Sort-Time-Complexity-Example]({{site.baseurl}}/assets/img/Knowledge/Algorithms/2020-08-25-mergesort/Algorithms-Merge-Sort-Time-Complexity-Example.png#center)

- 합병정렬에서의 시간복잡도는 분할과정이 아닌 정복과 합병에서 일어난다. 그 이유는 **분활 과정에서는 단순히 분할만하고, 비교와 이동연산이 일어나지 않기 때문**이다.
- **정복 & 합병**
    1. **비교연산**: 위 그림에서 보듯이 마지막 배열부분에서는 총 **n**개가 있고, 마지막 배열 단계에서 총 **n**번 비교해야한다. 트리의 깊이는 **k = log(n)** (**n**이 2의 제곱근일때, **n=2^k** => **k = log(n)**이 된다)이기 때문에, **n * log(n)**이 된다.
        - 비교연산 시간복잡도 : **O(n log(n) )**  
    2. **이동연산**: 트리의 깊이는 **k = log(n)** (**n**이 2의 제곱근일때, **n=2^k** => **k = log(n)**이 된다)이다. 이때 각 단계별로 임시 배열에 저장해두었다가 가져와야하므로 총 개수 **n**에 대하여 **2n**번의 이동이 발생한다. 즉 이동연산에 대한 시간 복잡도는 **(트리의 깊이 * 단계별 이동횟수)** = **(log(n) * 2n)**이 된다.
        - 이동연산 시간복잡도 : **O( 2nlog(n) )** 

    ***합병정렬 시간복잡도, T(n) = 비교연산 + 이동연산 = O( nlog(n) ) + O( 2nlog(n) ) = O( nlog(n) )***

<br>

### 마치며
합병정렬에 대해 알아보았다. 정렬 알고리즘을 공부하면서 항상 느끼지만 손으로 혹은 컴퓨터로 기록해가며 공부를 하는것이 정말 정리가 잘되고 기억에도 오래 남는다. 단순히 머리속으로만 생각할때 막혔던 부분이 시원하게 해결되는 느낌이 든다.

<br>

### reference
[\[Image-of-Algorithms-Merge-Sort-Main/google-image\]](https://www.google.com/search?q=%ED%95%A9%EB%B3%91&sxsrf=ALeKk02xIyEAo3WH-6wQYdp_PCZR4wONIw:1598322360630&source=lnms&tbm=isch&sa=X&ved=2ahUKEwiHyarkprXrAhWZMd4KHYBLCL4Q_AUoAXoECAwQAw&biw=1280&bih=616#imgrc=6SqsUbMqRYyy3M) <br>
[\[Exmaple-of-Algorithms-Merge-Sort/101computing\]](https://www.101computing.net/merge-sort-algorithm/) <br>
[\[General-Concept-of-Algorithms-Merge-Sort/ratsgo/personal-blog\]](https://ratsgo.github.io/data%20structure&algorithm/2017/10/03/mergesort/) <br>
[\[Image-of-Algorithms-Merge-Sort-Time-Complexity-Example/gmlwjd9405/github/personal-blog\]](https://gmlwjd9405.github.io/2018/05/08/algorithm-merge-sort.html) <br>
