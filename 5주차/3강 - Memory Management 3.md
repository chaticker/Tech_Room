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
