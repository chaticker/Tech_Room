![캡처](https://user-images.githubusercontent.com/23302973/97690915-00e67880-1ae1-11eb-9dea-21060fa84f0f.PNG)

----mode bit
* 사용자 프로그램의 잘못된 수행으로 다른 프로그램 및 운영체제에 피해가 가지 않도록 하기 위한 보호 장치 필요
* mode bit을 통해 하드웨어적으로 두 가지 모드의 operation 지원
  - 1 사용자 모드: 사용자 프로그램 수행
  - 0 모니터 모드: OS 코드 수행 **커널모드, 시스템 모드**
  
  ->보안을 해칠 수 있는 중요한 명령어는 모니터 모드에서만 수행 가능한 특권명령으로 규정
  ->interrupt나 exception 발생시 하드웨어가 mode bit을 0으로 바꿈
  ->사용자 프로그램에게 CPU를 넘기기 전에 mode bit을 1로 셋팅
