# 운영체제

> 운영체제란
>
> CPU
>
> Process vs Thread
>
> Context Switching

<br>

<br>

# 💻운영체제란?

![Untitled.png (1478×877)](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/d5e53265-6427-4c58-956f-52610a31b83b/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210613%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210613T150710Z&X-Amz-Expires=86400&X-Amz-Signature=f96d0949c05594d189751d7185e67084f229c5b46be3b1ab59d4562684cd4d13&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)

- 컴퓨터 시스템의 자원들을 효율적으로 관리하며 사용자가 컴퓨터를 편리하고 효과적으로 사용할 수 있도록 환경을 제공하는 여러 프로그램의 모임이다.
- 컴퓨터 사용자와 컴퓨터 하드웨어 간의 인터페이스로서 동작하는 시스템 소프트웨어의 일종으로 다른 응용프로그램이 유용한 작업을 할 수 있도록 환경을 제공한다.
- 종류: 윈도우, 유닉스, 리눅스, 맥OS, 안드로이드 등
- 목적: 처리 능력 향상, 사용 가능도 향상, 신뢰도 향상, 반환 시간 단축
- 기능
  1. 프로세서, 기억장치, 입출력장치, 파일 및 정보 자원 관리
  2. 자원 스케줄링 제공
  3. 사용자와 시스템간 인터페이스 제공
  4. 하드웨어와 네트워크 관리 및 제공
  5. 데이터 관리, 데이터와 자원의 공유 기능 제공
  6. 시스템 오류 검사 및 복구
  7. 자원 보호 기능 제공
  8. 입출력 보조 기능 제공

![Untitled.png (1832×1080)](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/0f521566-80c5-4e53-86e3-61c0ff1ed8f5/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210613%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210613T150730Z&X-Amz-Expires=86400&X-Amz-Signature=90ae781dabc4e1fdf9faab4b19dd68a8dd1dfdcda4157e92ef93805f6790a456&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)

<br>

## **부팅**

컴퓨터의 구조 단순화

