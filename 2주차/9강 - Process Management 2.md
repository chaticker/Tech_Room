## 프로세스 생성

* copy-on-write: write가 발생했을때, 그 때 copy를 하겠다는 것 -> 그 이전까지는 부모 것을 그대로 공유 함

### fork() 시스템 콜

* 부모 프로세스 복제 생성

![KakaoTalk_20201107_112202938](https://user-images.githubusercontent.com/23302973/98429682-870b4c00-20eb-11eb-90fa-9200e2114e5f.jpg)

### exec() 시스템 콜

* 완전히 새로운 프로그램으로 덮어 씌움

![KakaoTalk_20201107_113312411](https://user-images.githubusercontent.com/23302973/98429936-15cc9880-20ed-11eb-8aad-eb570cd0ac5a.jpg)

### wait() 시스템 콜

* 자식이 종료될 때까지 잠들어서 기다림

![KakaoTalk_20201107_113857096](https://user-images.githubusercontent.com/23302973/98430014-de122080-20ed-11eb-8127-c6915dc5661a.jpg)

### exit() 시스템 콜

* 프로세스의 종료
  - 자발적 종료
    * 마지막 statement 수행 후 exit() 시스템 콜을 통해
    * 프로그램에 명시적으로 적어주지 않아도 main 함수가 리턴되는 위치에 컴파일러가 넣어줌
  - 비자발적 종료
    * 부모 프로세스가 자식 프로세스를 강제 종료시킴
      - 자식 프로세스가 한계치를 넘어서는 자원 요청
      - 자식에게 할당된 태스크가 더 이상 필요하지 않음
    * 키보드로 kill, break 등을 친 경우
    * 부모가 종료하는 경우
      - 부모 프로세스가 종료하기 전에 자식들이 먼저 종료됨


## 프로세스 간 협력
* 독립적 프로세스
  - 프로세스는 각자의 주소 공간을 가지고 수행되므로, 원칙적으로 하나의 프로세스는 다른 프로세스의 수행에 영향을 미치지 못함

* 협력 프로세스
  - 프로세스 협력 메커니즘을 통해 하나의 프로세스가 다른 프로세스의 수행에 영향을 미칠 수 있음
  
  * 프로세스 간 협력 메커니즘(IPC:Interprocess Communication)
    - 메시지를 전달하는 방법
      * message passing: 커널을 통해 메시지 전달
    - 주소 공간을 공유하는 방법
      * shared memory: 서로 다른 프로세스 간에도 일부 주소 공간을 공유하게 하는 메커니즘
    - 스레드: 스레드는 사실상 하나의 프로세스이므로 프로세스 간 협력으로 보기는 어렵지만, 동일한 프로세스를 구성하는 스레드들 간에는 주소 공간을 공유하므로 협력 가능
    

### Message Passing

![KakaoTalk_20201107_115316225](https://user-images.githubusercontent.com/23302973/98430334-e2d7d400-20ef-11eb-97f9-8b0eee4bd685.jpg)

![KakaoTalk_20201107_115749216](https://user-images.githubusercontent.com/23302973/98430448-904ae780-20f0-11eb-8fab-775085717bfd.jpg)

##CPU 스케줄링

* CPU-burst Time의 분포
  - I/O-bound process
    * CPU를 잡고 계산하는 시간보다 I/O에 많은 시간이 필요한 job
    * many short CPU bursts
    
  - CPU-bound process
    * 계산 위주의 job
    * few very long CPU bursts

* CPU Scheduler & Dispatcher
  - CPU Scheduler -> CPU를 누구한테 줄지 결정
    * ready 상태의 프로세스 중에서 이번에 CPU를 줄 프로세스를 고름
    
  - Dispatcher -> 실제로 CPU를 주는 과정
    * CPU의 제어권을 CPU scheduler에 의해 선택된 프로세스에게 넘김
    * 이 과정을 문맥교환이라 함
    
  - CPU 스케줄링이 필요한 경우는 프로세스에게 다음과 같은 상태 변화가 있는 경우
    1. running -> blocked (예: I/O 요청하는 시스템 콜)
    2. running -> ready (예: 할당시간 만료로 타이머 인터럽트)
    3. blocked -> ready (예: I/O 완료 후 인터럽트)
    4. terminate
    
    **1, 4의 경우는 자진 반납, 이 외 스케줄링은 강제로 뺏는 경우임**
