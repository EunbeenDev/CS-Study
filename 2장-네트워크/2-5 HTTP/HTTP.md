## HTTP 발전 과정

HTTP(HyperText Transfer Protocol)는  
웹에서 클라이언트와 서버 간의 통신을 담당하는 **응용 계층 프로토콜**로,  
웹 환경의 변화에 따라 지속적으로 발전해왔다.

---

### 1. HTTP/1.0
- 최초의 HTTP 버전
- 기능
  - 단순한 `GET` 요청만 지원
- 특징
  - 요청/응답에 헤더가 없음
  - HTML 문서만 전송 가능
- 한계
  - 확장성과 기능이 매우 제한적
  - 요청마다 새로운 연결이 필요하여 **RTT(Round Trip Time) 증가 문제 발생**

- RTT 증가 문제
  - 리소스(이미지, 스크립트 등)를 개별 요청으로 받아야 함
  - 요청 횟수 증가로 인해 응답 지연 발생

- RTT 증가 문제 해결 방법
  - **이미지 스플리팅(Image Splitting)**  
    여러 이미지를 하나로 합쳐 요청 수 감소
  - **코드 압축(Code Minification)**  
    HTML, CSS, JavaScript 코드 용량을 줄여 전송 시간 단축
  - **이미지 Base64 인코딩**  
    이미지를 텍스트 형태로 변환하여 HTML/CSS에 포함  
    → 추가 HTTP 요청 제거


### 2. HTTP/1.1
- 현재까지도 널리 사용되는 표준
- 주요 개선 사항
  - **Persistent Connection(Keep-Alive)** 기본 지원  
    → 하나의 TCP 연결을 재사용하여 RTT 감소
  - 파이프라이닝(Pipelining) 도입  
    → 여러 요청을 연속으로 전송 가능
  - Host 헤더 필수화  
    → 하나의 IP에서 여러 도메인을 서비스하는 가상 호스팅 가능

- 문제점
  - **Head-of-Line Blocking (HOL Blocking)**  
    하나의 요청이 지연되면 이후 요청들도 함께 지연됨
  - 요청과 응답이 **순차적으로 처리**되어 병렬 처리 한계 존재
  - **무거운 헤더 구조**  
    매 요청마다 동일한 헤더 정보가 반복 전송되어 오버헤드 발생

---

### 3. HTTP/2 (2015)
- 성능 개선에 초점
- 주요 특징
    - **멀티플렉싱(Multiplexing)** 지원 - 여러 개의 스트림을 사용해 송수신
    - 헤더 압축(HPACK)
    - 바이너리(Binary) 프로토콜
    - 서버 푸시(Server Push)
- 장점
    - HOL Blocking 문제 완화
- 한계
    - 여전히 **TCP 기반**, TCP 레벨 HOL Blocking 존재

---

### 4. HTTP/3
- 차세대 HTTP 프로토콜
- 주요 특징
    - **QUIC 프로토콜 기반 (UDP 사용)**
    - TCP Handshake 제거
    - 연결 지연 감소
- 장점
    - TCP HOL Blocking 완전 해결
    - 모바일 환경에서 성능 우수
- 특징
    - 보안(TLS 1.3) 기본 내장

