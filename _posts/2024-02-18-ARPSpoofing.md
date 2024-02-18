---
category: Security
url_path: '/security/arpspoofing'
title: 'ARP Spoofing'
type: 'NORMAL'

layout: null
---

### ARP (주소 결정 프로토콜)

- ARP (주소 결정 프로토콜)은 MAC 주소와 IP 주소를 매칭시키기 위한 프로토콜이다.
- 논리적인 주소(IP address)를 물리적인 주소(MAC address)로 바꾸어주는 주소 해석 프로토콜이다.
- OSI 7 Layer의 2계층과 3계층을 연결하는 역할을 하며, 3계층에 해당하는 프로토콜이다.

### ARP Table

[ARP Table 그림]

- ARP Table은 통신했던 대상의 MAC 주소와 IP 주소가 매칭되어 저장되어있는 테이블이다.
- 컴퓨터는 통신을 시작하기전에 먼저 ARP Table에서 통신하려는 대상의 정보를 찾는다.
- ARP Table에 대상의 정보가 존재하는 경우, 별도의 탐색과정없이 테이블의 정보를 이용해 통신을 시작한다.

### ARP Spoofing

[ARP Spoofing 그림]

- ARP Spoofing은 공격 대상의 ARP Table을 조작하여, 상대의 통신 대상을 속이는 공격 기법이다.
- 공격 대상은 공격자를 통신 대상으로 인식하게 되어, 모든 패킷을 공격자에게 전송하게 된다.
- 이떄, 통신 대상과의 연결이 끊기게 되는데, 공격자는 공격 대상에게 받은 패킷을 확인하고, 원래 통신 대상에게 돌려주는 방식으로 연결이 끊기지 않게 한다.
  
[MITM 그림]

- 이를 MITM(Man in the middle, 중간자)공격이라고 한다.

#### 예제

[ARP Spoofing - arpspoof 그림]
[ARP Spoofing - fragrouter 그림]

#### 진단

[ARP Table 그림]

- ARP Spoofing이 성공하게 되면, 공격대상의 ARP Table이 조작되어 MAC 주소가 중복되어 나타나게 된다.
