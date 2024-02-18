---
category: Network
url_path: '/network/byteorder'
title: 'BYTE ORDER'
type: 'NORMAL'

layout: null
---

### 바이트 저장 순서(byte order)

- 컴퓨터가 데이터를 메모리에 저장할 때, 데이터를 byte단위로 나누어 저장하게 된다.
- 일반적으로 32bits(4bytes)나 64bits(8bytes) 단위로 쓰게 되는데, 이렇게 연속되는 바이트를 순서대로 저장하는 방법을 바이트 저장 순서(byte order)라 한다.
- 마이크로프로세서(CPU)에 따라 byte order가 결정된다.

#### 빅 엔디안(big endian)

- 빅 엔디안 방식은 낮은 주소에 데이터의 높은 값을 저장하는 방식이다.
- 평소에 사용하는 선형 구조와 같은 방식으로, 메모리의 데이터값을 그대로 읽을 수 있는 장점이 있다.
- SPARC를 포함한 RISC CPU 계열에서는 이 방식으로 데이터를 저장한다.

#### 리틀 엔디안(little endian)

- 리틀 엔디안 방식은 낮은 주소에 데이터의 낮은 값을 저장하는 방식이다.
- 평소에 사용하는 선형 구조에서 반대로 읽어야 한다.
- 인텔 CPU 계열에서 이 방식으로 데이터를 저장한다.

#### 예제

- 32bits에 저장된 16(decimal)값을 big endian byte order와 little endian byte order로 변환한다.
- 16(decimal)의 16진수 값은 0x10이다.

##### big endian 예제

- 0x00 0x00 0x00 0x10
  - 0 + 0 + 0 + 16 = 16이 된다.
 
##### little endian 예제

- 0x10 0x00 0x00 0x00
- -> 0x00 0x00 0x00 0x10 (반대로 읽음)
  - 0 + 0 + 0 + 16 = 16이 된다.

### 네트워크 바이트 저장 순서 (network byte order)

- 네트워크에서는 big endian 방식을 사용한다.
- 따라서 자신의 cpu가 little endian을 사용하는 경우, byte order를 big endian으로 변환해야 한다.
- 혹은 big endian을 사용하더라도 stable한 코드를 위해 network byte order로 변환하는 방식으로 코딩하는 것이 안전하다.
- 일반적으로는 hton (host to network)함수를 사용하는 것을 권장한다.
