## 프로세스의 개념
* 프로세스의 문맥(context) -> **프로세스의 상태를 나타내는 모든 것**
  * CPU 수행 상태를 나타내는 하드웨어 문맥
    - program counter -> 얘가 어디를 가리키고 있는가를 알아야함
    - 각종 register -> 어떤 명령까지 실행했는가를 알아야함
  * 프로세스의 주소 공간(메모리)
    - code, data, stack -> 현재 어떠한 내용을 쌓아놓고 있는가를 알아야함
  * 프로세스 관련 커널 자료구조
    - PCB(Process Control Block) -> 프로세스 하나가 실행될 때마다 pcb를 하나씩 두면서 cpu를 얼마나 주는지 등을 관리
    - Kernel stack -> system call이 일어나면 프로세스의 주소공간이 아닌 커널의 주소공간에서 프로세스가 실행됨(스택에 관련 정보를 쌓는 것)

--> 문맥을 파악하고 있어야 다음번 실행 할 때 처음부터 실행하지 않고 이어서 실행할 수 있게됨

## 프로세스의 상태
* 프로세스는 상태가 변경되며 수행
  * Running
    - CPU를 잡고 명령을 수행중인 상태
  * Ready
    - CPU를 기다리는 상태(메모리 등 다른 조건을 모두 만족하면서 -> CPU만 얻으면 바로 수행 가능한 상태)
  * Blocked(Wait, Sleep)
    - CPU를 주어도 당장 명령을 수행할 수 없는 상태
    - 프로세스 자신이 요청한 이벤트(I/O 등)가 즉시 만족되지 않아 이를 기다리는 상태
    - 예) 디스크에서 파일을 읽어와야 하는 경우
    
![KakaoTalk_20201106_181005731](https://user-images.githubusercontent.com/23302973/98347879-5da2df80-205b-11eb-89e6-34c2949a78ef.jpg)

![KakaoTalk_20201106_182156881](https://user-images.githubusercontent.com/23302973/98349201-0c93eb00-205d-11eb-99c0-dc64c6dd2c01.jpg)

## PCB(Process Control Block)
* 운영체제가 각 프로세스를 관리하기 위해 프로세스당 유지하는 정보
* 다음의 구성 요소를 가짐(구조체로 유지)
  1. OS가 관리상 사용하는 정보
     - 프로세스 상태, 프로세스 ID
     - 스케줄링 정보, 스케줄링 우선순위
  2. CPU 수행 관련 하드웨에 값
     - 프로그램 카운터, 레지스터
  3. 메모리 관련
     - Code, Data, Stack 위치 정보
  4. 파일 관련
     - 오픈 파일 디스크립션
     
 ![캡처](https://user-images.githubusercontent.com/23302973/98349660-a360a780-205d-11eb-835e-3e2737f7545a.PNG)

## 문맥 교환
* CPU를 한 프로세스에서 다른 프로세스로 넘겨주는 과정
* CPU가 다른 프로세스에게 넘어갈 때 운영체제는 다음을 수행
  * CPU를 내어주는 프로세스의 상태를 그 프로세스의 PCB에 저장
  * CPU를 새롭게 얻는 프로세스의 상태를 PCB에서 읽어옴
 
![KakaoTalk_20201106_183539539](https://user-images.githubusercontent.com/23302973/98350640-f71fc080-205e-11eb-9962-190bfd3bd265.jpg)

