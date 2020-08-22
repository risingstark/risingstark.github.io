---
layout: post
title: 선택정렬(SelectionSort)
date: 2020-08-20 00:00:00 +0300
description:  # Add post description (optional)
img:  Knowledge/Algorithms/2020-08-21-selectionsort/Algorithms-SelectionSort-Main.jpg
fig-caption: # Add figcaption (optional)
category: [Knowledge,Algorithms]
tags: [Algorithms,SelectionSort]
---

### 들어가며
그리스의 한 철학자는 말했다. **\"순간 순간의 선택이 우리의 인생을 구성하는 요소들이다\"**라고. 주어진 환경에 선택만 잘하면 좋은 결과를 얻을 수 있다. 선택 정렬은 어떤 선택을 하는지, 정렬을 어떠한 방식으로 하는지 이 글을 통해 알아보자. 

<br>

### 선택정렬(SelectionSort) 정의
<ins>**요소가 들어갈 자리는 이미 정해져 있고, 그 자리에 들어갈 요소를 찾아 선택하여 옮기는 알고리즘**</ins>이다. 오름차순으로 정렬할 경우, **첫번째 자리**에 들어갈 요소는 주어진 Input 배열에서 **제일 작은 요소**이다. 그래서 제일 작은 요소를 **2번째**부터 **n번째**에 있는 요소중에 찾아 첫번째에 있는 요소와 교환한다. 그러면 첫번째 자리에 제일 작은 요소가 존재하기때문에 그 자리는 정렬이 완료 된것이다. 이것을 **n-1번째까지 반복**해주면 주어진 배열은 정렬이 된다.

- 간단하게 순서로 정리하자면(**오름차순**),
    1. 제일 작은 요소가 들어올 **위치**를 기억한다.
    2. 제일 작은 요소를 배열에서 **찾고** 1.에서 기억하는 위치로 **교환**한다.
    3. 첫번째 요소는 **정렬**이 되었다. 그 요소를 뺀 **나머지 요소들을 같은방법**으로 정렬한다.

<br>

### 선택정렬(SelectionSort) 예시

![Algorithms-Selection-Sort-Example]({{site.baseurl}}/assets/img/Knowledge/Algorithms/2020-08-21-selectionsort/Algorithms-Selection-Sort-Example.jpg#center)

위 그림은 정렬되지 않은 배열, **[8,5,7,1,9,3]**을 선택정렬 알고리즘을 이용해 **오름차순**으로 정렬하는 예시이다. 

<span style="color:Green">*초록색*</span>은 정렬되지 않은 요소들 중 제일 작은 값이 들어갈 위치를 나타낸다.<br>
<span style="color:Red">*빨간색*</span>은 정렬되지 않은 요소들 중 제일 작은 값을 나타낸다.<br>
<span style="color:Blue">*파란색*</span>은 정렬이 된 요소들을 나타낸다.<br>

- **첫번째 줄**
    - 첫번째 자리가 제일 작은 요소가 들어갈 장소이다. <span style="color:Green">*\'8\'이 위치한 자리*</span><br>
    - 첫번째 자리에 들어갈 제일 작은 요소를 찾는다  <span style="color:Red">*\'1\'이 제일 작다*</span><br>
<br>
- **두번째 줄**
    - 첫번째 자리에 제일 작은 값인 \'1\'이 선택되어 교환되었다. <span style="color:Blue">*\'1\'은 정렬이 끝났다*</span>
<br>
    - 첫번째 자리는 정렬이 되었으니 그 다음 두번째 자리를 정렬할 차례이다.<span style="color:Green">*\'5\'가 위치한 자리*</span><br>
    - 정렬되지 않은 요소들 중 제일 작은 값을 찾는다  <span style="color:Red">*\'3\'이 제일 작다*</span><br> 
    ...

이러한 방식으로 계속 진행되어 주어진 초기 배열, **[8,5,7,1,9,3]**이 선택 알고리즘에 의하여 **[1,3,5,7,8,9]**로 정렬이 된다.

<br>

### 시간 복잡도(Time Complexity) & 공간 복잡도(Space Complexity)
구현이 간단한만큼 시간복잡도와 공간복잡도 역시 간단하다. 시간 복잡도는 크게 두가지로 나눌 수 있는데, **비교연산**과 **교환연산**이 걸리는 시간이다.

- **시간 복잡도**
    - **Worst-case**: **O(n^2) 비교연산, O(n) 교환연산**
    - **Best-case**: **O(n^2) 비교연산, O(n) 교환연산**
    - **Average-case**: **O(n^2) 비교연산, O(n) 교환연산**
- **공간 복잡도**:
    - **O(1)** : 배열에서 제일 작은 값을 찾아 그 값만 임시 Variable에 저장시켜 주면 되므로

위의 시간복잡도와 공간복잡도가 이해가 가지 않는다면 선택정렬의 **정의와 원리, 예시**를 다시 한번 보고 이해를 잘 해보자.

**note**: <ins>**선택정렬은 버블정렬과 함께 O(n^2)의 시간복잡도를 가지고 있다. 하지만 실제로는 버블정렬보다 훨씬 더 빠른 속도를 보여준다. 그이유는 버블정렬은 교환연산이 O(n^2)이지만 선택정렬은 O(n)이기 때문이다.**</ins> 

<br>

### 선택정렬(SelctionSort) 구현

아래는 선택정렬 알고리즘을 간단하게 **Python**으로 구현해보았다.

``` python
def selectionSort(l):
    '''(list) -> (list)
    return an ordered list using selectionSort algorithm given the unordered list
    '''

    # iterate from 1 to n-1
    for i in range(len(l)-1):
        # select where the minimum value will be located
        min_spot = i
        # find smallest value by comparing elements
        for j in range(i+1,len(l)):
            if l[j] < l[min_spot]:
                min_spot = j
        # change element
        l[i],l[min_spot] = l[min_spot],l[i]
    return l
```

<br>

### 마치며
선택정렬, 버블정렬, 삽입정렬은 항상 같이 붙어 다닌다. 서로의 장단점들을 잘 파악하고 설명할 줄 안다면 도움이 훨씬 될것이다. 기본적이니 만큼 꼭 숙지하고 기억하자.

<br>

### reference
[\[Image-of-Algorithms-SelectionSort-Main/google-img \]](https://www.google.com/imgres?imgurl=https%3A%2F%2Fcdn.elearningindustry.com%2Fwp-content%2Fuploads%2F2018%2F11%2F4-tips-to-select-the-right-course-management-system-for-your-training-company-1024x574.jpg&imgrefurl=http%3A%2F%2Fhspads.com%2F833157%2FSelect%2F&tbnid=64F4o2MyqhRbBM&vet=12ahUKEwjQhv_P1anrAhWZIqYKHfhnC9MQMygHegUIARC9AQ..i&docid=CxRxbwg1tnHFPM&w=1024&h=574&itg=1&q=select&ved=2ahUKEwjQhv_P1anrAhWZIqYKHfhnC9MQMygHegUIARC9AQ) <br>
[\[Image-of-SelectionSort-Example/it-swarm/ko \]](https://www.it-swarm.dev/ko/algorithm/%EC%82%BD%EC%9E%85-%EC%A0%95%EB%A0%AC-%EB%B0%8F-%EC%84%A0%ED%83%9D-%EC%A0%95%EB%A0%AC/1072484338/) <br>
