## HTTP 헤더
> field-name: OWS field-value OWS
- 필드 네임은 대소문자 구분 없음.
### 용도
- HTTP 전송에 필요한 모든 부가정보
  - 메시지 바디의 내용, 메시지 바디의 크기, 압축, 인증, 요청 클라이언트, 서버 정보 등등
### Representation
- representation Metadata + Representation Data
- 표현 = 표현 메타데이터 + 표현 데이터
- 메시지 본문을 통해 표현 데이터 전달
- 메시지 본문 = payload
- 표현은 요청이나 응답에서 전달할 실제 데이터.
- `표현 헤더`는 표현 데이터를 해석할 수 있는 정보 제공.
  - 데이터 유형, 데이터 길이, 압축 정보 등등
- 표현 헤더는 표현 메타데이터와, 페이로드 메시지를 구분해야 하지만 일단 생략.
------------------
### 표현 해더
> 표현 헤더는 전송, 응답 둘다 사용
- `Content-Type:` 표현 데이터의 형식 설명
    - 미디어 타입, 문자 인코딩
      - text/html; charset=utf-8
      - application/jason
      - image/png
- `Content-Encoding` : 표현 데이터의 압축 방식 (인코딩)
  - 표현 데이터를 압축하기 위해 사용
  - 데이터를 전달하는 곳에서 압축 후 인코딩 헤더 추가
  - 데이터를 읽는 쪽에서 인코딩 헤더의 정보로 압축 해제
    - gzip
    - deflate
    - identity
- `Content-Language` : 표현 데이터의 자연 언어
  - 표현 데이터의 자연 언어를 표현
    - ko
    - en
    - en-US
- `Content-Length`: 표현 데이터의 길이
  - 바이트 단위
  - Transfer-Encoding(전송 코딩)을 사용하면 Content-Length를 사용하면 안됨.

----------
## 협상 (Contents negotiation)
> 협상 헤더는 요청시에만 사용
- 클라이언트가 선호하는 표현 요청
- `Accept:` 클라이언트가 선호하는 미디어 타입 전달
- `Accept-Charset:` 클라이언트가 선호하는 문자 인코딩
- `Accept-Encoding:` 클라이언트가 선호하는 압축 인코딩
- `Accept-Language:` 클라이언트가 선호하는 자연 언어
### 협상과 우선순위 1(Quality Values(q))
- q값을 사용
- 0~1, 클수록 높은 우선순위
- 생략하면 1
- Accept-Language: ko-KR,ko;q=0.9,en-US;q=0.8;q=0.7
  - ko-KR;q=1(q 생략)
  - ko;q=0.9
  - en-US;q=0.8
  - en;q=0.7
### 협상과 우선순위 2
- 구체적인 것이 우선한다.
- Accept: text/*, text/plain, text/plain;format=flowed, */*
  - text/plain;format=flowed
  - text/plain
  - text/*
  -   */*
  
### 협상과 우선순위 3
- 구체적인 것을 기준으로 미디어 타입을 맞춘다.
----------
## 전송 방식
- 단순 전송(Content-Length: 123) : 한 번에 요청하고 한 번에 응답하는 방식.
- 압축 전송(Content-Encoding: gzip) : 요청을 받으면 압축해서 응답을 보냄.
- 분할 전송(Transfer-Encoding: chunked) :요청받은 것을 분할에서 보내줌.
- 범위 전송(Content-Range: bytes 1001-2000/2000): 범위를 지정해서 요청한것을 그 범위를 응답함.

--------
## 일반 정보
- `From`: 유저 에이전트의 이메일 정보
  - 일반적으로 잘 사용되지 않음
  - 검색 엔진 같은 곳에서, 주로 사용
  - 요청에서 사용
- `Referer` : 이전 웹 페이지 주소
  - 현재 요청된 페이지의 이전 웹 페이지 주소
  - A -> B로 이동하는 경우 B를 요청할 때 Referer: A를 포함해서 요청
  - Referer를 사용해서 유입 경로 분석 가능
  - 요청에서 사용
  - referrer의 오타이다.
- `User-Agent`
  - 유저 에이전트(클라이언트) 애플리케이션 정보
  - 클라이언트의 애플리케이션 정보(웹 브라우저 정보 등등)
  - 통계 정보
  - 어떤 종류의 브라우저에서 장애가 발생하는지 파악 가능
  - 요청에서 사용
- `Server`
  - 요청을 처리하는 origin 서버(여러 서버를 거치지만 응답을 주는 서버)의 소프트웨어 정보
    - Server: Apache/2.2.22(Debian)
    - Sercer: nginx
  - 응답에서 사용
- Date
  - 메시지 발생한 날짜와 시간
  - 응답에서 사용
--------
## 특별한 정보
- `Host`
  - 요청한 호스트 정보(도메인)
  - 필수
  - 하나의 서버가 여러 도메인을 처리해야 할 때
    - 가상호스트를 통해 여러 도메인을 한 번에 처리할 수 있는 서버에서 Host를 붙여서 보내면 도메인을 찾을 수 있다.
  - 하나의 IP 주소에 여러 도메인이 적용되어 있을 때
