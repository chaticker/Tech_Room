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

