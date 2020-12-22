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
  
![KakaoTalk_20201202_214625652](https://user-images.githubusercontent.com/23302973/100874411-e04a7d80-34e7-11eb-8bee-609ff16efd41.jpg)

![캡asdf처](https://user-images.githubusercontent.com/23302973/100874517-0a9c3b00-34e8-11eb-99c5-85fbb013c6a2.PNG)

## Dynamic Loading(메모리로 올리는 것)

* 프로세스 전체를 메모리에 미리 다 올리는 것이 아니라 해당 루틴이 불려질 때 메모리에 로드 하는 것
* 메모리 이용성 향상
* 가끔씩 사용되는 많은 양의 코드의 경우 유용(ex.오류 처리 루틴)
* 운영체제의 특별한 지원 없이 프로그램 자체에서 구현 가능(os는 라이브러리를 통해 지원 가능)

## Overlay

* 메모리에 프로세스의 부분 중 실제 필요한 정보만을 올림
* 프로세스의 크기가 메모리보다 클 때 유용
* 운영체제의 지원없이 사용자에 의해 구현
* 작은 공간의 메모리를 사용하던 초창기 시스템에서 수작업으로 프로그래머가 구현

->둘의 차이점: 라이브러리를 사용하기 때문에 프로그래머가 복잡한 코딩을 할 필요 없음/ 운영체제의 지원이 없고, 프로그래머가 코딩을 통해 구현해야 함 

## Swapping

* 프로세스를 일시적으로 메모리에서 **backing store**로 쫓아내는 것
* backing store(swap area): 디스크 - 많은 사용자의 프로세스 이미지를 담을 만큼 충분히 빠르고 큰 저장 공간
* swap in / swap out
  - 일반적으로 중기 스케줄러(swapper)에 의해 swap out시킬 프로세스 선정
  - 우선순위 기반 CPU 스케줄링 알고리즘
    * 우선순위가 낮은 프로세스를 swapped out시킴
    * 우선순위가 높은 프로세스를 메모리에 올려 놓음
  - 컴파일 타임 혹은 로드 타임 바인딩에서는 원래 메모리 위치로 swap in 해야 함
  - execution time binding에서는 추후 빈 메모리 영역 아무 곳에나 올릴 수 있음
  - swap time은 대부분 transfer time(swap 되는 양에 비례하는 시간)임
  
## Dynamic Linking

* Linking을 실행 시간까지 미루는 기법

* static linking
  - 라이브러리가 프로그램의 실행 파일 코드에 이미 포함됨 
  - 실행 파일의 크기가 커짐
  - 동일한 라이브러리를 각각의 프로세스가 메모리에 올리므로 메모리 낭비
  
* Dynamic linking
  - 라이브러리가 실행 시 연결됨(실행 파일에 포함 x)
  - 라이브러리 호출 부분에 라이브러리 루틴의 위치를 찾기 위한 stub이라는 작은 코드를 둠
  - 라이브러리가 이미 메모리에 있으면 그 루틴의 주소로 가고 없으면 디스크에서 읽어옴
  - 운영체제의 도움이 필요
  
## Allocation of Physical Memory

* 메모리는 일반적으로 두 영역으로 나뉘어 사용
  - OS 상주 영역
    * 인터럽트 벡터와 함께 낮은 주소 영역 사용
  - 사용자 프로세스 영역
    * 높은 주소 영역 사용

* 사용자 프로세스 영역의 할당 방법
  - contiguous allocation: 각각의 프로세스가 메모리의 연속적인 공간에 적재되도록 하는 것(연속 할당)
    * fixed partition allocation(고정 분할)
    * variable partition allocation(가변 분할)
  - noncontiguous allocation: 하나의 프로세스가 메모리의 여러 영역에 분산되어 올라갈 수 있음(불연속 할당)
    * paging
    * segmentation
    * paged segmentation
    
    
### contiguous allocation(연속 할당)

* 고정분할 방식
  - 물리적 메모리를 몇 개의 영구적 분할로 나눔
  - 분할의 크기가 모두 동일한 방식과 서로 다른 방식 존재
  - 분할당 하나의 프로그램 적재
  - 융통성이 없음
    * 동시에 메모리에 load되는 프로그램의 수가 고정됨
    * 최대 수행 가능 프로그램 크기 제한
  - internal fragmentation 및 external fragmentation 발생(내,외부 조각) 
  
* 가변 분할 방식
  - 프로그램의 크기를 고려해서 할당
  - 분할의 크기, 개수가 동적으로 변함
  - 기술적 관리 기법 필요
  - external fragmentation 발생
  
![KakaoTalk_20201203_002257719](https://user-images.githubusercontent.com/23302973/100892504-bef48c00-34fd-11eb-9cd9-7f4e7be7d199.jpg)

![asdfasdfasdgas](https://user-images.githubusercontent.com/23302973/100892682-f105ee00-34fd-11eb-9178-97f4a56373a8.PNG)

* Dynamic Storage-Allocation Problem: 가변 분할 방식에서 size n인 요청을 만족하는 가장 적절한 hole을 찾는 문제
  - first-fit
    * size가 n 이상인 것 중 최초로 찾아지는 hole에 할당
  - best-fit 
    * size가 n 이상인 가장 작은 hole을 찾아서 할당
    * hole들의 리스트가 크기순으로 정렬되지 않은 경우 모든 hole 리스트를 탐색 해야함
    * 많은 수의 아주 작은 hole들이 생성됨
  - worst-fit
    * 가장 큰 hole에 할당
    * 역시 모든 리스트를 탐색해야 함
    * 상대적으로 아주 큰 hole들이 생성
    
  - compaction
    * 외부 조각 문제를 해결하는 한 가지 방법 -> 한 군데에 몰아 넣기
    * 사용 중인 메모리 영역을 한 군데로 몰고 hole들을 다른 한 곳으로 몰아 큰 block을 만드는 것
    * 매우 큰 비용이 드는 방법(전체 프로그램의 바인딩과 관련되어 있기 때문에)
    * 최소한의 메모리 이동으로 compaction하는 방법
    * 프로세스의 주소가 실행 시간에 동적으로 재배치 가능한 경우에만 수행될 수 있음
    
### noncontiguous allocation(불연속 할당)
-> 다음 시간에 ~
