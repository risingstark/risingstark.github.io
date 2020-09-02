---
layout: post
title: 운영체제(Operating System)
date: 2020-09-01 00:00:00 +0300
description:  # Add post description (optional)
img:  Knowledge/Operating_System/2020-09-01-operating-system/Operating_System_Main.jpg
fig-caption: # Add figcaption (optional)
category: [Knowledge,Operating System]
tags: [Operating System]
---

### 1. 들어가며
컴퓨터의 발전 속도는 우주의 팽창속도를 따라가듯 기세를 모르고 발전을 해왔다. 인텔의 고든 무어가 주장한 무어의 법칙은 반도체의 집적회로 성능이 18개월마다 2배로 증가한다는 법칙인데, 실제 2005년에는 120MB였던 MicroSD card가 2014년엔 120GB의 변화가 이를 뒷받침한다. 이는 컴퓨터의 성능이 일정 시기마다 기하급수적으로 향상된다는 뜻이기도 하다. 이러한 발전이 삶의 질을 향상하고 인류의 발전을 이끌어왔으며, 현대에서 컴퓨터는 필수이자 없어서는 안 될 물건이다. 필자는 컴퓨터 전공이라 기본적인 개념에 대해서는 다 알고 있다. 하지만 현대인이라면 누구나 다 컴퓨터를 알고 배워야 한다고 생각한다. 그렇다면 컴퓨터 내부가 어떻게 관리되고 구성되어 있는지 알아보자.

<br>

### 2. 운영체제(Operating System) 정의

: **<ins>운영 체제(Operating System)는 컴퓨터 자원(Hardwar & Software)을 효율적으로 관리하기 위한 사용자 친화적 소프트웨어 시스템</ins>**이다. 즉, 컴퓨터의 성능(Performance)을 높이고, 사용자의 편의 제공을 목적으로 설계된 컴퓨터 관리 프로그램이다.

- **컴퓨터의 물리적인 자원(Physical Resource)**
: CPU, Memory, Disk, Terminal, Network 등의 시스템틀 구성하는 요소들과 장치
- **컴퓨터의 추상적인 자원(Abstract Resource)**
: Task, Segment, Page, File, Protocol, Packet등 운영체제가 물리적 자원을 관리하기 위해 추상화 시킨 객체

