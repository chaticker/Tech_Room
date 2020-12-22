## Segmentation 이어서

* 세그먼트 번호와 세그먼트 length register의 값을 비교해서 trap에 걸릴지 안걸릴지 결정
  - 세그먼트 번호 < length register 일때만 통과

![KakaoTalk_20201205_140019088](https://user-images.githubusercontent.com/23302973/101234398-46aae800-3702-11eb-9c1f-dccd3fee2a59.jpg)

## Segmentation with Paging

* 세그먼트를 여러 개의 페이지로 구성하는 기법

![KakaoTalk_20201205_141353442](https://user-images.githubusercontent.com/23302973/101234599-2714bf00-3704-11eb-9983-8a2922444902.jpg)

* 주소 변환을 위한 운영체제의 역할은 없음 -> 다 하드웨어가 해야함
    - 왜? 주소 변환을 할 때마다 운영체제가 개입을 한다면 문맥교환에 시간이 너무 많이 듦 -> 그래서 무조건 하드웨어가 해야함!!!
