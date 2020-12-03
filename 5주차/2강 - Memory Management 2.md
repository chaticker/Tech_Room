## Paging

* 프로세스의 가상 메모리를 동일한 사이즈의 페이지 단위로 나눔
* 가상 메모리의 내용이 페이지 단위로 불연속 하게 저장됨
* 일부는 backing storage에, 일부는 physical memor에 저장

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
