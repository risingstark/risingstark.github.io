---
layout: post
title: Operating System - 4. System Call
date: 2020-10-08 00:00:00 +0300
description:  # Add post description (optional)
img:  Knowledge/Operating_System/2020-10-08-system-call/Operating_System_Main.jpg
fig-caption: # Add figcaption (optional)
category: [Knowledge,Operating System]
tags: [Operating System,System Call]
---

### 1. 들어가며
운영체제에는 2가지 모드인 커널모드(Kernal Mode)와 유저모드(User Mode)가 존재한다고 배웠다. 프로세스를 운영체제가 직접적으로 관리 및 사용하는 방식을 이 글을 통해 알아보자.

<br>

### 2. 시스템 호출(System Call)이란?
: **시스템 호출(system call)은 운영 체제의 커널이 제공하는 서비스에 대해, 응용 프로그램의 요청에 따라 커널에 접근하기 위한 인터페이스이다. 즉 응용프로그램에서 커널의 서비스를 이용하는 방법**이 시스템 호출이다. 여기서 C나 C++과 같은 고급 언어로 작성된 프로그램들은 직접 시스템 호출을 사용할 수 없기 때문에 고급 API를 통해 시스템 호출에 접근하는 방식을 사용한다. 
- 운영체제는 프로세스의 실행, 종료나 I/O 작업 등의 사용자가 함부로 사용하면 문제가 될 만한 명령들을 Privileged Instruction으로 분류하여 막아놓았다. 따라서 사용자들이 이와 같은 기능을 사용하기 위해서는 OS가 제공하는 System Call을 사용하여야 한다.

![Operating-System-Example-of-System-Call]({{site.baseurl}}/assets/img/Knowledge/Operating_System/2020-10-08-system-call/Operating-System-Example-of-System-Call.png
#center)

### 3. 시스템 호출(System Call)의 종류

#### 3.1 프로세서 제어(process Control)
- 끝내기(end), 중지(abort)
- 적재(load), 실행(execute)
- 프로세스 생성(create process)
- 프로세스 속성 획득과 설정(get process attribute and set process attribute)
- 시간 대기(wait time)
- 사건 대기(wait event)
- 사건을 알림(signal event)
- 메모리 할당 및 해제 : malloc, free

#### 3.2 파일 조작(file manipulation)
- 파일 생성(create file), 파일 삭제(delete file)
- 열기(open), 닫기(close)
- 읽기(read), 쓰기(write), 위치 변경(reposition)
- 파일 속성 획득 및 설정(get file attribute and set file attribute)

#### 3.3 장치 관리(Device Management)
- 장치를 요구(request devices), 장치를 방출release device)
- 읽기, 쓰기, 위치 변경
- 장치 속성 획득, 장치 속성 설정
- 장치의 논리적 부착(attach) 또는 분리(detach)

#### 3.4 정보 유지(Information maintenance)
- 시간과 날짜의 설정과 획득(time)
- 시스템 데이터의 설정과 획득(date)
- 프로세스 파일, 장치 속성의 획득 및 설정

#### 3.4 통신(Communication)
- 통신 연결의 생성, 제거
- 메시지의 송신, 수신
- 상태 정보 전달
- 원격 장치의 부착 및 분리

<br>

### 4. 시스템콜 예시(Window ans Unix)
![Algorithms-Quick-Sort-Example]({{site.baseurl}}/assets/img/Knowledge/Operating_System/2020-10-08-system-call/Operating-System-Example-of-Windows-and-Unix-System-Calls.png
#center)

<br>

### reference
[\[Image-of-Operating-System-Main/Komando\]](https://www.komando.com/downloads/zorin-os-alternative-to-windows-and-apple/535834/) <br>
[\[Image-of-System-Call-Example/guru99\]](https://www.guru99.com/system-call-operating-system.html) <br>
[\[Image-of-System-Call-Window-Unix-Example/Geeksforgeeks\]](https://www.geeksforgeeks.org/introduction-of-system-call/#:~:text=A%20system%20call%20is%20a,Application%20Program%20Interface(API).) <br>
[\[General-Definition-of-System-Call/wiki\]](https://ko.wikipedia.org/wiki/%EC%8B%9C%EC%8A%A4%ED%85%9C_%ED%98%B8%EC%B6%9C#:~:text=%EC%8B%9C%EC%8A%A4%ED%85%9C%20%ED%98%B8%EC%B6%9C(system%20call)%EC%9D%80,%EC%A0%91%EA%B7%BC%ED%95%98%EA%B8%B0%20%EC%9C%84%ED%95%9C%20%EC%9D%B8%ED%84%B0%ED%8E%98%EC%9D%B4%EC%8A%A4%EC%9D%B4%EB%8B%A4.) <br>
[\[Operating-System-System-Call-Classification/tistory/luckyouwu\]](https://luckyyowu.tistory.com/133) <br>
