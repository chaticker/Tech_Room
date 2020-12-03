## Paging

* 프로세스의 가상 메모리를 동일한 사이즈의 페이지 단위로 나눔
* 가상 메모리의 내용이 페이지 단위로 불연속 하게 저장됨
* 일부는 backing storage에, 일부는 물리 메모리에 저장

* basic method
  - 물리 메모리를 동일한 크기의 프레임으로 나눔
  - 논리 메모리를 동일한 크기의 페이지로 나눔(프레임과 같은 크기)
  - 모든 가용 프레임들을 관리
  - 페이지 테이블을 사용하여 논리 주소를 물리 주소로 변환
  - 외부 단편화 발생 x
  - 내부 단편화 발생 가능

![KakaoTalk_20201203_231348118](https://user-images.githubusercontent.com/23302973/101032556-435a1400-35bd-11eb-9d11-b3614cd9a033.jpg)

![KakaoTalk_20201203_231905864](https://user-images.githubusercontent.com/23302973/101035106-017d9d80-35be-11eb-985f-ddadde07aa5b.jpg)

* 페이지 테이블은 메인 메모리에 상주
* page-table base register(PTBR)가 페이지 테이블을 가리킴
* page-table length register(PTLR)가 테이블 크기 보관
* 모든 메모리 접근 연산에는 **2번의 메모리 접근**이 필요
  - 페이지 테이블 접근 1번(주소 변환을 위함), 실제 데이터/연산 접근 1번(메모리 접근을 위함) -> 시간이 오래 걸림
* 위의 시간 문제에서 속도 향상을 위해 associative register 혹은 translation look-aside buffer(TLB)라 불리는 고속의 lookup 하드웨어 캐시 사용

![KakaoTalk_20201203_233731337](https://user-images.githubusercontent.com/23302973/101042450-908bb500-35c0-11eb-9a1d-09f45b0490c1.jpg)

* 연관 레지스터(TLB): 한 번에 평행 서치 가능 (여러 개)
  - TLB에는 페이지 테이블 중 일부만 존재
* 주소 변환
  - 페이지 테이블 중 일부가 TLB에 보관되어 있음
  - 만약 해당 페이지가 TLB에 있는 경우 곧바로 프레임 얻음
  - 그렇지 않은 경우 메인 메모리에 있는 페이지 테이블로부터 프레임 얻음
  - TLB는 문맥 교환 때 오래된 엔트리를 삭제함(flush) - 프로세스마다 다르기 때문에
  
* two-level page table(시간x /공간이 줄어드는 게 목표)
  - 현대의 컴퓨터는 주소 공간이 매우 큰 프로그램 지원
    * 32bit 주소 사용시 : 2^32(4G)의 주소 공간
      - 페이지 크기가 4K시 1M개의 페이지 테이블 엔트리 필요
      - 각 페이지 엔트리가 4Byte시 프로세스당 4M의 페이지 테이블 필요
      - 그러나, 대부분의 프로그램은 4G의 주소 공간 중 지극히 일부분만 사용하므로 페이지 테이블 공간이 심하게 낭비 됨
      
      - 따라서, 페이지 테이블 자체를 **페이지**로 구성
      - 사용되지 않는 주소 공간에 대한 outer 페이지 테이블의 엔트리 값은 NULL(대응하는 inner 페이지 테이블이 없음)

![KakaoTalk_20201204_002240859](https://user-images.githubusercontent.com/23302973/101049978-5d005900-35c7-11eb-802b-68ec4d62dd19.jpg)
![KakaoTalk_20201204_002241150](https://user-images.githubusercontent.com/23302973/101049981-5e318600-35c7-11eb-8229-a2a3a1797b4a.jpg)

