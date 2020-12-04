![캡asdfadsghhh처](https://user-images.githubusercontent.com/23302973/101168243-7d3f1f00-367e-11eb-98a0-1c4b62865b8b.PNG)
- 4번의 주소 변환, 1번의 실제 메모리 접근(4단계 페이지 테이블을 사용하는 경우)

![KakaoTalk_20201204_222441920](https://user-images.githubusercontent.com/23302973/101168924-8da3c980-367f-11eb-89f0-31ce66aa1a3c.jpg)

## Memory Protection
* 페이지 테이블의 각 엔트리마다 아래의 bit를 둔다

  - Protection bit
    * 페이지에 대한 접근 권한(read / write / read-only)
    
  - valid-invalid bit
    * valid는 해당 주소의 프레임에 그 프로세스를 구성하는 유효한 내용이 있음을 뜻함(접근 허용)
    * invalid는 해당 주소의 프레임에 유효한 내용이 없음을 뜻함(접근 불허)
      - 유효한 내용이 없다는 것은, **프로세스가 그 주소 부분을 사용하지 않거나 해당 페이지가 메모리에 올라와 있지 않고 swap area에 있는 경우**
      

## Inverted Page Table
* 페이지 테이블이 매우 큰 이유
  - 모든 프로세스별로 그 논리 주소에 대응하는 모든 페이지에 대해 페이지 테이블 엔트리가 존재
  - 대응하는 페이지가 메모리에 있든 아니든 간에 페이지 테이블에는 엔트리로 존재
  
* Inverted Page Table
  - 페이지 프레임 하나당 페이지 테이블에 하나의 엔트리를 둔 것
  - 각 페이지 테이블 엔트리는 각각의 물리적 메모리의 페이지 프레임이 담고 있는 내용 표시(프로세스 아이디, 프로세스의 논리 주소)
  - 단점: 테이블 전체를 탐색해야함
  - 조치: associative register사용(비쌈)

![KakaoTalk_20201204_224301217](https://user-images.githubusercontent.com/23302973/101170672-20ddfe80-3682-11eb-8cf0-bf74903ca180.jpg)


## Shared Page
* shared code
  - Re-entrant Code(Pure code)
  - read-only로 하여 프로세스 간의 하나의 코드만 메모리에 올림
  - shared code는 모든 프로세스의 논리 주소 공간에서 동일한 위치에 있어야 함
  
* private code and data
  - 각 프로세스들은 독자적으로 메모리에 올림
  - private data는 논리 주소 공간의 아무 곳에 와도 무방
  
![KakaoTalk_20201204_225034882](https://user-images.githubusercontent.com/23302973/101171484-30117c00-3683-11eb-9303-8f92c80bc23d.jpg)

* * *

## Segmentation
* 프로그램은 의미 단위인 여러 개의 세그먼트로 구성
  - 작게는 프로그램을 구성하는 함수 하나하나를 세그먼트로 정의
  - 크게는 프로그램 전체를 하나의 세그먼트로 정의 가능
  - 일반적으로는 code, data, stack 부분이 하나씩의 세그먼트로 정의됨
  
* 세그먼트는 다음과 같은 논리 단위들임
  - main()
  - function
  - global variables
  - stack
  - symbol table
  - arrays

* 페이지 기법과의 차이: 페이지는 프로그램을 구성하는 주소 공간을 같은 단위의 페이지로 나눈 것. 세그먼테이션 기법은 의미 단위로 쪼갠 것
![asdfasdfasdfasd](https://user-images.githubusercontent.com/23302973/101172511-9ba81900-3684-11eb-9f60-dee7877f0c89.PNG)

![KakaoTalk_20201204_231425968](https://user-images.githubusercontent.com/23302973/101173892-8207d100-3686-11eb-805d-a6b5734df3d6.jpg)

![asdfasdfasdf](https://user-images.githubusercontent.com/23302973/101173962-96e46480-3686-11eb-84af-f93ca4e1f874.PNG)
