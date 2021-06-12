# 쿠키 vs 세션

<br>

### 로그인 인증이 필요한 이유

- Connectionless
  - client와 server가 요청을 한 번씩 주고받으면 연결을 끊어버리는 HTTP 프로토콜의 특성
  - client가 req 요청을 보내면 서버에선 res 응답 후 연결을 끊음
- Stateless
  - 요청, 응답으로 통신이 끝나면 상태정보를 유지하지 않는 HTTP 프로토콜의 특성
  - 페이지 전환 시 상태정보 초기화

위의 두 특징으로 인해 누가 로그인 후 새로운 요청을 보냈을 때 누가 그 요청을 보냈는지에 대한 인증 방법이 필요하다

ex) 로그인 후 예를 들어 상품 구매 버튼을 클릭한다면?

-> 위의 두 HTTP 특성상 상품 구매 버튼을 누른 로그인한 유저가 누군지 알 수 없음

-> 때문에 요청을 보낸 유저가 누구인지 인증하기 위한 방법이 필요

-> 크게 세가지 방법(쿠키, 세션, JWT(Json Web Token))이 있음

<br>

#### 쿠키 vs 세션

|                  | 쿠키                                 | 세션                              |
| ---------------- | ------------------------------------ | --------------------------------- |
| 데이터 저장 위치 | 클라이언트                           | 서버                              |
| 보안 정도        | 낮음                                 | 쿠키보다는 높음                   |
| 인증 유효 시간   | 별도로 설정                          | 클라이언트 종료시 자동 종료       |
| 용도             | 장바구니, 자동로그인 설정            | 로그인 인증, 구매 등              |
| 용량 제한        | 쿠키 용량 제한                       | 용량 제한 X                       |
| 한계             | 쿠키 사이즈가 커질수록 네트워크 부하 | 동시접속자가 많아질수록 서버 부하 |

<br><br>



# JWT(Json Web Token)

`.` 을 구분자로 3가지의 문자열로 구성

![Untitled.png (717×125)](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/2489cf61-3226-4d57-8c3f-79d66942aeac/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210612%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210612T164644Z&X-Amz-Expires=86400&X-Amz-Signature=e461cb2feecfdbc2ba1da7dd783497705815acdd91f23b3279ef24dd0115773c&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)

## 헤더

typ: 토큰의 타입

alg: 해싱 알고리즘 지정

## Payload

실제 보관할 데이터

![Untitled.png (414×259)](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/ac6f112d-01df-46c5-9465-196071a45b21/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210612%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210612T164705Z&X-Amz-Expires=86400&X-Amz-Signature=884e9fb280dd00f65595567e1d4adf215bced01ae4f09aa5c1fa01bd69a47ed8&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)

## Signature

헤더와 페이로드를 조합하고 비밀키를 이용해 해쉬값을 만들어냄.

![Untitled.png (595×226)](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/eb02579c-45f4-49f3-8294-2381cb8c742f/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210612%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210612T164722Z&X-Amz-Expires=86400&X-Amz-Signature=8ae883c14478efdcae32953557c27e8474ef6982db7f128eff5715e7c4c35aa9&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)

서버에서는 유저가 보내준 헤더와 페이로드를 이용해 만든 시그니쳐 값과, 기존에 보낸 시그니쳐 값을 비교

<br>

### 한계

1. 중복 로그인인지 알 방법이 없음(단, 만료시간 설정은 가능)
2. 인증 토큰이 한번 유출되면 손 쓸 방법 없음(갑작스럽게 만료시킬 방법이 없기에).이를 보완하기 위해 Refresh Token이 나오게 되었다.(하지만 여전히 탈취가능)

하지만, 충분히 장점도 있다.

1. 별도의 인증 저장소가 필요 없음. → 인증서버와 DB에 의존하지 않아도 됨.
2. 서버를 확장하거나 유지, 보수하는데 유리

<br>

<br>

# 웹소켓

- HTTP 프로토콜은 매 요청과 응답마다 연결을 수립하고 끊는 과정을 반복해야했기 때문에 이러한 실시간 통신의 문제를 해결하기 위해 웹소켓이 등장했다.
- 웹소켓은 웹서버와 웹 브라우저가 지속적으로 연결된 TCP 라인을 통해 실시간으로 데이터를 주고 받을 수 있도록 하는 HTML5의 새로운 사양이다.
- OSI 모델의 제 7계층에 위치하며 제 4계층의 TCP에 의존한다.
- 웹소켓 이전의 양방향 통신 방법
  1. Polling 방식
     - 클라이언트가 서버에 HTTP 요청을 주기적으로 요청하고 서버가 응답하는 방식
     - 오버헤드가 크다
  2. Long Polling 방식
     - 클라이언트가 서버에 HTTP 요청을 하면 서버는 대기하고 있다가 이벤트가 발생했을 때 응답하는 방식(유튜브 실시간 댓글)
  3. Streaming 방식
     - Polling, Long Polling처럼 커낵션을 연결하고 끊는 과정 없이 필요한 메세지를 계속 전달한다.
