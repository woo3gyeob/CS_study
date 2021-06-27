# Race Condition

> **`두 개 이상의 프로세스`**가 공통 자원을 **병행적으로(concurrently)** 읽거나 쓰는 동작을 할 때, 공용 데이터에 대한 접근이 어떤 순서에 따라 이루어졌는지에 따라 그 **실행 결과가 같지 않고** 달라지는 상황

![Kotlin Coroutine에서의 동기화 제어](https://media.vlpt.us/post-images/dvmflstm/71800cd0-3529-11ea-bb25-9b067b44fbb4/racecondition.jpg)

- 멀티 프로세스 또는 멀티 스레드의 환경에서 발생하는 문제

- 멀티 프로세스(스레드) 상에서 발생하는 제어 문제
  - Mutual Exclusion 상호 배제
    - 공용 데이터 자원에는 특정 시점에 하나의 프로세스만 진입할 수 있어야 함
    - 다른 프로세스는 해당 자원에 접근 금지
  - Deadlock
    - 상호 배제로 인해 파생된 문제
    - 한 프로세스가 여러 공용 데이터를 필요로 하는 경우, 하나의 공용 데이터를 활용하는 동안 다른 데이터에 대해서 다른 프로세스의 접근이 금지되어 교착 상태에 빠지는 문제
  - Starvation
    - 프로세스들이 서로의 작업만 끝나기를 기다리면서 진행을 하지 못하고 영구적으로 block되어 있는 상태

<br>

### Critical Section

- **각 프로세스에서 공유 데이터를 엑세스하는 프로그램 코드 영역**

- 프로세스나 스레드가 공통으로 사용하는 변수나 테이블이나 파일을 업데이트

- Race Condition 해결을 위한 조건

  - Bounded Wait : 다른 프로세스가 진입할 수 없게 막아서는 안됨

  - Process : Critical Section에 다른 프로세스가 없다면 진입할 수 있어야 함

    ​				 임계 구역에 누가 먼저 들어갈 것인가 하는 결정은 유한 시간 내에 결정

  - Mutual Exclution : Critical Section에는 특정 시점에 하나의 프로세스만 진입할 수 있어야 함

    

<br>

<br>

### `Race Condition 해결방법` : 동기화 (Synchronization)

___

> Race Condition 문제 해결을 위해 서로가 알고있는 **정보를 일치**시키는 것

> `Semaphore(세마포어)`
>
> `Mutex(뮤텍스)`

<br>

#### Semaphore(세마포어)

![img](https://blog.kakaocdn.net/dn/cgvF68/btqDyMXcTWu/zhuMLl9YWBrhRkv6xkEm11/img.png)

- **`여러 프로세스`**에서 동일한 공유 자원의 접근을 막아 동기화시키는 기술
- 일반적으로 긴 시간을 확보하는 리소스에 대해 적용
- **여러 스레드 접근의 허용 선택 가능 **

<br>

#### Mutex (뮤텍스)

![img](https://blog.kakaocdn.net/dn/KK4GG/btqDyMXcTVK/dMLkVA1QUmN3khbdFuxoF1/img.png)

- **`여러 스레드`**에서 동일한 공유 자원의 접근을 막는 기술
- **Critical Section**을 가진 쓰레드들의 Running time이 서로 겹치지 않게 각각 단독으로 실행되게 하는 기술
- 상호배제를 사용해 두개 이상의 Thread의 동시 사용을 막는 것

<br>

#### 이외의 방법

- 모니터 : 특정 공유 자원을 프로세스에 할당하는데 필요한 데이터와 데이터를 처리하는 프로시저로 구성

- Readers & Writers Lock : 읽기 접근은 동시에 여러 Thread에서 허용하되,

  ​											 쓰기 접근은 한 시점에 한 Thread만 허용하는 기법

- Spin Lock : 계속해서 Lock을 시도하면서 CPU를 점유하는 기법

- barrier : 모든 자식 Thread의 작업 완료를 기다렸다가 후속 작업을 진행하는 기법