## HTTP(HyperText Transfer Protocol)
- HTTP 메시지에 모든 것을 전송
  - HTML, TEXT
  - image, 음성, 영상, 파일
  - JASON, XML(API)
  - 거의 모든 형태의 데이터 전송 가능
  - 서버간에 데이터를 주고 받을 때도 대부분 HTTP 사용
- HTTP/1.1을 가장 많이 사용한다. 이 이후는 성능을 개선한 것.
  - 기반 프로토콜
    - TCP : HTTP/1.1, HTTP/2
    - UDP : HTTP/3
    - 현재 HTTP/1.1 주로 사용
  
## 특징
- 클라이언트 서버 구조
  - request response 구조
  - 클라이언트 서버에 요청을 보내고, 응답을 대기
  - 서버가 요청에 대한 결과를 만들어서 응답 
------
## 무상태 프로토콜(Stateless)
  - Stateful, Stateless 차이 
    - `stateful` : 서버가 클라이언트의 이전 상태를 보존(문맥보존).
      - 서버가 바뀌면 상태 정보를 서버에게 미리 알려줘야함.
    - `stateless` : 서버가 클라이언트의 상태를 보존하지 않음. 
      - 중간에 다른 서버로 바뀌어도 된다.
      - 갑자기 클라이언트가 증가해도 서버를 대거 투입할 수 있다.
      - 무상태는 응답 서버를 쉽게 바꿀 수 있다.
      - 스케일 아웃(서버 수평 확장)에 유리하다.
### stateless 한계
  - 모든 것을 무상태로 설계할 수 있는 경우도 있고 없는 경우도 있다.
  - 단순한 서비스 소개 화면 같은 경우 무상태로 가능하다.
  - 로그인 같은 경우는 서버가 상태를 유지하고 있어야 한다.(서버가 끊기면 로그인이 끊기도록)
  - 일반적으로 브라우저 쿠키와 서버 세션 등을 사용해서 상태 유지
  - 상태 유지는 최소한만 하는 것이 좋음.
  - 전송하는 데이터가 많아진다.

## 비 연결성(Connectionless)

       1. 연결을 유지하는 모델
         - 클라이언트마다 서버 연결을 계속 유지하면서 서버 자원이 소모된다.
       2. 연결을 유지하지 않는 모델 
         - 서버는 연결 유지를 하지 않고 최소한의 자원을 유지한다.
- HTTP는 기본이 연결을 유지하지 않는 모델
- 일반적으로 초 단위 이하의 빠른 속도로 응담
- 실제로 서버에서 동시에 처리하는 요청은 수십개 이하로 매우 작음
- 서버 자원을 효율적으로 사용가능하다.

### 비 연결성 한계와 극복
- TCP/IP 연결을 새로 맺어야 함 - 3 way handshake 시간 추가
- 웹 브라우저로 사이트를 요청하면 HTML뿐 아니라 자바스크립트,css,추가 이미지 등 수 많은 자원이 함께 다운로드 됨.
- 지금은 HTTP 지속 연결(persistent Connections)로 문제 해결(몇십 초간 연결을 유지)
------
## HTTP 메시지
### HTTP 메시지 구조
| start line  |
|-------------|
| header      |
| 공백          |
| message body |

#### - 시작 라인(start-line)
- 요청 메시지(request-line) : method SP request-target SP HTTP-version CRLF(엔터)
> GET /search?q=hello&hl=ko HTTP/1.1
  - HTTP 메서드 : 서버가 수행해야 할 동작 지정
    - GET, POST, PUT, DELETE
  - 요청 대상(request-target)  : 절대 경로[?query]
  - HTTP 버전 : HTTP:1.1, HTTP/2 등
- 응답 메시지(status-line) : `HTTP-version SP status-code SP reason-phrase CRLF`
> HTTP/1.1 200 OK
  - HTTP 버전
  - HTTP 상태 코드
    - 200 : 성공
    - 400 : 클라이언트 요청 오류
    - 500 : 서버 내부 오류
  - 이유 문구 : 사람이 이해할 수 있는 짧은 상태 코드 설명 글.

#### - 헤더(header)
- header-field : `field-name":" OWS(띄어쓰기 허용) field-value OWS`
>Content-Type(여기는 붙여써야함): text/html...
    - field-name은 대소문자 구분 없음
- 용도
  - HTTP 전송에 필요한 모든 부가 정보
    - 바디의 내용, 메시지 바디의 크기, 압축, 인증 등등
#### - 메시지 바디(message body)
- 실제 전송할 데이터
- HTML 문서, 이미지 등등 byte로 표현할 수 있는 모든 데이터 전송 가능.