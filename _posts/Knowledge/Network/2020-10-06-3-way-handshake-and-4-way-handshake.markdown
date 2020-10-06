---
layout: post
title: Network - 4. 3-way-handshake and 4-way-handshake
date: 2020-10-06 00:00:00 +0300
description:  # Add post description (optional)
img:  Knowledge/Network/2020-10-06-3-way-handshake-and-4-way-handshake/Network-Main.jpg
fig-caption: # Add figcaption (optional)
category: [Knowledge,Network]
tags: [Network,TCP,3 way handshake,4 way handshake]
---

### 들어가며
네트워크 TCP/IP 글에서 TCP에 대해 알아보았다. 연결 지향성 프로토콜인 TCP가 어떤 방식으로 연결되고 종료되는지 이 글을 통해 알아보자.

<br>

###  1. 3-way-handshake
: TCP 통신을 이용하여 데이터를 전송하기 위해 네트워크 연결을 설정(Connection Establish) 하는 과정이다. 자세히 설명하자면, <ins>**TCP/IP프로토콜을 이용해서 통신을 하는 응용프로그램이 데이터를 전송하기 전에 먼저 정확한 전송을 보장하기 위해 상대방 컴퓨터와 사전에 세션을 수립하는 과정**</ins>을 의미한다.

- 안전한 연결을 구축해 양쪽 모두 데이터를 전송할 준비가 되었다는 것을 보장한다.
- 실제로 데이터 전달이 시작하기 전에 한 쪽이 다른 쪽이 준비되었다는 것을 알 수 있도록 한다.

![3-Way-Handshake-Example]({{site.baseurl}}/assets/img/Knowledge/Network/2020-10-06-3-way-handshake-and-4-way-handshake/3-Way-Handshake-Example.png#center)

1. **<ins>Client -> Server: SYN</ins>**
- 접속 요청 프로세스 Client가 연결 요청 패킷(SYN)을 Server에 전송한다.
- 송신자(Client)가 최초로 데이터를 전송할 때 Sequence Number를 임의의 랜덤 숫자로 지정하고, SYN 플래그 비트를 1로 설정한 세그먼트를 전송한다. 예) Seq = 10, SYN
- ***PORT 상태 - Server: LISTEN, Client: CLOSED***
2. **<ins>Server -> Client: SYN + ACK</ins>**
- 접속 요청을 받은 Server가 요청을 수락했으며, 접속 요청 Client도 포트를 열어 달라는 패킷(SYN + ACK)을 Client에 전송한다.
- 수신자(Client)는 Acknowledgement Number 필드를 (Sequence Number + 1)로 지정하고, SYN과 ACK 플래그 비트를 1로 설정한 세그먼트를 전송한다. 예) Seq = 50, ACK = 11, SYN,ACK
- ***PORT 상태 - Server: SYN_RCV, Client: CLOSED***
3. **<ins>Client -> Server: ACK</ins>**
- ***PORT 상태 - Server: SYN_RCV, Client: ESTABLISHED***
- 마지막으로 접속 요청 Client가 수락 확인을 보내 연결을 맺음 (ACK)
- 이때, 전송할 데이터가 있으면 이 단계에서 데이터를 전송할 수 있다.
- ***PORT 상태 - Server: ESTABLISHED, Client: ESTABLISHED***

<br>

### 2. 4-way-handshake
: **4-way-handshake는 TCP간의 안전한 세션 종료를 위한 과정**이다.
![4-Way-Handshake-Example]({{site.baseurl}}/assets/img/Knowledge/Network/2020-10-06-3-way-handshake-and-4-way-handshake/4-Way-Handshake-Example.jpeg#center)

Note: **Client와 Server가 서로 안정적으로 연결되어 있는 상태**이어야한다.
1. **Client -> Server: FIN**
- Client가 연결을 종료하겠다는 FIN 플래그를 전송한다.
- Server가 FIN 플래그로 응답하기 전까지 연결을 계속 유지한다.
2. **Server -> Client: ACK**
- Server는 일단 확인 메시지를 보내고 자신의 통신이 끝날 때까지 기다린다.(상태: TIME_WAIT)
- 수신자는 Acknowledgement Number 필드를 (Sequence Number + 1)로 지정하고, ACK 플래그 비트를 1로 설정한 세그먼트를 전송한다. 그리고 자신이 전송할 데이터가 남아있다면 이어서 계속 전송한다.
3. **Server -> Client: FIN**
- Server가 통신이 끝났으면 연결 종료 요청에 합의한다는 의미로 Client에게 FIN 플래그를 전송한다.
4. **Client -> Server: ACK**
- Client는 확인했다는 메시지를 전송한다.

<br>

### 3. TCP Header 안의 플래그 정보
- TCP Header에는 **CONTROL BIT(플래그 비트, 6bit)**가 존재하며, 각각의 bit는 **“URG-ACK-PSH-RST-SYN-FIN”**의 의미를 가진다.
    - 해당 위치의 bit가 1이면 해당 패킷이 어떠한 내용을 담고 있는 패킷인지를 나타낸다.
- **SYN(Synchronize Sequence Number)**
    - 연결 설정 / **000010**
    - Sequence Number를 랜덤으로 설정하여 세션을 연결하는 데 사용하며, 초기에 Sequence Number를 전송한다.
- **ACK(Acknowledgement)**
    - 응답 확인 / **010000**
    - 패킷을 받았다는 것을 의미한다.
    - Acknowledgement Number 필드가 유효한지를 나타낸다.
    - 양단 프로세스가 쉬지 않고 데이터를 전송한다고 가정하면 최초 연결 설정 과정에서 전송되는 첫 번째 세그먼트를 제외한 모든 세그먼트의 ACK 비트는 1로 지정된다고 생각할 수 있다.
- **FIN(Finish)**
    - 연결 해제 / **000001**
    - 세션 연결을 종료시킬 때 사용되며, 더 이상 전송할 데이터가 없음을 의미한다.

<br>

### reference
[\[Image-of-Network-Main/google-Image\]](https://www.google.com/search?q=network&tbm=isch&ved=2ahUKEwiRnpWb2L3rAhUNeZQKHYM9B14Q2-cCegQIABAA&oq=network&gs_lcp=CgNpbWcQAzIECAAQQzIECAAQQzICCAAyAggAMgQIABBDMgIIADICCAAyAggAMgIIADICCAA6BwgjEOoCECc6BQgAELEDOgQIABAYOgQIIxAnUILiD1jO-A9g5PkPaAVwAHgAgAF8iAHxCJIBBDAuMTCYAQCgAQGqAQtnd3Mtd2l6LWltZ7ABCsABAQ&sclient=img&ei=StxIX5HRNI3y0QSD-5zwBQ&bih=665&biw=1280#imgrc=EuzZ19pRAo0S5M&imgdii=aARG9gSlFAM_VM) <br>
[\[Image-of-3-Way-Handshake/guru99\]](https://www.guru99.com/tcp-3-way-handshake.html) <br>
[\[Image-of-4-Way-Handshake/tistory/real-dongsoo7\]](https://real-dongsoo7.tistory.com/73) <br>
[\[General-Idea-of-3-Way-Handshake-and-4-Way-Handshake/tistory/needjarvis\]](https://needjarvis.tistory.com/157) <br>
[\[3-Way-Handshake-and-4-Way-Handshake-Steps\]](https://gmlwjd9405.github.io/2018/09/19/tcp-connection.html) <br>
