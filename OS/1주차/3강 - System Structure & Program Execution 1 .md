![캡처](https://user-images.githubusercontent.com/23302973/97690915-00e67880-1ae1-11eb-9dea-21060fa84f0f.PNG)

----timer
* 정해진 시간이 흐른 뒤 운영체제에게 제어권이 넘어가도록 인터럽트를 발생시킴
* 타이머는 매 클럭 때마다 1씩 감소
* 타이머 값이 0이 되면 타이머 인터럽트 발생
* CPU를 특정 프로그램이 독점하는 것으로부터 보호

* time sharing을 구현하기 위해 이용됨

----device controller
* I/O device controller
  - 해당 I/O 장치유형을 관리하는 일종의 작은 CPU
  - 제어 정보를 위해 control register, status register를 가짐
  - local buffer를 가짐(일종의 data register)
* I/O는 실제 device와 local buffer 사이에서 일어남
* device controller는 I/O가 끝났을 경우 인터럽트로 CPU에 그 사실을 알림

----입출력(I/O)의 수행
* 모든 입출력 명령은 특권 명령
* 사용자 프로그램은 어떻게 I/O를 하는가?
  - 시스템 콜: 사용자 프로그램은 운영체제에게 I/O 요청
  - trap을 사용하여 인터럽트 벡터의 특정 위치로 이동
  - 제어권이 인터럽트 벡터가 가리키는 인터럽트 서비스 루틴으로 이동
  - 올바른 I/O 요청인지 확한 후 수행
  - I/O 완료 시 제어권을 시스템 콜 다음 명령으로 옮김
  
----인터럽트
* 인터럽트 당한 시점의 레지스터와 program counter를 저장 한 후 CPU의 제어를 인터럽트 처리 루틴에 넘김
* 넓은 의미의 인터럽트
  - interrupt(하드웨어 인터럽트): 하드웨어가 발생시킨 인터럽트
  - trap(소프트웨어 인터럽트): exception - 프로그램이 오류를 범한 경우 / system call - 프로그램이 커널 함수를 호출하는 경우
* 인터럽트 관련 용어
  - 인터럽트 벡터: 해당 인터럽트의 처리 루틴 주소를 가지고 있음
  - 인터럽트 처리 루틴: 해당 인터럽트를 처리하는 커널 함수