![Operating-System-Example]({{site.baseurl}}/assets/img/Knowledge/Operating_System/2020-09-01-operating-system/Operating_System_Example.jpg#center)

<br>

### 3. 운영체제(Operating System) 구성 및 기능
- **프로세스 관리(process management)**: 프로세스를 생성하고 실행을 제어,관리하는 기능들을 의미한다.
- **메인 메모리 관리(memory management)**: 프로세스가 실행될 수 있도록 메인 메모리 공간을 할당하고 회수하는 일을 의미한다.
- **파일 관리(file management)**: 파일을 보조기억장치에 저장하고 파일시스템을 운영하는 기능들 집합이다.
- **입출력 관리(I/O management)**: 컴퓨터 시스템에서의 입력과 출력을 관리하는 기능들 집합이다.
- **보조기억장치 관리(secondary storage management)**: 하드 디스크와 같은 보조기억장치의 공간을 할당하고 관리하는 기능들을 말한다.
- **네트워킹(Networking)**: 컴퓨터 통신에 필요한 제어 관리 기능들의 집합이다.
- **정보 보안 관리(Security)**: 사용자 인증 및 실행권한 관리에 대한 것이다.
- **명령해석시스템(command interpreter system)**: 운영체제에 주는 사용자 명령을 해석하고 관련 함수를 실행 시키는 기능들이다

<br>

### 4. 운영체제(Operating System) 운영 기법
- #### 4.1 싱글태스킹 운영 체제 / 멀티태스킹 운영 체제
    : 싱글 태스킹 운영 체제는 한번에 오직 하나의 프로그램만 실행할 수 있으나 멀티태스킹 운영 체제는 하나 이상의 프로그램이 동시에 실행할 수 있게 한다. 이는 운영 체제의 작업 스케줄링 하부 시스템에 의해 제각기 반복적으로 인터럽트 처리되는 여러 프로세스 사이에서 이용 가능한 프로세서 시간을 쪼개는 시분할을 통해 이루어진다. 멀티태스킹의 경우 선점형과 협동형(비선점형)이 있다. 선점형 멀티태스킹의 경우 운영 체제는 CPU 시간을 쪼개어 프로그램들 각각에 슬롯을 할당해준다. 

- #### 4.2 단일 사용자 운영 체제 / 다중 사용자 운영 체제
    : 단일 사용자 운영 체제는 사용자 구별이 없으나 여러 프로그램이 나란히 실행하는 것은 허용한다. 다중 사용자 운영 체제는 디스크 공간과 같은 리소스와 프로세스를 식별하는 기능을 갖춘 멀티태스킹의 기본 개념을 확장하며, 여러 사용자에 속해 있으면서 여러 사용자가 동시에 시스템과 상호 작용할 수 있게 한다. 시분할 운영 체제들은 시스템의 효율적인 이용을 위해 태스크를 스케줄링하며, 프로세서 시간, 기억 공간, 인쇄, 기타 자원을 여러 사용자에게 비용적으로 할당하기 위한 회계 소프트웨어를 포함할 수 있다.

- #### 4.3 분산 운영 체제
    : 분산 운영 체제는 구별된 컴퓨터 그룹을 관리하고 이들이 마치 하나의 컴퓨터인 것처럼 보이게 만들어 준다. 서로 연결되어 통신하는 네트워크화된 컴퓨터들이 개발되면서 분산 컴퓨팅이 활성화되었다. 분산되는 연산들은 하나 이상의 컴퓨터에서 수행된다. 하나의 그룹에 속하는 컴퓨터들이 협업을 할 때 분산 시스템을 형성하게 된다.

- #### 4.4 임베디드 운영 체제
    : 임베디드 운영 체제는 임베디드 컴퓨터 시스템에서 사용할 수 있게 설계되어 있다. PDA처럼 조그마한 기계에 동작하도록 설계되어 있으며 ,제한된 수의 자원으로 동작한다. 매우 크기가 작고 극히 효율적으로 설계되어 있다.

<br>

### 5. 운영체제(Operating System) 종류

![Operating-System-Example]({{site.baseurl}}/assets/img/Knowledge/Operating_System/2020-09-01-operating-system/Operating_System_Type_Example.png#center)
- **유닉스(UNIX)**: 1969년 미국 AT&T의 벨 연구소에 근무하던 켄 톰슨과 데니스 리치가 개발한 오픈소스 기반의 운영체제이다. 유닉스를 기반으로 리눅스, AIX, BSD, 솔라리스, 안드로이드, MAC OS 등 다양한 운영체제가 개발되었다.
    - **리눅스(Linux)**: 기존의 유닉스(Unix) 운영체제를 소형화하여 PC와 서버컴퓨터 등에서 사용하기 위해 만든 운영체제이다. 오픈소스 기반의 무료 소프트웨어이다.
    - **맥 OS(Mac OS)**: 애플이 매킨토시 용으로 개발한 그래픽 사용자 인터페이스 운영 체제이다.
    - **우분투(Ubuntu)**: 남아프리카공화국 출신의 영국인인 마크 셔틀워스가 개발한 오픈소스 기반의 리눅스 운영체제이다. 우분투는 남아프리카의 반투어로 "네가 있기에 내가 있다"는 뜻으로서 '다른 사람에 대한 인간적 배려'를 의미한다. 기존의 데비안을 포크하여 개발했다
- **윈도우(Windows)**: 미국 마이크로소프트 회사가 만든 운영체제이다. '윈도' 또는 '윈도우즈'라고도 한다. 개인 PC 시장의 대부분을 장악했고 서버컴퓨터 시장에서도 상당한 시장을 차지했으나, 스마트폰 시장에서는 안드로이드와 iOS에게 밀려 시장점유율이 매우 낮다.
- **도스(DOS)**: 컴퓨터에서 파일을 읽고 쓰고 복사하고 삭제하는 등의 역할을 수행하는 운영체제이다. 미국 마이크로소프트의 MS-DOS 등의 제품이 있다.

- **스마트폰 운영체제**
    - **안드로이드(Android)**: 2003년 앤디 루빈이 리눅스를 기반으로 만든 오픈소스 운영체제이다. 2005년 구글이 인수하여 전 세계에 무료로 보급하였다. 삼성전자㈜, LG, 화웨이, 샤오미 등 전 세계 스마트폰의 운영체제로 사용되고 있다.
    - **iOS**: 스티브 잡스가 설립한 애플이 개발한 운영체제이다. '아이오에스'라고 읽는다. 아이폰, 아이패드, 아이팟, 애플TV 등에서 사용되고 있다. 2001년 개발 당시에는 OS X(오에스텐)이라고 부르다가 2010년 iOS로 이름을 변경했다.
    - **타이젠(Tizen)**: 삼성전자㈜와 인텔 등이 주도하여 구글의 안드로이드와 애플의 iOS에 대항하기 위해 만든 오픈소스 기반의 운영체제이다. 리눅스를 기반으로 개발했고, 삼성전자㈜의 스마트폰, 스마트 카메라, 스마트워치, 스마트 TV 등에 사용되고 있다.

<br>

### 마치며
갈길이 멀다. 시스템콜, 쓰레드, 프로세스, 스케줄링, 페이징, 가상 메모리 등 운영체제의 내부를 자세히 들여다보면 공부하고 설명할것들이 너무 많다. 이 글에서는 전반적인 운영체제에 대해 설명한것이니 Knowledge 파트의 Operating System 섹션을 참고하여 운영체제 마스터가 되어보자. 
<br>

### reference
[\[Image-of-Operating-System-Main/Komando\]](https://www.komando.com/downloads/zorin-os-alternative-to-windows-and-apple/535834/) <br>
[\[Image-of-Operating-System-Example/tutorialspoint/OS\]](https://www.tutorialspoint.com/operating_system/os_overview.htm) <br>
[\[Image-of-Operating-System-Type-Example/google-image\]](https://www.google.com/search?q=%EC%9A%B4%EC%98%81%EC%B2%B4%EC%A0%9C%EC%A2%85%EB%A5%98&sxsrf=ALeKk00OB_As_w_tfQ-jpABLfxDwQk1UTA:1599012409547&source=lnms&tbm=isch&sa=X&ved=2ahUKEwiD-KW1scnrAhWUdXAKHbkoDoE4ChD8BSgBegQIDBAD&biw=1280&bih=616#imgrc=GBvWC_L3Q0N-pM) <br>
[\[Overview-of-Operating-System/tutorialspoint/OS\]](https://www.tutorialspoint.com/operating_system/os_overview.htm) <br>
[\[Definition-of-Operating-System-General/techterms\]](https://techterms.com/definition/operating_system) <br>
[\[Functions-of-Operating-System-Example/tistory/coding-factory\]](https://coding-factory.tistory.com/300) <br>
[\[Definition-of-Operating-System-Type/hashwiki\]](http://wiki.hash.kr/index.php/%EC%9A%B4%EC%98%81%EC%B2%B4%EC%A0%9C#.EC.A2.85.EB.A5.98) <br>
