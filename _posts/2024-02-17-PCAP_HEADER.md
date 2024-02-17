---
category: Network
url_path: '/network/pcap_header'
title: 'PCAP Header'
type: 'EASY'

layout: null
---

### PCAP 설명

- tcpdump, wireshark 와 같은 네트워킹 툴로 패킷을 캡쳐하면 확장자가 .pcap인 파일을 얻을 수 있다.
- .pcap파일은 네트워크 상에 송,수신되는 패킷들을 캡쳐하여 모아놓은 파일이다.

-----------------------------------------------------------------------------------------
### 데이터의 Header와 Trailer ([MissingNo]추후 카빙 설명으로 이동예정)

- 우리가 사용하는 프로그램 그리고 저장공간에 존재하는 모든 데이터는 각각의 Header와 Trailer가 존재한다.
- Header란, 데이터의 시작부분에 존재하는 것으로, 데이터를 구분하기위한 식별자와 데이터의 메타데이터로 이루어져 있다.
- Trailer란, 데이터의 끝부분에 존재하는 것으로, 저장공간에서 해당 데이터가 점유한 공간의 마지막공간을 나타낸다.
- Header부터 Trailer까지를 하나의 데이터로 구분한다.
-----------------------------------------------------------------------------------------

### PCAP Header

- .pcap파일의 헤더는 global header와 packet header 두가지로 구분된다.
- 모든 필드는 little endian으로 해석한다.

#### Global Header

[Global Header 그림]

- .pcap파일의 헤더로 파일의 가장 앞부분에 존재한다.

##### Global Header 구조

[Magic Number 그림]

- Magic Number
  - Global Header 첫 4bytes는 Magic Number이다.
  - Libpcap의 경우, D4 C3 B2 A1 으로 이루어져있다.

[Version 그림]

- Major, Minor Version
  - 2bytes의 Major Version 과 2bytes의 Minor Version으로 이루어져있다.

[thiszone 그림]

- thiszone
  - 4bytes의 thiszone 필드가 존재한다.

[sigfigs 그림]

- sigfigs
  - 4bytes의 sigfigs 필드가 존재한다.

[snaplen 그림]

- snaplen
  - 4bytes의 snaplen 필드가 존재한다.
  - 실제 수집된 패킷의 길이를 의미한다.

[network 그림]

- network
  - 4bytes의 network 필드가 존재한다.
  - datalink type을 의미하며, ethernet type은 01 00 00 00 이다.

#### Packet Header

[Packet Header 그림]

- .pcap파일 내의 각 패킷들의 Header이다.
- 패킷의 가장 앞부분에 존재한다.

##### Packet Header 구조

[ts_sec 그림]

- 4bytes의 ts_sec 필드가 존재한다.
- 해당 패킷을 캡쳐한 시간(Unix Time)의 정수부분을 16진수로 표기한다.

[ts_usec 그림]

- 4bytes의 ts_usec 필드가 존재한다.
- 해당 패킷을 캡쳐한 시간(Unix Time)의 소수점부분을 16진수로 표기한다.

[incl_len 그림]

- 4bytes의 incl_len 필드가 존재한다.
- 캡쳐한 패킷의 전체 길이를 의미한다.

[orig_len 그림]

- 4bytes의 orig_len 필드가 존재한다.
- 패킷의 실제 길이를 의미한다.

[Global Header와 Packet Header, Payload, Packet Header, Payload ... 그림]

- 따라서 전체적인 구조는 위와 같은 형태를 띈다.
