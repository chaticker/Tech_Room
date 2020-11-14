## 세마포어
![KakaoTalk_20201114_125736715](https://user-images.githubusercontent.com/23302973/99139083-08795600-2679-11eb-95ef-c48c603134af.jpg)

* 세마포어의 두 종류
  - Counting 세마포어
    * 도메인이 0 이상인 임의의 정수값 -> 자원의 개수가 여러개라 남으면 가져다 쓸 수 있음
    * 주로 resource counting에 사용
    
  - Binary 세마포어(=mutex)
    * 0 또는 1 값만 가질수 있는 세마포어
    * 주로 mutual exclusion(lock/unlock)에 사용

-> 세마포어를 사용하면 훨씬 간단한 프로그래밍 가능

##Block / Wakeup 방식
![KakaoTalk_20201114_130328666](https://user-images.githubusercontent.com/23302973/99139166-dae0dc80-2679-11eb-8aa9-26793fc1277b.jpg)

![KakaoTalk_20201114_130913669](https://user-images.githubusercontent.com/23302973/99139294-a6b9eb80-267a-11eb-9df4-55dbf6f2e695.jpg)

![캡ljljl](https://user-images.githubusercontent.com/23302973/99139302-c81ad780-267a-11eb-9251-8f5c83f75221.PNG)

## Deadlock and Starvation
![KakaoTalk_20201114_132132255](https://user-images.githubusercontent.com/23302973/99139477-5ba0d800-267c-11eb-8573-c2af180a9793.jpg)

