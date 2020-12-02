## Local vs. Physical Address

* Local Address(논리 / 가상 주소)
  - 프로세스마다 독립적으로 가지는 주소 공간
  - 각 프로세스마다 0번지부터 시작
  - CPU가 보는 주소

* Physical Address(물리)
  - 메모리에 실제 올라가는 위치
  
* 주소 바인딩: 주소를 결정하는 것 -> 논리 주소가 물리 주소로 언제 결정되는가?

* Symbolic Address -> Local Address -> Physical Address

## 주소 바인딩

* compile time binding
  - 물리적 메모리 주소가 컴파일 시 알려짐
  - 시작 위치 변경시 재컴파일
  - 컴파일러는 절대 코드 생성

* load time binding
  - 로더의 책임하에 물리적 메모리 주소 부여
  - 컴파일러가 재배치 가능코드를 생성한 경우 가능

* execution time binding(run time binding)
  - 수행이 시작된 이후에도 프로세스의 메모리 상 위치를 옮길 수 있음
  - CPU가 주소를 참조할 때마다 바인딩을 점검
  - **하드웨어적인 지원 필요**
  
![KakaoTalk_20201202_213530923](https://user-images.githubusercontent.com/23302973/100873258-5a7a0280-34e6-11eb-8db8-35865a3d9620.jpg)

## MMU(Memory-Management Unit)

* 논리 주소를 물리 주소로 매핑해주는 **하드웨어** 디바이스

* 사용자 프로세스가 CPU에서 수행되며 생성해내는 모든 주소 값에 대해 base register(relocation register) 의 값을 더함

* user program
  - 논리 주소만을 다룸
  - 실제 물리 주소를 볼 수 없으며, 알 필요 없음
