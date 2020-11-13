![KakaoTalk_20201113_170950806](https://user-images.githubusercontent.com/23302973/99044426-18d6f580-25d3-11eb-8eb9-2ab176d98e18.jpg)

## 프로그램적 해결법의 충족 조건 3가지
1. Mutual Exclusion(상호 배제)
  - 프로세스가 critical section 부분을 수행 중이면 다른 모든 프로세스들은 critical section에 들어가면 안됨
2. Progress(진행)
  - critical section에 아무도 들어가 있지 않은 상태에서, 들어가고자 하는 프로세스가 있다면 critical section에 들어가게 해줘야함
3. Bounded Waiting(유한 대기)
  - 프로세스가 critical section에 들어가려고 요청한 후부터 그 요청이 허용될 때까지 다른 프로세스들이 critical section에 들어가는 횟수에 한계가 있어야 함
  
## Algorithm 1
* 
