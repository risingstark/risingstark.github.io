---
layout: post
title: 퀵정렬(QuickSort)
date: 2020-08-24 00:00:00 +0300
description:  # Add post description (optional)
img:  Knowledge/Algorithms/2020-08-24-quicksort/Algorithms-Quick-Sort-Main.jpg
fig-caption: # Add figcaption (optional)
category: [Knowledge,Algorithms]
tags: [Algorithms,QuickSort]
---

### 들어가며
빨리 빨리 퀵정렬(**QuickSort**)의 정의, 구현, 예시, 시간복잡도에 대해 알아보자.(퀵정렬이다보니 intro는 짧게~)

<br>

### 퀵정렬(**QuickSort**) 정의
- **<ins>배열의 원소중 피벗(Pivot)이라는 기준을 정해 큰값은 오른쪽, 작은값은 왼쪽으로 나누어 정렬하는 알고리즘</ins>**이다. 이때 좌우측 두 부분리스트의 크기는 **비균등**하게 나누어질 수 있으며, 분할된 두 리스트를 정렬한다음 서로 합하여 정렬한다. 
- 기본적으로 퀵정렬은 **분할 정복** 개념을 이용하여 정렬한다.
    - **분할(Divide)**: 피벗(**Pivot**)을 기준으로 비균등한 두개의 부분리스트로 분할한다.(왼쪽은 피벗보다 작은값, 오른쪽은 피벗보다 큰값)
    - **정복(Conquer)**: 분할된 두 리스트를 정렬시킨다. 이때 두 부분리스트의 크기가 크다면 순환호출(**Recursion**)을 이용해 다시 분할정복 시킨다
    - **결합(Combine)**: 정렬된 두 부분배열을 하나로 결합한다.
**note**: 분할정복에서 순환호출이 될때마다 최소한 1개(Pivot)이 정렬되므로, 퀵정렬의 안정성을 보장한다.

<br>

### 퀵정렬(**QuickSort**) 예시
- 피벗의 값은 처음, 마지막, 중간 혹은 랜덤으로 정할 수 있으나, 편의상 이 글에서는 **처음 값을 피벗**으로 정해보자. 아래 그림은 초기배열 **[4,1,8,2,3,9,6,5,7]**을 퀵정렬을 이용해 **오름차순**으로 정렬하는 예시이다.

![Algorithms-Quick-Sort-Example]({{site.baseurl}}/assets/img/Knowledge/Algorithms/2020-08-24-quicksort/Algorithms-Quick-Sort-Example.png#center)

- **첫번째 순환**
    1. **step1**: 배열의 첫 요소인, **\'4\'**를 피벗으로 설정하고 그 다음 요소인 **\'1\'**을 low 마지막 요소인 **\'7\'**을 high로 지정하였다. 이때 low는 왼쪽에서 오른쪽으로 이동하며 pivot값과 비교해 큰 값을 찾는다.(**high는 그 반대**)
    2. **step2 & 3**: low와 high가 **pivot(\'4\')**보다 큰값(**\'8\'**), 작은값(**\'3\'**)을 찾았다. 그 값을 서로 교환해준다.
    3. **step4**: low와 high가 서로 다른 방향으로 이동하며 **큰값과 작은값을 계속 찾는다**.
    4. **step5**: high의 위치가 low의 위치보다 작아졌다. 즉 **pivot**보다 작은값과 큰 값을 다찾았다는 의미이다. 그래서 high와 pivot을 교환해준다. 
    5. **step6**: pivot이였던 **\'4\'**의 값은 정렬이 된 상태로 배열에 저장된다.

- **두번째 순환**
    - 첫번째 순환에서 사용된 피벗 **\'4\'**의 왼쪽리스트 에는 그것보다 작은값들이, 오른쪽리스트에는 그것도보다 큰값들이 위치해 있다. 이 두 리스트를 첫번째 순환에서 했던것과 마찬가지로 퀵정렬(**Quick Sort**)에 넣어 정렬해준뒤 합하여 배열을 정렬해준다.

<br>

### 퀵정렬(**QuickSort**) 구현
아래는 퀵정렬을 간단하게 **Python**언어를 사용해 구현해보았다.
``` python
def quick_sort(l, start, end):
    '''(list, int, int) -> (int)
    return sorted list using Quicksort algorithms given unsorted list, l
    '''
    if start < end:
        pivot = partition(l, start, end)
        quick_sort(l, start, pivot - 1)
        quick_sort(l, pivot + 1, end)
    return l

def partition(l, start, end):
    '''(list, int, int) -> (int)
    sort given list l that depends on pivot. low is smaller than pivot and high is bigger than pivot
    '''
    pivot = l[start]
    low = start + 1
    high = end
    done = False
    while not done:
        while low <= high and l[low] <= pivot:
            low += 1
        while low <= high and pivot <= l[high]:
            high -= 1
        if high < low:
            done = True
        else:
            l[low], l[high] = l[high], l[low]
    l[start], l[high] = l[high], l[start]
    return high

```

### 퀵정렬(**QuickSort**) 시간 복잡도
: 퀵정렬에서는 **Partition**함수가 부분 리스트를 얼마나 잘 균등하게 나누느냐에 따라 그 시간 복잡도가 상이하게 차이난다.

- **Worst-Case**: 이미 정렬되어 있는 리스트를 정렬할경우(즉, partition함수에 의해 분할되는 리스트가 n번이 반복됨)
    - 순환호출: **n**, (순환호출 깊이가 n이 되므로)
    - 비교연산: **n**, (전체 리스트의 대부분의 레코드를 비교해야하므로)
    - **T(n) = 순환호출 * 비교연산 = n * n = O(n^2)**
- **Best-Case**: partitiong함수가 부분리스트를 대부분 균등하게 분배할때
    - 순환호출: **log(n)**, (순환호출 깊이가 log(n),이진트리구조)
    - 비교연산: **n**, (전체 리스트의 대부분의 레코드를 비교해야하므로)
    - **T(n) = 순환호출 * 비교연산 = log(n) * n = O(nlog(n))**
- **Average: T(n) = O(nlog(n))**

<br>

### 마치며
**공부가 답이다. 빨리 빨리 마치며..**

### reference
[\[Image-of-Algorithms-Quick-Sort-Main/thegear/article\]](https://www.thegear.kr/news/articleView.html?idxno=8592) <br>
[\[General-definition-of-Algorithms-Quick-Sort/geeksforgeeks\]](https://www.geeksforgeeks.org/quick-sort/) <br>
[\[Algorithms-of-Quick-Sort-Examle/interviewbit\]](https://www.interviewbit.com/tutorial/quicksort-algorithm/) <br>