![https://user-images.githubusercontent.com/34755287/53879645-5a6b7b00-4052-11e9-84ad-25a4dc7c1306.png](https://user-images.githubusercontent.com/34755287/53879645-5a6b7b00-4052-11e9-84ad-25a4dc7c1306.png)

- **Processor**는 일반적으로 **CPU**를 말함

- main memory를 보면 ROM과 RAM으로 나누어져 있음

- ROM: 

  비휘발성

   으로 메모리에서 극히 일부를 차지 (수 KB)

  - ROM은 하드디스크와 같이 비휘발성으로 전원이 꺼져도 그 안의 내용이 계속 유지됨

- RAM: 

  휘발성

   으로 메모리의 대부분을 차지하며 실제 프로그램이 할당되는 곳 (수 MB ~ 수 GB)

  - RAM은 휘발성이므로 전원이 꺼지면 메모리안의 모든 내용 삭제

### **컴퓨터의 전원이 켜졌을 때**

1. 프로세서(CPU)에서 ROM에 있는 내용을 읽음

2. ROM안에 저장되어 있는 **POST**(Power-On Self-Test), **부트 로더**(boot loader)에 의해 **부팅** 진행

   - **POST**는 전원이 켜지면 가장 처음에 실행되는 프로그램으로 현재 컴퓨터의 상태를 검사
   - POST 작업이 끝나면 부트 로더 실행
   - **부트 로더**는 하드디스크에 저장되어 있는 운영체제를 찾아서 메인 메모리(RAM)에 가져옴

3. 아래 그림처럼 **부트 로더**가 진행되고 나면 운영체제가 수행할 준비를 마치게 되며,

   컴퓨터 전원이 꺼질 시 운영체제 종료

![https://user-images.githubusercontent.com/34755287/53879648-5b041180-4052-11e9-9642-6bf80de33a3e.png](https://user-images.githubusercontent.com/34755287/53879648-5b041180-4052-11e9-9642-6bf80de33a3e.png)

# CPU

- Central Processing Unit의 줄임말로 중앙 처리 장치라고 한다. (뇌)
- 컴퓨터 하드웨어와 신호를 주고 받으면서 시스템 전체를 제어하는 역할을 한다. (**프로그램을 실행시키는 역할**)

※ 이해하기 쉽게 컴퓨터 구매할때 확인하는 정보로 알아보자.

![https://blog.kakaocdn.net/dn/bOpXFQ/btq65dGhRUz/KcIX5wT5o3ksT49HkNiwp1/img.png](https://blog.kakaocdn.net/dn/bOpXFQ/btq65dGhRUz/KcIX5wT5o3ksT49HkNiwp1/img.png)

1. 코어 : CPU 핵심, 이진수 연산, 1개면 싱글코어, 여러개면 멀티코어(듀얼, 쿼드, 헥사...)

> > 코어가 많다(=터널을 많이 뚫었다 = 처리 속도가 빠르다) ↔ 쓰레드가 많다(= 차선이 많다)

2. 클럭 : 초당 명령어를 처리할 수 있는 속도, GHz

> > 클럭이 높다(=제한속도가 높다 = 더 빠르게 일들을 처리할 수 있다)

3. L3 캐시 메모리 : RAM을 거치지 않고 즉각 응답할 수 있도록 저장하는 장소

4. 연산체계 : 32/64bit, 연산 능력, 2의 64승까지 연산 가능 (1 클럭에 처리할 수 있는 데이터의 양

- 구성 요소
  1. 제어 장치(CU): 컴퓨터에 있는 모든 장치들의 동작을 지시하고 제어하는 장치이다. 명령 레지스터에서 읽어들인 명령어를 해독하여 해당하는 장치에게 제어 신호를 보내 정확하게 수행하도록 지시한다.
  2. 연산 장치(ALU): 제어 장치의 명령에 따라 실제로 연산을 수행하는 장치(산술 연산, 논리 연산, 관계 연산 등)
  3. 레지스터: CPU 내부에서 처리할 명령어나 연산의 중간 결과 값 등을 일시적으로 기억하는 임시 기억장소이다.
  4. 버스: CPU, 메모리 I/O 장치 등과 상호 필요한 정보를 교환하기 위해 연결된 공동의 전송선이다.

<br>

<br>

# 프로세스 vs 스레드

여러개의 파일 → 프로그램 → 실행하면 프로세스 : CPU(프로세서)

※ 프로그램 : 파일이 저장 장치에 저장, 메모리에는 올라가 있지 않은 정적인 상태

- 프로세스 : 운영체제로부터 자원을 할당받은 작업의 단위

  : 다른 정의 - 동적 상태의 프로그램

  ![Untitled.png (2991×1588)](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/a2620cb7-aae2-406f-9446-6fcde4b84f26/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210613%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210613T150839Z&X-Amz-Expires=86400&X-Amz-Signature=9e0467a8f32eda66d0517d322ec8099cac0fe8fb998999c454bf1777499a47d6&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)

  - **Code** : 코드 자체를 구성하는 메모리 영역(프로그램 명령)
  - **Data** : 전역변수, 정적변수, 배열 등 (초기화된 데이터)
  - **Heap** : 동적 할당 시 사용 (new(), mallock() 등)
  - **Stack** : 지역변수, 매개변수, 리턴 값 (임시 메모리 영역)

  <br>

  특징

  - 메모리에 올라와 있는 프로그램의 인스턴스(독**립적인 개체**)

  - 프로세스는 각각 **독립된 메모리 영역**을 할당받는다.

    **메모리 영역**

    1. Code: 코드 자체를 구성하는 메모리 영역(프로그램 명령)
    2. Data: 전역 변수, 정적 변수, 배열 등(초기화된 데이터)
    3. Stack: 지역 변수, 매개변수, 리턴 값등(임시 메모리 영역)
    4. Heap: 동적 할당 시 사용(new(), mallock() 등)

  - 프로세스 하나당 최소 한개의 스레드(메인 스레드)를 가지고 있다.

  - 각 프로세스는 별도의 주소 공간에서 실행되며, **다른 프로세스의 변수나 자료구조에 접근할 수 없다.**

  - 다른 프로세스의 자원에 접근하려면 프로세스 간의 통신 **(IPC:i**nter-process communication) 이용

    ex) 파일, 파이프, 소켓

  ![Untitled.png (1354×507)](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/2bb22ee1-ae1e-4000-87b9-6f04931767fe/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210613%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210613T150914Z&X-Amz-Expires=86400&X-Amz-Signature=d61869a32f53df4af3ca46b5301ee0810181c96762e4e12f17d8183143fe67e8&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)

  **멀티 프로세스**

  : 하나의 응용 프로그램을 여러개의 프로세스로 구성하여 각 프로세스가 하나의 작업을 처리하도록 한다.

  - 장점
    1. 여러개의 자식 프로세스 중 하나에 문제가 발생하면 해당 프로세스만 죽는 것 이상으로 다른 영향이 확산되지 않는다.
  - 단점
    1. 각각의 독립된 메모리 영역을 할당받았기 때문에 하나의 프로그램에 속하는 프로세스들 사이의 변수 공유가 안된다.
    2. Context switching 에서의 오버헤드(캐쉬메모리 초기화 등 무거운 작업이 진행되고 많은 시간이 소모)가 발생한다.

  <br>

  **멀티 스레드**

  - **장점**
    1. 컨텍스트 스위칭을 드물게 일어나므로 자원 손실이 적음
    2. 2.stack을 제외한 모든 메모리를 공유하기에 효율적인 일처리 가능

  - **단점**

    1. 하나의 스레드가 데이터 공간 망가뜨리면, 모든 스레드가 작동 불능 상태 (공유 메모리를 갖기 때문) ⇒ 안정성 문제

       - 멀티스레드의 안전성에 대한 단점은 Critical Section 기법을 통해 대비함

       ↔ 반대로 멀티프로세스는 영향을 받지 않아 상대적으로 **안정성이 높음**

    2. code-data-heap 영역을 공유하기에 스레드간 동기화 문제 발생

  <br>

  ex) `인터넷익스플로러 하나가 응답 없으면 다 꺼지지만 크롬은 아닌 이유`

  인터넷 익스플로러는 하나의 프로세스에 멀티스레드를 사용하고, 크롬은 여러 개의 프로세스를 사용하기 때문!

  <br>

  <br>

# Context Switching

시분할기법 : 일정 시간 이후 프로세스를 중단시키고 다른 프로세스로 넘어가게 하는 작업 → 그때 주는 신호 : 인터럽트

> CPU에서 여러 프로세스를 돌아가면서 작업을 처리하는 과정이다. 동작 중인 프로세스가 대기를 하면서 해당 프로세스의 상태(Context)를 보관하고, 대기하고 있던 다음 순서의 프로세스가 동작하면서 이전에 보관했던 프로세스의 상태를 복구하는 작업을 말한다.

- Context: CPU가 해당 프로세스를 실행하기 위한 해당 프로세스의 정보들 (PCB에 저장)

- PCB(프로세스 제어블록): 프로세스 식별자, 프로세스 상태, 프로그램 카운터(다음에 실행할 명령어 주소), CPU 레지스터 및 일반 레지스터, CPU 스케쥴링 등등의 정보를 담음

- TCB(Task Control Block) : Thread에서 context switching을 처리할 때 정보를 담는 내부 공간

  ![Untitled.png (134×189)](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/04d48687-b3af-4780-b9f0-a8494bbcb909/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210613%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210613T151159Z&X-Amz-Expires=86400&X-Amz-Signature=2dd58312dabcca96e12fc93d5aee1da3f9d190ea98f95d0294f647799bfd7a10&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)

- Context Switching 필요 이유: 하나의 작업이 끝날 때까지 기다리면 속도가 너무 느리고 사용하기 불편해서

- 진행 과정:

  1. 대부분의 정보는 레지스터에 저장되고 PCB로 관리한다.
  2. 현재 실행하고 있는 작업의 PCB 정보를 저장한다.
  3. 다음 실행할 작업의 PCB 정보를 읽어 레지스터에 저장하고 CPU가 이전에 진행했던 과정을 연속적으로 수행한다.

- 주의할 점: Context Switching 할 때 해당 CPU는 아무 일을 하지 못하는데, 따라서 Context Switching이 잦아지면 오버헤드가 발생해 성능이 떨어진다.

- Dispatcher는 현재 CPU 데이터는 이전 프로세스의 PCB에 갱신하고, 새로 시작되는 프로세스의 PCB 데이터를 CPU로 복원해준다. Context switching이 발생할 때마다, dispatcher에서 수행하는 작업을 매번 수행해야하며 이 모든 것은 overhead이다.

- Context Switching 을 수행하는 CPU 는 Cache 를 초기화하고 Memory Mapping 을 초기화하는 작업을 거치는 등 아무 작업도 하지 못하므로 잦은 Context Switching 은 성능 저하를 가져온다(메모리 바꿔주느라 찐 작업을 못함)

- 입출력 요청이 왔을 때, CPU 사용 시간이 만료되었을 때, 자식 프로세스를 만들 때, 인터럽트 처리를 기다릴 때 context switching이 발생한다.





