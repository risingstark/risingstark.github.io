---
layout: post
title: Operating System - 3. Scheduling
date: 2020-09-29 00:00:00 +0300
description:  # Add post description (optional)
img:  Knowledge/Operating_System/2020-09-29-process-scheduling/Operating_System_Main.jpg
fig-caption: # Add figcaption (optional)
category: [Knowledge,Operating System]
tags: [Operating System, Process, Scheduling, Preemptive, Non-preemptive]
---

### 1. 들어가며
우리가 필요로하는 자원은 너무나도 한정적이다. 이러한 자원을 효율절으로 사용하고 관리하는것이 비용절감 뿐만 아니라 작업의 속도를 증가시키고, 향후 일어날 문제를 예방하기도 한다. 이 글에서는 컴퓨터의 자원에 해당하는 CPU가 프로세스에 할당되고 반환되는 알고리즘, 기법 및 목적등에 대해 알아보자.

<br>

### 2. Process Scheduling 정의
: **<ins>프로세스가 생성되어 실행될때 필요한 시스템의 여러자원을 해당 프로세스에게 할당하는 작업을 의미</ins>**한다. 프로세스는 생성부터 작업이 끝날때까지 여러 종류의 스케줄링 과정을 거치게 되는데, 그 이유는 **대기 시간을 최소화 하고 최대한 공평하게 처리하는 것을 목적**으로하기 때문이다. 메모리에 여러개의 프로세스를 올려놓고(=**다중 프로그래밍**), CPU의 가동시간을 적절히 나누어(=**시분할**) 각각의 프로세스에게 분배하여 실행되도록한다.  

<br>

### 3. Process Scheduling 유형

- **3.1 장기 (Long-term scheduling)**
    - 어떤 프로세스가 시스템의 자원을 차지할 수 있도록 할 것인가를 결정하여 아래 준비(ready) 상태 큐로 보내는 작업을 의미한다.
    - 상위 스케줄링이라고도 하며, 작업 스케줄러에 의해 수행된다.
    - 수행 빈도 적고, 느리다.
- **3.2 중기 (middle-term scheduling)**
    - 어떤 프로세스들이 CPU를 할당 받을 것인지 결정하는 작업을 의미한다.
    - CPU를 할당받으려는 프로세스가 많을 경우 프로세스를 일시 대기(waiting)시킨 후 활성화해서 일시적으로 부하를 조절한다.
    - 스왑 인/아웃 결정 (메모리 부족 시 swap out, 남으면 swap in) 한다.
- **3.3 단기 (Short-term scheduling)**
    - 프로세스가 실행되기 위해 CPU를 할당받는 시기와 특정 프로세스를 지정하는 작업을 의미한다.
    - 프로세서 스케줄링, 하위 스케줄링이라고도 한다.
    - 프로세서 스케줄링 및 문맥 교환은 프로세서 스케줄러에 의해 수행한다.
    - 자주 수행되고 빠르다

![Operating-System-Process-Scheduling-Type-Example]({{site.baseurl}}/assets/img/Knowledge/Operating_System/2020-09-29-process-scheduling/Operating-System-Process-Scheduling-Type-Example.png#center)

- **스케줄링 결정 시점**
: **<ins>CPU 스케줄링의 결정 시점은 다음과 같은 프로세스의 상태 변화가 있을 때이다</ins>**.
    - **수행 → 대기(비선점)**, 예) **I/O Request**
    - **수행 → 준비(선점)**, 예) **Response to an interrupt**
    - **대기 → 준비(선점)**, 예) **I/O의 completion**
    - **수행 → 종료(비선점)**

<br>

### 4. Process Scheduling 기법 종류

- **4.1 비선점(Non-preemptive) 스케줄링**
: **이미 할당된 CPU를 다른 프로세스가 강제로 빼앗아 사용할 수 없는 스케줄링 기법**이다. 프로세스가 CPU를 할당받으면 해당 프로세스가 완료될 때까지 CPU를 사용한다. 일괄 처리 방식의 스케줄링이라고 부른다.(공정하지만 긴급 응답을 요하는 작업에 좋지 않다.)
<br>
    - **FCFS(First Come First Service)** : 준비상태 큐에 도착한 순서에 따라 CPU를 할당하는 기법으로 공평성은 유지되지만 짧은 작업이 긴 작업 혹은 중요한 작업이 중요하지 않은 작업을 기다리게 되는 단점이 있다.
    - **SJF(Shortest Job First)** : 실행시간이 가장 짧은 프로세스에 먼저 CPU를 할당하는 기법으로 가장 적은 평균 대기 시간을 제공하는 최적 알고리즘이다.
    - **HRN(Highest Response ratio)** : 실행 시간이 긴 프로세스에 불리한 SJF기법을 보완하기 위한 것으로 우선순위 계산 결과 값이 높은 것부터 우선순위가 부여된다. 대기 시간이 길수록 계산 결과가 높다. (대기시간 + 서비스시간 / 서비스시간)
    - **기한부(DeadLine)** : 프로세스에게 일정한 시간을 주어 그 시간 안에 프로세스를 완료하도록 하는 기법이다.
    - **우선순위(Priority)** : 준비상태 큐에서 기다리는 각 프로세스마다 우선순위를 부여하여 그 중 가장 높은 프로세스에게 먼저 CPU를 할당하는 기법이다.