- 웹소켓 연결은 HTTP 프로토콜을 통해 이루어진다.
- 웹소켓은 stateful protocol 이기 때문에 클라이언트와 한번 연결되면 계속 연결을 유지하며 오버헤드가 매우 작다.
- 웹소켓은 서버와 클라이언트 간에 Socket Connections을 유지해서 **양방향 통신**을 가능하도록 하는 기술로 **Real-time web** application구현을 위해 사용되어지고 있다. (SNS, 게임, 구글 DOC, 증권거래 등)
- 웹소켓 통신 과정
  1. 클라이언트와 서버간에 전이중 통신을 수행하려면 클라이언트가 서버로 HTTP UPGRADE 요청을 보내야 한다. 이를 웹 소켓 프로토콜 핸드 쉐이크라고한다.
  2. 서버가 커넥션을 UPGRADE 할 수 있는 경우,  HTTP 101 응답을 클라이언트에게 보낸다. 서버는 핸드 쉐이크가 성공적으로 수행되었다고 판단하고,서버와 클라이언트 사이의 커넥션을 웹 소켓 프로토콜로 UPGRADE 한다. 클라이언트와 서버 사이의 HTTP 101 응답이 전달되는 순간, 서버와 클라이언트 사이의 커넥션은 HTTP 프로토콜이라고 하지 않는다. 그리고 이순간 양방향 통신이 가능해진다.
  3. 웹 소켓으로 연결된 모든 클라이언트는 다른 클라이언트에게 커넥션을 끊는 요청을 전송할 수 있다.

<br>

#### HTTP vs 웹소켓

|                | HTTP        | 웹소켓           |
| -------------- | ----------- | ---------------- |
| 통신 방법      | 일회성      | 실시간 반복 가능 |
| 주요 활용 목적 | 문서전달    | 실시간 통신      |
| 프로토콜       | http, https | ws, wss          |

<br>

#### 웹소켓 핸드쉐이크

- 한 번의 HTTP 요청과 HTTP 응답으로 이루어짐
- 핸드쉐이크가 끝나면 HTTP 프로토콜을 웹소켓 프로토콜로 변환하여 통신
- 먼저 클라이언트가 HTTP로 웹소켓 연결 요청을 하면서 시작됨
  - 웹소켓 연결 요청에는 `“Connection:Upgrade”`와 `“Upgrade:websocket”` 헤더를 통해 웹소켓 요청임을 표시
  - `“Sec-WebSocket-Key”` 헤더를 통해 핸드쉐이크 응답을 검증할 키 값을 보냄

