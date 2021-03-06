# 면접대비

> 면접용 CS 스터디
>
> 면접에서 자주 나오는 CS 질문을 유형별로 정리

<br>

## 네트워크

### 1. GET / POST 방식의 차이

http 프로토콜에서 데이터를 서버에 요청하는 방식으로 대표적인 것이 get과 post방식이다.

GET

- 클라이언트에서 서버로 어떠한 리소스로부터 정보를 요청하기 위해 사용하는 메서드

- url 주소에 데이터를 파라미터로 담아 전송 (쿼리 스트링)
- 쿼리 문자열에 포함되어 전송되므로 길이제한 존재
- 주소에 정보가 다 드러나기 때문에 보안상 취약
- 캐시됨, 브라우저 히스토리에 남음



POST

- 클라이언트에서 서버로 리소스를 생성하거나 업데이트하기 위해 데이터를 보낼때 사용하는 메서드
- HTTP 메시지 body 부분에 담아서 서버로 보냄
- 길이제한 X
- GET보다는 보안상 나음
- 캐시안됨, 브라우저 히스토리에 남지 않음

<br>

### 2. HTTP와 프로토콜에 대해 설명해보세요

- Hyper Text Transfer Protocol의 약자
- 인터넷에서 데이터를 주고 받을 수 있는 프로토콜
- 프로토콜은 컴퓨터와 같은 원거리 장비간에 메시지를 주고 받기 위해 지켜야하는 일종의 규약

<br>

### 3. HTTP는 비연결성/연결성 프로토콜?

- 비연결성 프로토콜
- Request에 대한 reponse가 전달 되면 연결을 끊음

<br>

### 4. 그럼 비연결성을 해결할 방법은? (이를테면 로그인하면 계속 상태를 유지하기 위해 사용하는 방식)

- 쿠키와 세션
  - 쿠키에 클라이언트에 대한 정보를 저장해뒀다가 사용
  - 세션을 등록해서 유지하는 방식

- 세션 스토리지와 로컬 스토리지
  - HTML5에서 제공
  - 세션스토리지는 세션이 유지되고 있을 때 까지는 브라우저 내부 스토리지에 저장을 하고 세션이 끊키면 자동 삭제
  - 로컬 스토리지 같은 경우는 사용자나 프론트엔드 내부적으로 삭제를 하지 않는 이상 영구적으로 저장

<br>

### 5. 아까 GET방식은 캐시된다고 했는데 캐시는 뭔가?

Cache란 자주 사용하는 데이터나 값을 미리 복사해 놓는 임시 장소를 가리킨다. 아래와 같은 저장공간 계층 구조에서 확인할 수 있듯이, 캐시는 저장 공간이 작고 비용이 비싼 대신 빠른 성능을 제공한다. 

<br>

### 6. 그럼 브라우저 캐시는 뭔가?

**1. Browser Caches**

- 브라우저 또는 HTTP요청을 하는 클라이언트에 의해 내부 디스크에 캐시

- 캐시된 Resource를 공유하지 않는 한 개인에 한정

- 사용 예시
  - 브라우저의 Back버튼
  - 이미 방문한 페이지를 재방문할 때



<br>

### 2. 스위치/라우터 차이

스위치

- 데이터링크 계층
- 단순 경로연결

라우터

- 네트워크 계층
- 별도 테이블 존재. 포워딩



### CORS에 대해 설명해주세요

CORS **출처가 다른 리소스도 공유할 수 있도록 하는 정책**을 말합니다.보안상의 이유로 원칙적으로는 오직 출처가 동일한 리소스만 공유할 수 있습니다.

Cross-Origin Resource Sharing(CORS) 은 추가 HTTP 헤더를 사용하여 브라우저가 한 출처에서 실행중인 웹 애플리케이션에 선택된 액세스 권한을 부여하도록하는 메커니즘입니다. 다른 출처의 자원. 웹 응용 프로그램은 자체와 다른 출처 (도메인, 프로토콜 또는 포트)를 가진 리소스를 요청할 때 cross-origin HTTP 요을 실행합니다

<br>

- TCP와 UDP의 차이가 무엇인가요?

  > TCP는 신뢰성 통신 프로토콜이고 UDP는 비신뢰성 통신 프로토콜입니다.

- HTTP와 HTTPS의 차이는 무엇인가요?

  > HTTP는 하이퍼 텍스트를 위한 통신 규약이고 여기에 정보를 암호화 하기위해 SSL을 사용한 것이 HTTPS입니다. 인증기관으로부터 공개키를 저장한 인증서 발급을 요청함으로써 보안을 높입니다.

- 로드밸런싱이 무엇인가요?

  > 서버에 가해지는 부하를 분산해주는 기술입니다. 대표적인 로드 밸런싱 알고리즘으로 라운드로빈이 있습니다.

- 프로토콜은 무엇인가요?

  > 데이터 통신을 원활하게 하기 위한 규악입니다.

- 쿠키와 세션을 사용하는 이유와 차이점을 말해보세요

  > HTTP는 요청에 대한 응답이 오면 연결을 끊고 상태를 유지하지 않는 특징이 있는데, 이를 보완 하기 위해 쿠키와 세션을 사용합니다. 쿠키는 클라이언트 로컬에 저장되고 세션은 서버에서 관리한다는 차이점이 있습니다.

- RESTful이란 무엇인가요?

  > REST API의 규칙을 올바르게 지킨 시스템을 RESTful 하다고 합니다. REST란 HTTP URI를 통해 자원을 명시하고 HTTP Method를 통해 CRUD 동작을 하는 것을 의미합니다. REST API란 REST의 원리를 따르는 API를 의미합니다.

- 프록시 서버가 무엇인가요?

  > 서버와 클라이언트 사이에서 통신을 수행해주는 서버를 의미합니다. 캐시 데이터를 사용하거나 보안, 접속 우회를 위해 사용됩니다.

- 주소창에 URL을 적었을 때 과정을 말해주세요

  > 브라우저가 URL을 해석하고 DNS를 조회하여 IP 주소를 찾게됩니다. 그 다음 라우터를 통해 해당 서버의 게이트웨이로 이동하여 MAC주소로 변환하고 TCP 통신을 통해 소켓을 열고 HTTP 요청을 하게 됩니다.

- URL과 URI의 차이가 무엇인가요?

  > URL은 자원의 위치로 자원을 식별하는 방식이고 URI는 URL의 상위 개념으로 자원 식별자를 뜻합니다.

- Public IP와 Private IP의 차이는 무엇인가요?

  > 공인 IP는 ISP에서 할당하는 IP 주소로 인터넷 상에서 사용할 수 있습니다. 사설 IP는 IPv4의 주소 부족으로인해 서브넷팅된 IP주소로 라우터에 의해 로컬 내트워크에 할당됩니다.