- **4.2 선점(Preemptive) 스케줄링**
: **<ins>하나의 프로세스가 CPU를 할당받아 실행 하고 있을 때 우선순위가 높은 프로세스가 CPU를 강제로 빼앗아 사용할 수 있는 스케줄링 기법이</ins>**다. 선점으로 인한 많은 **오버헤드가 발생할 우려**가 있으며 **시분할 시스템에 사용하는 스케줄링**이다.(긴급을 요하는 우선순위를 갖는 시분할 처리, 실시간 처리에 유용) 선점을 위해 시간 배당을 위한 **인터럽트용 타이머 클럭(Clock)**이 필요하다.
<br>
    - **SRT(Shortest Remaining Time)** : 현재 실행 중인 프로세스의 남은 시간과 대기 큐에 프로세스의 실행시간이 가장 짧은 프로세스에게 CPU를 할당하는 기법이다.(비선점 기법인 SJF 알고리즘의 선점 형태로 변경한 기법)
    - **선점 우선순위** : 준비상태 큐의 프로세스들 중에서 우선순위가 가장 높은 프로세스에게 먼저 CPU를 할당하는 기법이다.
    - **RR(Round Robin)** : 시분할 시스템을 위해 고안된 방법으로, FCFS 알고리즘을 선점 형태로 변형한 기법이다. 대기 큐를 사용하여 먼저 대기한 작업이 먼저 CPU를 사용한다. CPU를 사용할 수 있는 시간(Quantum)동안 CPU를 사용한 후에 다시 대기 큐의 가장되로 배치된다. 할당되는 시간이 클 경우 FCFS 기법과 같아지고, 시간이 작을 경우 문맥교환 및 오버헤드가 자주 발생되는 단점이 있다.
    - **다단계 큐** : 프로세스를 특정 그룹으로 분류할 수 있는 경우 그룹에 따라 각기 다른 준비상태 큐를 사용한다.
    - **다단계 피드백 큐** : 특정 그룹의 준비상태 큐에 들어간 프로세스가 다른 준비상태 큐로 이동할 수 없는 다단계 큐 기법을 준비상태 큐 사이를 이동할 수 있도록 개선한 기법이다.

<br>

### 5. 마치며
그놈의 효율적인 알고리즘... 효율적인것만 찾다가 이기적으로 변하고 머리털 다 빠지겠네...

<br>

### reference
[\[Image-of-Operating-System-Main/Komando\]](https://www.komando.com/downloads/zorin-os-alternative-to-windows-and-apple/535834/) <br>
[\[Image-of-Process-Scheduling-Type-Example/tistory/junsday\]](https://junsday.tistory.com/28) <br>
[\[Definition-of-Process-Scheduling/tistory/eastroot1590\]](https://eastroot1590.tistory.com/entry/%ED%94%84%EB%A1%9C%EC%84%B8%EC%8A%A4-%EC%8A%A4%EC%BC%80%EC%A4%84%EB%A7%81-%EB%B0%A9%EC%8B%9D%EC%9D%98-%EC%A2%85%EB%A5%98) <br>
[\[Process-Scheduling-Type-Example/velog/hax0r\]](https://velog.io/@hax0r/%EC%84%A0%EC%A0%90%EB%B9%84%EC%84%A0%EC%A0%90-%ED%94%84%EB%A1%9C%EC%84%B8%EC%8A%A4-%EC%8A%A4%EC%BC%80%EC%A4%84%EB%A7%81) <br>
[\[Definition-of-Process-Scheduling-preemptive-Non-Preemptive\]](https://sangcho.tistory.com/entry/%ED%94%84%EB%A1%9C%EC%84%B8%EC%8A%A4%EC%8A%A4%EC%BC%80%EC%A4%84%EB%A7%81) <br>