![diagram](https://woowacourse.github.io/javable/static/9c28655f35ef0319b945fc4a7c9a67ad/ad78b/2020-09-20-websocket_diagram.png)

<br>

<br>

# 사설 IP간의 통신

![img](https://t1.daumcdn.net/cfile/blog/1215C63850F0084A0B)

### NAT ( Network Address Translation )

- IPv4의 주소 고갈 문제를 해결하기 위한 방법 중 하나로, IP 헤더 안의 한 주소를 다른 주소로 변환하는 것
- 사설 네트워크에 속한 여러 개의 호스트가 하나의 공인 IP 주소를 사용하여 인터넷에 접속하기 위해 쓰이는 방식
- 외부 관점에서 볼 때, 하나의 NAT 서버로만 보이기 때문에 네트워크 내부 구조를 숨기는 효과를 가지며, 보안 수준이 향상된다는 장점이 있다.
- 공식적으로 알려진 IP 주소와 사설 IP 주소를 분리함으로써, 많은 양의 공인 IP 주소가 필요하지 않도록 수요를 줄여준다.

**게이트웨이가 발신자의 IP를 수정하여 발신할 때 게이트웨이는 내부에 갖고 있는 테이블에 이를 기록해 둔다. 어떤 주소에서 어떤 주소로, 무슨 프로토콜을 사용하여 발신했는지를 기록한 후, 응답 패킷이 되돌아오면 그 값을 찾아서 해당하는 사설망 기기에게 발신하는 것이다. 이렇게 테이블을 만들어서 저장해놓고 찾아가는 방법으로 통신하게 된다.**

**NAT의 통신 방식은 큰 문제가 하나 있다. 바로 여러 개의 사설망 내의 기기가 동시에 같은 외부망 주소로 접속을 요청하는 경우이다. 원래라면 요청한 곳의 주소와 포트를 보고 해당하는 사설망 주소를 찾아서 보내주어야 하는데, 해당하는 주소가 여러 개일 경우 중복되므로 이를 처리할 방법이 없는 것이다.**

**이를 해결하기 위해 만들어진 것이 NAPT이다.**

![Untitled.png (640×360)](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/820569f1-c1d3-4e27-823f-c0a0e3bf834b/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210612%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210612T165033Z&X-Amz-Expires=86400&X-Amz-Signature=3d22bb70145b72a34a82c25c9e631086bbb092ed7c9d8fd19313eceb322cacd6&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)

**NAPT는 Network Address Port Translation의 약자로, NAT에서는 발신자의 사설망-외부망 IP를 바꿔서 보내주는 역할만을 수행했다면 이제는 포트까지 바꿔서 보내는 역할을 한다. 이러면서 NAPT의 테이블은 NAT의 테이블에서 Port에 해당하는 컬럼이 추가된다. 이렇게 변경한 결과 게이트웨이는 발신자의 포트 번호를 보고도 구별할 수 있게 되었다. 만약 발신자의 포트 번호까지 같게 패킷이 보내지면 어떻게 되느냐고도 할 수 있는데, 그럴 경우에는 위 그림처럼 Private Port를 임의의 SRC 포트로 바꿔서 보내면 되므로 아무런 문제가 없다.**

<br>

#### 사설 IP간의 통신 순서

1. 송신호스트는 송신지 IP 주소는 192.168.0.10, 송신지 포트번호는 8000번, 목적지 IP 주소를 211.189.19.20(라우터+NAT) 으로 적고, 목적지 포트번호를 9000번 이라고 적는다. 그리고 패킷을 전송한다.

2. 210.119.19.10(라우터+NAT) 는 1번에서 전송된 패킷을 받는다. 그리고 송신지의 IP 주소를 210.119.19.10 으로 바꿔 적는다. 그리고 패킷 전송한다.

3. 211.189.19.20(라우터+NAT) 는 2번에서 전송된 패킷을 받는다. 이 때 목적지 IP 주소에 211.189.19.20 으로 써있기 때문에 자신에게 온 패킷이라고 확인한다. 그리고 목적지 포트번호가 9000번 임을 확인한다. 그 후 9000번 포트로 오는 데이터를 누구에게 전달해야 하는지 확인한다. 확인해보니 9000번 포트->192.168.0.20 으로 전달해야 되는 것을 알아낸다. 그리고 192.168.0.20(진짜 수신호스트) 으로 패킷을 전달한다.

4. 수신호스트 (192.168.0.20) 는 패킷을 잘 전달받는다. 그리고 답장을 하기 위해서 송신지 IP 주소와 포트번호를 살핀다. 송신지 IP 주소에는 210.119.19.10(라우터+NAT) 로 적혀 있고, 포트번호는 8000번이 적혀 있다. 따라서 이 주소로 다시 답장 패킷을 보낸다.

5. 답장 패킷은 송신호스트에게 위와 같은 방식으로 다시 전달된다.

<br>

<br>

# 사설 IP에서 서버를 구축하는 포트포워딩

### 포트포워딩

특정 IP주소와 포트 번호의 통신 요청을 다른 ip와 포트 번호로 넘겨주는 네트워크 주소 변환(NAT)의 응용

1. 공인 IP의 특정 포트로 전송,
2. 특정 포트로 들어온 요청을 특정 IP의 특정 포트로  전송

![Untitled.png (1168×468)](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/998297c6-ecb9-4e01-832c-3f7c09d9122a/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210612%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210612T165044Z&X-Amz-Expires=86400&X-Amz-Signature=96d930f7834d23982b1afb748d2b27c936eded7bc2484ca7f50bdaf711e5b234&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)

<br>

<br>



# CORS

Cross-Origin Resource Sharing(CORS)은 추가적인 HTTP header를 사용해서 애플리케이션이 다른 origin의 리소스에 접근할 수 있도록 하는 메커니즘

다른 origin에서 내 리소스에 함부로 접근하지 못하게 하기 위해 사용됨

- CORS가 필요한 이유
  - 서비스 공급자 외의 사용자가 악의적으로 세션을 요청해 세션을 탈취하는 것을 방지
  - 공급자가 허용한 origin의 요청만 받기 위함
  - 대표적으로 피싱사이트 예방을 위해 사용
  - 악의를 가진 사용자가 소스 코드를 구경한 후 [CSRF(Cross-Site Request Forgery)](https://ko.wikipedia.org/wiki/사이트_간_요청_위조)나 [XSS(Cross-Site Scripting)](https://ko.wikipedia.org/wiki/사이트_간_스크립팅)와 같은 방법을 사용하여 여러분의 어플리케이션에서 코드가 실행된 것처럼 꾸며서 사용자의 정보를 탈취하기가 너무나도 쉬워진다.
- CORS 동작 방식
  - 브라우저에서 리소스 요청 헤더(**`request header`**)에 **`Origin`** 필드에 요청을 보내는 출처와 다음의 정보를 담아 전송
    - 내 origin 정보
    - 요청한 method 정보
    - 어떤 header를 포함할 것인지에 대한 정보
  - 서버에서는 응답 헤더 (response header)의 **`Access-Control-Allow-Origin`** 이라는 값에 응답할 수 있는 origin들( **`이 리소스를 접근하는 것이 허용된 출처`**)을 헤더에 담아서 브라우저에 보냄
  - 브라우저는 이 헤더를 보고 해당 origin에서 요청할 수 있다면 리소스 전송을 허용하고 만약 불가능하면 에러 발생시킴