- `Location`
  - 페이지 리다이렉션
  - 웹 브라우저는 3xx 응답의 결과에 Location 헤더가 있으면, Location 위치로 자동 이동
  - 201(Created): 이 때 Location 값은 요청에 의해 생성된 리소스 URI이다.
  - 3xx(Redirection) :  이 때 Location 값은 요청을 자동으로 리다이렉션하기 위한 대상 리소스를 가리킴.
- `Allow`
  - 허용 가능한 HTTP 메서드
  - 405(Method Not Allowed)에서 응답에 포함해야 함.
    - Allow: GET, HEAD, PUT
- `Retry-After`
  - 유저의 에이전트가 다음 요청을 하기까지 기다려야 하는 시간
  - 503(Service Unavailable): 서비스가 언제까지 불능인지 알려줄 수 있음.
    - Retry-After : ~~ 날짜 표기
    - Retry-After : 120(초단위 표기)
--------
## 인증
- `Authorization`
  - 클라이언트 인증 정보를 서버에 전달
    - Authorization: Basic xxxxxxxxxxx 이런 식으로 나옴.
- `WWW-Authenticate`
  - 리소스 접근시 필요한 인증 방법 정의
  - 401 Unauthorized 응답과 함께 사용
---------
## 쿠키
- `Set-Cookie` : 서버에서 클라이언트로 쿠키 전달(응답에서)
- `Cookie` : 클라이언트가 서버에서 받은 쿠키를 저장하고, HTTP 요청시 서버로 전달
### 쿠키 미사용
> 로그인 정보를 기억을 못함.
- Statelss 상황
  - HTTP는 무상태 프로토콜이다.
  - 클라이언트와 서버가 요청과 응답을 주고 받으면 연결이 끊어진다.
  - 클라이언트가 다시 요청하면 서버는 이전 요청을 기억하지 못한다.
  - 클라이언트와 서버는 서로 유지 상태를 유지한다.
- 대안
  - 모든 요청에 정보를 넘긴다??
    - 모든 요청에 사용자 정보가 포함되도록 개발해야함.
    - 브라우저를 완전히 종료하고 다시 열면? 어떻게 할껀데?
### 쿠키를 사용
- 클라이언트에서 보낸 정보를 서버가 쿠키로 전달
- 클라이언트는 쿠키를 쿠키 저장소에 저장한다.
- 클라이언트는 쿠키 저장소에서 조회하여 쿠키를 서버에 보낸다.
- 모든 요청에 쿠키 정보 자동 포함.
### 특징
- 쿠키 사용처
  - 사용자 로그인 세션 관리
  - 광고 정보 트레킹
- 쿠키 정보는 항상 서버에 전송됨
  - 네트워크 트래픽 추가 유발
  - 최소한의 정보만 사용(sessionID,인증 토큰)
  - 서버에 전송하지 않고, 웹 브라우저 내부에 데이터를 저장하고 싶으면 웹 스토리지 참고
- 민감한 데이터는 저장하면 안됨.
### 쿠키 - 생명주기
> `Expires`, `max-age`
- Set-Cookie: expires=Sat,23~~
  - 만료일이 되면 쿠키 삭제
- Set-Cookie: max-age=3600(초)
  - 0이나 음수를 지정하면 쿠키 삭제
- 세션 쿠키 : 만료 날짜를 생략하면 브라우저 종료시 까지만 유지
- 영속 쿠키 : 만료 날짜를 입력하면 해당 날짜까지 유지
### 쿠키 - 도메인
> `Domain`
- 명시: 명시한 문서 기준 도메인 + 서브 도메인 포함
  - domain=example.org를 지정해서 쿠키 생성
  - example.org는 물론 dev.example.org도 쿠키 접근
- 생략: 현재 문서 기준 도메인만 적용
  - example.org에서 쿠키를 생성하고 domain 지정을 생략
    - example.org에서만 쿠키 접근
    - dev.example.org는 쿠키 미접근
 ### 쿠키- 경로
> `Path`
- 경로를 포함한 하위 경로 페이지만 쿠키 접근
- 일반적으로 path=/ 루트로 지정
  - path=/home
    - /home 가능
    - /home/level1 가능
    - /home/level1/level2 가능
    - /hello -> 불가능
### 쿠키 - 보안
> `Secure`, `HttpOnly` `SameSite`
- Secure
  - 쿠키는 http, https를 구분하지 않고 전송
  - Secure를 적용하면 https인 경우에만 전송
- HttpOnly
  - XSS 공격 방지
  - 자바스크립트에서 접근 불가
  - HTTP 전송에만 사용
- SameSite
  - XSRF 공격 방지
  - 요청 도메인과 쿠키에 설정된 도메인이 같은 경우만 쿠키 전송.