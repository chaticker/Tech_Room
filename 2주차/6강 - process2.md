## Thread(경량 프로세스)
* CPU를 수행하는 단위
* Thread의 구성(얘만 독립적으로 가지는 부분)
  - program counter
  - register set
  - stack space
  
* Thread가 동료 Thread와 공유하는 부분 (=task)
  - code 부분
  - data 부분
  - OS 자원

![KakaoTalk_20201106_232920061](https://user-images.githubusercontent.com/23302973/98377285-f7808180-2087-11eb-8ab3-2b3760bb6b89.jpg)

* 장점
  - 스레드가 blocked(waiting) 상태인 동안에도 동일한 태스크 내의 다른 스레드가 실행되어 빠른 처리 가능
  - 동일한 일을 수행하는 다중 스레드가 협력하여 높은 처리율과 성능 향상을 얻을 수 있음
  - 병렬성을 높일 수 있음

## 
