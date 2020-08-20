---
layout: post
title: Greedy Algorithm
date: 2020-08-13 00:00:00 +0300
description:  # Add post description (optional)
img: Knowledge/Algorithms/2020-08-13/greedy_algorithm_main.jpg # Add image post (optional)
fig-caption: # Add figcaption (optional)
category: [Knowledge,Algorithms]
tags: [Algorithm, Greedy] # add tag
---

### 들어가며
알고리즘 중에 기본이라고 할 수 있는 ***Greedy Algorithm***. 이글을 통해 알고리즘의 정의, 사용법 그리고 예시를 알아보자.

<br>

### Greedy Algorithm 정의
***Greedy Algorithm***은 단어 뜻에서도 알 수 있듯이 탐욕적인 방식으로 문제를 풀어나가는 알고리즘이다. <ins>***단순 미래를 생각하지 않고 당장 지금 최적의 해를 구해 전체적인 답***</ins>을 구하는 것이다. 하지만 인생이 그러하듯 순간 순간 최선이라고 생각했던 답이 향후 최고의 답만을 항상 내어 놓진 않는다. 간단한 예로, 마시멜로 실험을 들어보자. 실제 1970년대 스탠포드에서 어린이들을 대상으로 하나의 마시멜로를 주고 15분을 기다리면 하나를 더 주겠다는 실험이다. 순간의 탐욕을 절제하면 추가로 하나의 마시멜로를 더 얻지만, 대부분의 아이들은 눈앞에 놓인 마시멜로를 입에 넣으며 미소를 짓는다. 15분을 기다리면 2개를 얻을 수 있음에도 불구하고..

그러면 ***Greedy Algorithm*** 을 언제 사용 할 수 있을까? 최적의 답을 구하기위해 ***Greedy Algorithm***은 <ins>**두 가지 조건**</ins>을 만족하는 문제를 풀때 유용하게 쓸 수 있다.
- **선택 조건**(_greedy choice property_): 이전의 선택이 이후의 선택에 영향을 주지 않는다.
- **최적 부분 구조 조건**(_optimal substructure_): 부분문제의 최적의 답이 전체문제의 최적의 답가 된다.

이러한 조건들을 만족하는 예시들은 대표적으로 앞서 본 마시멜로, 거스름돈 문제(_Exchange Problem_), AI 결정트리 학습법(_Decision Tree Learning_), 최소 신장트리(_Minimum Spanning Tree_), 다익스트라 알고리즘이 있다.

**Note**: 추가적으로 위의 2가지 조건을 만족하지 않더라도 ***Greedy Algorithm***은 근사 알고리즘으로 사용 할 수 있으며, 대부분의 경우 계산 속도가 빠르기 때문에 실용적으로 사용이 가능하다.

<br>


### Greedy Algorithm 예시

#### 거스름돈 문제(Exchange Problem)

![Greedy-Algoritm-Coins]({{site.baseurl}}/assets/img/Knowledge/Algorithms/2020-08-13/greedy-algorithm-coins.jpg#center)

***Greedy Algorithm***을 사용하여 최소 개수로 거스름돈 동전들을 반환하는 알고리즘을 작성해보자. 5000원의 현금이 있고, 3800어치의 물건을 샀다고 가정할때 받아야 하는 거스름돈은 1200이다. 당연한 소리지만 큰 단위 동전으로 받는것이 거스름돈 동전의 개수를 최소한으로 줄일 수 있는 방법이다. 이 경우 500원짜리 동전으로 최대한 거스름돈을 받을 수 있을만큼 받고, 나머지는 그 다음 단위인 100원짜리 동전으로 채운다. 이런식으로 50원 10원 동전들로 거스름돈이 남아있는 경우에 반복이 가능하다.

그렇다면 거스름돈 문제를 풀 수 있는 ***Greedy Algorithm***을 **Python**으로 간단하게 구현해보자.
```python

def minCoins(change):
 '''(int, list) -> dict
 return minumum number of coins for the given amount of change
 '''
 answer = {}
 change_val = change
 coins = [500,100,50,10]

 if change_val < 0:
   print("Change can't be negative value")
   return 0
 else:
   for i in range(len(coins)):
     if change_val%coins[i] == 0 and change_val != 0:
       answer[coins[i]] = int(change_val/coins[i])
       change_val -= (change_val/coins[i]) * coins[i]
    for key, value in answer.items():
     print(change,"에 대한 잔돈은", key,"원짜리 동전:",value,"개가 필요하다")
 return 0
```
<br>

### 마치며
실제로 ***Greedy Algorithm***은 간단한 예시를 제외하고는 그 자체로 쓰이기 보단 다른 문제들과 함께 사용되는 경우가 많다. 그리고 ***Greedy Algorithm***하면 항상 따라오는게 ***Dynamic Programming***인데, 이것에 관한 자료는 ***Knowledge - Algorithm***에 있는 포스트를 참고하여 공부하자.

### reference
[\[Definition-of-Algorithm/wiki\]](https://en.wikipedia.org/wiki/Greedy_algorithm) <br>
[\[Definistion-of-Algorithm/ratsgo's-blog\]](https://ratsgo.github.io/data%20structure&algorithm/2017/11/22/greedy/) <br>
[\[Examples-of-Greedy-Algorithm/namu-wiki\]](https://namu.wiki/w/%EA%B7%B8%EB%A6%AC%EB%94%94%20%EC%95%8C%EA%B3%A0%EB%A6%AC%EC%A6%98) <br>
[\[Picture-of-Coins/google-image\]](https://www.google.com/imgres?imgurl=https%3A%2F%2Fimages-wixmp-ed30a86b8c4ca887773594c2.wixmp.com%2Ff%2Fe32041bf-889e-41f6-a291-4f6b2a1bd922%2Fd7o4o12-31442d94-7f9b-43cb-acfd-8bad81c61953.jpg%3Ftoken%3DeyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJzdWIiOiJ1cm46YXBwOiIsImlzcyI6InVybjphcHA6Iiwib2JqIjpbW3sicGF0aCI6IlwvZlwvZTMyMDQxYmYtODg5ZS00MWY2LWEyOTEtNGY2YjJhMWJkOTIyXC9kN280bzEyLTMxNDQyZDk0LTdmOWItNDNjYi1hY2ZkLThiYWQ4MWM2MTk1My5qcGcifV1dLCJhdWQiOlsidXJuOnNlcnZpY2U6ZmlsZS5kb3dubG9hZCJdfQ.MYnWR4aCQsWIp2eqEzrKpdVs_Kn8jFUUlUujBI2cEAA&imgrefurl=https%3A%2F%2Fwww.deviantart.com%2Ftidalkraken%2Fart%2FPretty-pretty-coin-coins-463791782&tbnid=2kuMhY__D7XXhM&vet=12ahUKEwjW18DTl5frAhVF35QKHWEBC7kQMygDegUIARCvAQ..i&docid=SeUkYl4bwUPz3M&w=1920&h=1421&itg=1&q=pretty%20coins&ved=2ahUKEwjW18DTl5frAhVF35QKHWEBC7kQMygDegUIARCvAQ) <br>
[\[Greedy-Algorithm-Marshmellow-pics/therockstaracademy\]](https://www.therockstaracademy.com/blog/marshmallow) <br>

