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
    
  * Suspended(stopped) -> **중기 스케줄러로 인해 생김**
    - 외부적인 이유로 프로세스의 수행이 정지된 상태
    - 프로세스는 통째로 디스크에 swap out 됨
    - 예) 사용자가 프로그램을 일시 정지시킨 경우(break key) / 시스템이 여러 이유로 프로그램을 잠시 중단시킴(메모리에 너무 많은 프로세스가 올라와 있을 경우)
    
  **Blocked 와 Suspended의 차이(문제 내기)**
  
  * Blocked: 자신이 요청한 이벤트가 만족되면 ready로 돌아갈 수 있음
  
  * Suspended: 외부에서 정지시킨 상태이므로, 외부에서 다시 재개 시켜줘야 active할 수 있음
  
    
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

![KakaoTalk_20201106_184421907](https://user-images.githubusercontent.com/23302973/98351535-2c78de00-2060-11eb-8066-f43a6a28d22a.jpg)

## 프로세스를 스케줄링 하기 위한 큐
* Job queue
  * 현재 시스템 내에 있는 모든 프로세스의 집합(Ready queue, Device queue 모두를 포함)
  
* Ready queue
  * 현재 메모리 내에 있으면서 CPU를 잡아서 실행되기를 기다리는 프로세스의 집합
  
* Device queue
  * I/O device의 처리를 기다리는 프로세스의 집합
  
* 프로세스들은 각 큐들을 오가며 수행

* 프로세스 스케줄링 큐의 모습
![KakaoTalk_20201106_192308753](https://user-images.githubusercontent.com/23302973/98355526-95af2000-2065-11eb-99bb-ac480d090eea.jpg)


## 스케줄러
* Long-term scheduler(장기 스케줄러 또는 잡 스케줄러)
  - 시작 프로세스 중 어떤 것들을 ready queue에 보낼지 결정
  - 프로세스에 **메모리 및 각종 자원**을 주는 문제 -> **new 상태에 프로세스에게 메모리를 줄지, 안줄지 결정**
  - 멀티프로그래밍의 수를 제어 -> 메모리에 프로그램이 몇 개나 올라가 있는가를 나타냄
  - 시분할 시스템에는 보통 장기 스케줄러가 없음 xxx (무조건 ready)
  -> **실제로는 장기 스케줄러가 없음 (뭐징;)**
  
* Short-term scheduler(단기 스케줄러 또는 CPU 스케줄러)
  - 어떤 프로세스를 다음번에 실행시킬지 결정
  - 프로세스에 **CPU**를 주는 문제
  - 충분히 빨라야 함
  
* Medium-term scheduler(중기 스케줄러 또는 **Swapper**) -> 요걸로 조절함!!!
  - 여유 공간 마련을 위해 프로세스를 통째로 메모리에서 디스크로 쫓아냄 -> 시스템의 성능이 좋아지도록 함
  - 프로세스에게서 메모리를 뺏는 문제
  - 멀티프로그래밍의 수를 제어
  
## 프로세스 상태도(외부요인까지 확장)

![KakaoTalk_20201106_195009084](https://user-images.githubusercontent.com/23302973/98358033-71554280-2069-11eb-92d9-75d0807ee332.jpg)

