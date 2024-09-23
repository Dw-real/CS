# 운영체제
_____
### 🔴 운영체제란?
사용자와 컴퓨터 하드웨어 사이에서 중계 역할을 하면서, 프로그램의 실행을 관리하고 제어하는 시스템 소프트웨어
_____
### 🔴 컴퓨터 시스템의 범위
- 응용소프트웨어 층
- 운영체제 층
- 컴퓨터 하드웨어 층
_____
### 🔴 스택이란?
운영체제는 프로그램을 실행시킬 때 프로그램마다 다음과 같은 4개의 영역을 제공한다.
![Memory Area](https://velog.velcdn.com/images/dodozee/post/c4fec618-156e-4634-a70f-146a614799d7/image.png)
- 코드 영역 - 프로그램 코드가 적재되는 메모리 영역
- 데이터 영역 - 전역 변수, 정적변수들이 적재되는 영역
- 힙 영역 - 프로그램이 실행 중 동적으로 저장할 데이터를 위한 영역
- 스택 영역 - 함수가 호출될 때 매개변수나 지역 변수, 함수가 실행을 마치고 돌아갈 주소 등을 저장하기 위한 공간

스택은 프로그램의 지역 변수 등을 저장하도록 할당된 메모리 영역으로 다음 내용들이 저장된다.
- 함수의 지역변수들
- 매개변수 값들
- 함수를 마치고 돌아갈 주소
- 함수 코드가 의도적으로 스택에 저장한 값
  
**특별한 메모리나 장치가 컴퓨터에 별도로 있는 것이 아님**
_____
### 🔴 컨텍스트 스위칭
여러 프로세스를 처리해야 하는 상황에서 현재 진행중인 Task(프로세스 혹은 쓰레드)의 상태를 PCB에 저장하고, 다음에 진행할 Task의 상태 값을 읽어 레지스터에 적재하는 과정
> 컨텍스트 : CPU에 들어 있는 레지스터의 값들

**컨텍스트 스위칭을 통해 CPU 사용률을 높일 수 있고 여러 프로세스를 처리할 수 있다.**
_____
### 🔴 커널이란?
**운영체제의 핵심 부분**으로 메모리에 상주하면서 CPU, 캐시, 메모리 등 하드웨어를 관리하고 프로세스의 실행과 중단, 파일 시스템 관리 등
운영체제의 핵심적인 기능을 실행하는 코드와 이들을 관리하기 위해 필요한 프로세스 테이블, 페이지 테이블 등 여러 자료 구조의 집합

다음과 같은 운영체제의 핵심 기능들이 커널 코드에 의해 실행
- 프로세스와 스레드 관리
- 메모리 관리
- 파일 생성, 삭제, 파일 입출력 등 파일 및 파일 시스템 관리
- 디바이스 드라이버를 호출하여 장치 입출력
_____
### 🔴 사용자 공간과 커널 공간
운영체제는 CPU로 액세스할 수 있는 전체 주소 공간을 **사용자 공간**과 **커널 공간**으로 분리하여 운영한다.
- 사용자 공간: 응용프로그램이 적재되고 응용프로그램의 변수가 만들어지고 동적 할당 받는 공간으로 활용하는 공간
- 커널 공간: 커널 코드와 커널 데이터, 그리고 커널 함수들이 실행될 때 필요한 스택 공간, 디바이스 드라이버 등이 탑재되는 공간

✅**사용자 공간과 커널 공간으로 나누는 이유**
응용프로그램으로부터 커널 코드와 데이터를 지키기 위함
_____
### 🔴 시스템 호출(System Call)이란?
사용자나 응용프로그램이 커널에서 제공하는 기능을 사용하기 위한 인터페이스

운영체제는 커널이 제공하는 서비스를 **시스템 호출**을 사용해야만 사용할 수 있도록 제한함으로써 컴퓨터 자원을 보호하면서 사용자나 응용 프로그램에게 서비스를 제공
_____
### 🔴 인터럽트(Interrupt)란?
하드웨어 장치들이 CPU에게 하드웨어 신호를 물리적으로 발생시켜 입출력 완료나 타이머 완료 등을 CPU에게 알리는 방법
_____
### 🔴 프로세스란?
메모리에 적재되어 **실행 중**인 프로그램

💡**실행 중**

CPU에 의해 현재 실행되고 있거나, 준비 상태로 기다리거나, 입출력 등으로 인해 중단되어 CPU로 부터 실행을 대기하고 있는 상태
_____
### 🔴 프로세스 주소 공간
프로세스가 실행 중에 접근할 수 있도록 허용된 주소의 최대 범위로 다음 그림과 같다.
![Process Area](https://velog.velcdn.com/images/rhgurqls00/post/6f24f679-dfca-4e9c-ba2d-1bfc10223d0b/image.png)

**프로세스의 코드는 CPU가 접근할 수 있는 모든 주소 범위에 접근하도록 허용되므로, 사실상 프로세스의 주소 공간은 CPU 주소 공간과 같다.**

힙과 스택 영역의 크기는 정해져 있지 않고 코드 영역과 데이터 영역을 뺀 나머지 공간을 둘이 합쳐 사용한다.
_____
### 🔴 힙 영역과 스택 영역의 차이점
|     | 힙 영역 | 스택 영역 |
|:--- | :--- | :--- |
|저장하는 변수|동적으로 할당된 변수|지역변수, 매개변수, 함수의 리턴값 등|
|크기 결정 순간|런타임(Runtime)|컴파일(Compile)|
|크기 제한|크기가 제한되어 있지 않음 |크기가 제한되어 있음 |
|주소 할당 방향|낮은 주소 -> 높은 주소|높은 주소 -> 낮은 주소|
|장점|큰 데이터 저장 가능, 유연한 메모리 관리 가능|메모리 할당 및 해제가 빠름|
|단점|직접 메모리 관리 필요, 이에 따라 메모리 누수나 조각화 발생 가능|제한된 크기 때문에 스택 오버플로우 발생 가능|
_____
### 🔴 PCB(Process Control Block)이란?
프로세스에 관한 정보를 저장하는 구조체

프로세스 당 하나씩 존재하며 프로세스가 생성될 때 만들어지고 종료되면 삭제

**커널에 의해 생성, 저장, 읽혀지는 등의 관리됨**
_____
### 🔴 프로세스의 생명 주기와 상태 변이
![Process Life Cycle](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FbFhNJu%2Fbtr5PREMV2G%2Fmr9OvmKZulcxmSpZYLFjy0%2Fimg.png)

상태 변이는 **커널 코드**에 의해 이루어짐
_____
### 🔴 프로세스의 종류
- 부모 프로세스 - 프로세스를 생성한 프로세스
- 자식 프로세스 - 프로세스에 의해 생성된 프로세스
- 좀비 프로세스 - 종료하였지만 부모가 종료코드를 읽지 않은 상태로 시스템에 남아있는 프로세스
- 고아 프로세스 - 부모가 먼저 종료한 자식 프로세스
_____
### 🔴 스레드란?
운영 체제나 프로세스 내에서 실행되는 가장 작은 작업 단위

스레드 출현 목적
- 프로세스 보다 작은 실행 단위 필요
- 프로세스의 생성 및 소멸에 따른 오버헤드 감소
- 빠른 컨텍스트 스위칭
- 프로세스들 사이의 통ㅇ신에 대한 어려움 해소

스레드마다 TCB(Thread Control Block) 생성

![Process and Thread](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FkHGmX%2FbtsaESFpHrp%2F6if2bm4y7XjTg9iT3vnTyK%2Fimg.png)
_____
### 🔴 CPU 스케줄링
준비(Ready) 상태에 있는 스레드들 중 하나를 선택하여 CPU를 할당하는 과정

**비선점 스케줄링**
실행 중인 스레드가 자발적으로 종료하거나 기다릴 때까지 CPU 제어권을 다른 프로세스에게 넘기지 않는 스케줄링 방식

- SRTF(Shortest Remaining Time First)
- Priority 스케줄링 (non-preemptive version)

**선점 스케줄링**
현재 실행 중인 스레드를 강제로 중단시켜 준비 리스트로 이동시키고 스케줄링하는 방식

- RR(Round Robin)
- SJF(Shortest Jpb First)
- Prirority (preemtive version)

### 다양한 CPU 스케줄링 알고리즘
1. FCFS(First Come First Served) 스케줄링
   * 큐에 먼저 도착한 스레드를 먼저 스케줄링
   * 비선점 스케줄링
   * 일반적으로 기아는 발생되지 않음
   * 처리율이 낮음

❗실행사례
![FCFS](https://github.com/Dw-real/CS/blob/main/OS/FCFS.png?raw=true)

2. SJF(Shortest Job First) 스케줄링
  * 실행 시간이 가장 짧은 스레드를 먼저 스케줄링
  * 비선점 스케줄링
  * 기아 발생 가능
  * 스레드의 실행 시간을 예측할 수 없기 때문에 현실에서 사용 불가

❗실행사례
![SJF](https://github.com/Dw-real/CS/blob/main/OS/SJF.png?raw=true)

3. SRTF(Shortest Remaining Time First) 스케줄링
  * 남은 실행 시간이 가장 짧은 스레드를 먼저 스케줄링
  * 선점 스케줄링
  * 기아 발생 가능
  * 스레드의 실행 시간을 예측할 수 없기 때문에 현실에서 사용불가

❗실행사례
![SRTF](https://github.com/Dw-real/CS/blob/main/OS/SRTF.png?raw=true)

4. RR(Round-Robin) 스케줄링
  * 스레드들을 타임 슬라이스 주기로 스케줄링
  * 선점 스케줄링
  * 기아 발생 X
  * 구현이 쉬우나 잦은 스케줄링으로 컨텍스트 스위칭에 소요되는 시간이 큼
  * 타임 슬라이스가 작을수록 성능 저하

❗실행사례
![RR 2ms](https://github.com/Dw-real/CS/blob/main/OS/RR1.png?raw=true)

![RR 1ms](https://github.com/Dw-real/CS/blob/main/OS/RR2.png?raw=true)

5. Priroiry 스케줄링
  * 우선순위에 따라 스레드를 실행
  * 선점/비선점 스케줄링
  * 기아 발생 가능
  * 스레드마다 고정 우선순위를 가지는 실시간 시스템에서 주로 사용

6. MLQ(Multi-level Queue) 스케줄링
  * n개의 우선순위 레벨로 구분하여 레벨이 높은 스레드를 우선 처리
  * 선점/비선점 스케줄링
  * 기아 발생 가능
  * 스레드 별로 고정 우선순위를 두고 높은 순위의 스레드를 먼저 실행시키는 시스템에서 사용

7. MLFQ(Multi-level Feedback Queue) 스케줄링
  * 우선순위로 구분된 n개의 큐를 두어 높은 레벨의 큐에 있는 스레드를 먼저 스케줄링
  * 선점 스케줄링
  * 기아 발생 X
  * 알고리즘이 복잡하여 CPU의 오버헤드가 증가됨
_____
### 🔴 스레드 동기화
다수의 스레드가 공유 데이터를 동시에 접근하는 충돌 상황에서 공유 데이터가 훼손되지 않도록 스레드의 실행을 제어하는 기법

❗공유 집계판 문제의 코드 사례
![공유 집계판 문제](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FcMNklq%2FbtsbTpWnX7W%2FQtPOTp2WhhHwPqQM9lO8UK%2Fimg.png)
![공유 집계판 문제 발생](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FL19gO%2Fbtsb60glem2%2FZAKKb6766PHjQWNJrtokA0%2Fimg.png)

🟥 문제점

T1과 T2가 공유 변수 sum에 접근하여 공유 데이터 sum이 훼손

🟥 해결 방법

한 스레드가 공유 데이터 사용을 마칠 때 까지 다른 스레드가 공유 데이터에 접근하지 못하도록 제어

🟡 스레드 동기화와 관련된 중요 개념
  * 임계 구역 : 공유 데이터에 접근하는 코드 블록
  * 상호 배제 : 멀티스레드가 실행되는 환경에서 한 스레드가 임계구역 전체를 배타적으로 실행하도록 보장하는 기법

##### 상호 배제 구현

하드웨어적 방법 - 인터럽트 서비스 금지, 원자명령 활용

1. 인터럽트 서비스 금지
   
임계구역으로 진입할 때 entry 코드에서 인터럽트 서비스를 금지하고 exit 코드에서 인터럽트 서비스를 허용하는 CPU 명령들을 실행하는 방법

❗동작 과정

![인터럽트 서비스 금지](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FcBQ0J7%2FbtsbSfmkBun%2Fqmi107wha0gHkiDuJRjTWk%2Fimg.png)

**문제점**
1. 임계구역을 실행하는 동안 모든 인터럽트가 무시됨
2. 단일 CPU 시스템에서는 활용 가능하지만 멀티코어를 비롯한 다중 CPU를 가진 시스템에서는 활용할 수 없다.

2. 원자명령(Atomic instruction) 사용

상호배제를 위해 만들어진 CPU 명령으로 오늘날 상호배제를 구현하기 위해 사용하는 기법

🟥 원자명령 없이 lock 변수를 이용한 상호 배체 시도

lock 변수 : 1이면 잠금 상태 0이면 열린 상태

![성공 사례](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FbtsLkR%2FbtscmMBImP1%2FH34lUhOBKCiCYuMGU9k1u0%2Fimg.png)
![실패 사례](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2Fbt23lC%2FbtsbTpvlASI%2FKd3poetuqwZJ32vJfJWdck%2Fimg.png)

lock 변수를 사용한 상호배제가 실패한 원인

lock 변수 값을 읽어 들이는 명령과 lock 변수를 1로 바꾸는 명령 사이에 컨텍스트 스위칭이 발생할 때 문제 발생

🟥 해결 방법 - 원자명령 도입

lock 변수 값을 읽어 들이는 명령과 lock 변수를 1로 저장하는 명령을 하나의 명령으로 만드는 것 (원자명령 혹은 TSL)

![TSL](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FbkqA7U%2FbtsbVe0RG14%2Fo9Fk79s3o8ZOxKkRB0PkG1%2Fimg.png)

##### 멀티스레드 동기화 기법

여러 스레드들이 문제 없이 공유 자원을 활용하도록 하는 기법

- lock 방식 - 뮤텍스(mutex), 스핀락(spinlock)
- wait-signal 방식 - 세마포(semaphore)

1. 뮤텍스

- 잠김/열림 중 한 상태를 가지는 락 변수 사용
- 한 스레드만 임계구역에 진입시키고 다른 스레드들을 큐에 대기시킴
- 임계구역의 실행 시간이 짧은 경우 비효율적
![뮤텍스 기법 동기화 구조](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FbdWaGm%2FbtsbSLk1Kd6%2FiplljaUQ85byJUpAujIEE1%2Fimg.png)

🟥 뮤텍스를 활용한 스레드 동기화 과정

![뮤텍스 동기화 과정](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FbpEIRl%2Fbtsb6Z9Cx2J%2FxJyy7TmNmUaq7jCOXfaZcK%2Fimg.png)

2. 스핀락

- 락 변수를 기반
- 뮤텍스와 달리 대기 큐 X
- 커널에서 많이 사용
- 뮤텍스 기법의 **busy-waiting** 모형
- 단일 CPU를 가진 운영체제에서 비효율적
- 임계구역 코드가 짧아서 락이 빨리 열리는 응용에 효과적
- 기아 발생 가능
![스핀락 동기화 구조](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2F1l9vB%2FbtscfBm0IXp%2FzFzBaecdbn1qlr5sIT1840%2Fimg.png)

🟥 스핀락을 활용한 스레드 동기화 과정

![스핀락 동기화 과정](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FpBpvd%2FbtscmKYdNhB%2FApzQuaiEjAD2OlgGOLSDkk%2Fimg.png)

🟥 뮤텍스와 스핀락의 비교

||뮤텍스|스핀락|
|:---|:---|:---|
|대기큐|있음|없음|
|블록 가능 여부|락이 잠겨 있으면 블록|락이 잠겨 있어도 블록되지 않고 계속 락 검사|
|lock/unlock 연산 비용|저비용|고비용|
|하드웨어 관련|단일 CPU에 적합|멀티코어 CPU에 적합|
|주 사용처|사용자 응용프로그램|커널 코드, 인터럽스 서비스 루틴|

3. 세마포

n개의 자원을 다수의 스레드가 공유하여 사용하도록 돕는 자원 관리 기법

🟥 세마포가 필요한 상황

![세마포 필요 상황](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2Fba8VIW%2Fbtsb2TBWIow%2FjKJ9yvFkGOwsyvOwZiTQIK%2Fimg.png)

🟥 세마포 구성 요소
- 자원 - n개
- 대기 큐 - 자원을 할당받지 못한 스레드가 잠자는 곳
- counter 변수 - 사용가능한 자원의 개수를 나타내는 정수형 변수
- P/V 연산 - P 연산은 자원 요청 시, V 연산은 자원 반환 시 실행되는 연산

![세마포](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FdqsiKl%2Fbtsb1RRRhLq%2FVxucV0Bybtkak8cNPxeLvK%2Fimg.png)
_____
### 🔴 교착상태(Deadlock)
두 개 이상의 프로세스가 서로 자원을 기다리면서 무한히 대기하는 상태

컴퓨터 시스템에서 교착상태는 **다중프로그래밍** 도입과 함께 발생

🟥 식사하는 철학자 문제
![식사하는 철학자](https://i.namu.wiki/i/yK-_patdtMNP-901Y93kyV8FSwg4ze2ZQ-OPSGrNiKFYBnCHnIpMaQusYkIy_CAIHEXpEgKt9e6XsDRDpkFsbQk298AeCtY7SHMmjXwqBIBhIg4yPhfLyAGvelKOq0bWBUHqT3pUmglenu-KWYO0zA.webp)

❗ 5명이 동시에 왼쪽 포크를 들고 오른쪽 포크를 집으려고 하는 경우 교착상태 발생

- 원인 : 환형 요청/대기
  ㅇㄹㄴㅇㄹㅇㄴ
- 해결 : 환형 요청/대기가 생기지 않게 규칙 변경
