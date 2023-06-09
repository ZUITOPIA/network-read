### Chap8. 네트워크 보안을 공부하자 - 바이러스로부터 PC 지키기

### 01. 방화벽이란 무엇일까?

방화벽 : 네트워크의 보안을 확보하기 위한 중요한 기능  
( 네트워크 통신의 데이터는 방화벽에 의해 모두 체크됨)

```
방화벽 - 미리 설정된 조건에 따라 데이터 허가/파기하는 문지기 역할

방화벽 종류 : PC에서 데이터를 체크하는 타입 / 라우터의 기능 일부로써 동작하는 타입

방화벽 전용 장비도 존재함
- PC 상에서 동작하는 방화벽 :'개인 방화벽'이라고 불림
- 대부분의 가정용 브로드밴드 라우터 -> 방화벽 기능 내장되어 있음

```

### 01-1. 다중방어가 중요하다

한 군데뿐만 아니라 여러 군데에서 체크를 함으로써 전체의 보안 레벨을 높임

### 01-2. 방화벽은 완벽하지 않다

방화벽은 설정된 조건에 기초하여 통신을 차단할 뿐, 악의를 가진 유저가 방화벽 입장에서 정상으로 보이는 데이터로 위장시키면 방화벽을 그냥 통화하고 마는 경우가 있을 수 있음

### 01-3. 방화벽의 구조

브로드밴드 라우터의 방화벽은 기본적으로 홈 네트워크에서 개시된 인터넷 통신의 응답만을 허가
=> SPI (Stateful Packet Inspection)

### 01-4. 방화벽이 체크하는 정보

SPI : 통신 상태를 유지하고, 일련의 통신 데이터만 방화벽을 통과시킴, 통신 상태로써 데이터에 추가된 정보 (목적지/송신지 IP 주소, 목적지/송신지 포트 번호, 프로토콜)를 체크함

### 01-5. 인터넷 쪽의 응답 판단 기준

통신 : 쌍방향

과정
LAN 쪽에서 인터넷으로 데이터를 전송하면 인터넷 쪽에서 그 응답이 되돌아옴
(이때 응답 데이터는 IP 주소나 포트 번호의 목적지와 송신지가 서로 바뀌어있음 => 정상적인 응답!)

### 01-6. 기업 네트워크에서의 방화벽

브로드밴드 라우터와 같이, 필요한 통신 데이터만을 허가하여 부정 액세스를 방지함

기업 네트워크의 방화벽 : 반드시 3개 이상의 인터페이스를 상호 연결함

-   사내 네트워크
-   DMZ(DeMilitarized Zone)
-   인터넷 쪽의 네트워크

### 01-7. DoS를 막는 'IPS'

DoS(Denial of Service) : 공개 서버의 다운을 목적으로 대량의 요청을 보내는 공격 수단

DoS를 막기 위해 도입된 IPS(Intrusion Prevention System)
=> 방화벽과 같이 네트워크 상에서 전송되는 데이터를 체크함
=> 단시간에 요청이 반복되거나 비정상적인 요청을 포함한 데이터 등 부정 액세스의 징후를 검출해서 그에 해당하는 통신 차단함

### 02. 멀웨어 방어

### 02-1. 멀웨어란?

멀웨어 : PC나 유저에게 유해한 소프트웨어
대표적인 멀웨어 예시 - 컴퓨터 바이러스, 트로이 목마, 봇, 스파이웨어, 애드웨어 등

### 02-2. 바이러스 탐지 기법

안티바이러스 소프트웨어가 바이러스를 탐지하는 기법 2가지 : 패턴 매칭 / 휴리스틱 분석

패턴 매칭 : 이미 알려진 바이러스의 특징과 PC 상의 파일을 비교하여 바이러스 검출
(바이러스의 특징을 모아놓은 DB는 '정의파일'이나 '시그니처'라고 불림)

휴리스틱 분석 : 알려지지 않은 바이러스를 검출하기 위한 것, 수상한 동작을 하는 프로그램을 바이러스로 검출함

### 03. 공개 키가 뭐지?

### 03-1-1. 암호화의 개요

데이터 암호화 : 데이터 도청이나 변조를 방지하기 위해 이용하는 것

암호화 : 암호 키를 사용하여 평문을 암호문으로 바꾸는 것
복호화 : 암호문을 원래의 평문으로 바꾸는 것

암호화되지 않은 데이터 - 평문
암호화 된 데이터 - 암호문

암호 키 : 특별히 의미를 가지지 않는 데이터

### 3-1-2. 암호화 방식

(1) 대칭 키 암호 방식

-   암호화와 복호화에 같은 암호 키를 사용하는 방식 (그래서 공통 키 암호 방식이라고 부르기도 함)

(2) 공개 키 암호 방식

-   암호화와 복호화에 서로 다른 암호 키를 사용하는 방식 (그래서 비대칭 키 암호 방식이라고 부르기도 함)
-   키 페어를 만듦

### 03-2. 디지털 서명과 인증서

디지털 서명

-   공개 키 암호 방식을 사용할 때 데이터의 변조 여부와 데이터 송신자를 확인하기 위해서 사용되는 것
-   송신자가 데이터를 송신할 때에는 데이터뿐만 아니라 디지털 서명(데이터로 계산한 해시 값'을 송신자의 비밀 키로 암호화한 것)을 추가함

인증서 : 공개 키가 확실히 '진짜'라는 것을 증명하는 역할

인증기관 (CA)

-   인증서 안에 공개 키가 들어있으며 공개 키가 '진짜'라고 보증해 줌
-   대표적 인증기관 서비스를 제공하는 기업 : GeoTrust, Cyber Trust, Versign
-   인증기관 끼리는 서로를 신뢰하며 '인증서 체인'을 구성함
-   신뢰받는 인증 기관이 발행한 증명서를 이용한 시스템 기반 => PKI(Public Key Infrastructure)

### 03-3. SSL이 뭐지?

SSL(Secure Socket Layer)에 의한 암호 통신

-   인증서를 체크해서 통신 상대가 위장되지 않았는지 확인하고, 데이터를 암호화하여 안전한 통신을 수행하는 시스템
