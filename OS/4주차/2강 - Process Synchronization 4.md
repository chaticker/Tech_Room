## Monitor

![캡처fggh](https://user-images.githubusercontent.com/23302973/99818136-2f5fec80-2b91-11eb-9062-0be5545805a0.PNG)

* 프로세스의 동시 접근을 모니터가 해결해줌으로써 프로그램의 부담을 줄여줌
* 프로세스가 공유 데이터에 접근할 때, 모니터를 통해서만 접근할 수 있도록 함 
* active한 코드 하나만 모니터 안에서 수행할 수 있도록 함(모니터 자체가 자동적으로 제어 하는 것임)
* 모니터에서는 lock을 걸고 푸는 게 필요하지 않음

![캡처dfdfd](https://user-images.githubusercontent.com/23302973/99820381-0ab94400-2b94-11eb-8706-12b7d35a7937.PNG)

![캡dfasd처](https://user-images.githubusercontent.com/23302973/99820560-4bb15880-2b94-11eb-9ee5-8420e25dc876.PNG)

* lock 걸고 푸는 부분이 다 빠짐(세마포어 코드와 비교했을 때)
* 그냥 잠들어 있는 프로세스를 깨우라는 코드로 존재

![캡처jkkjk](https://user-images.githubusercontent.com/23302973/99821039-de51f780-2b94-11eb-926f-9925376145d3.PNG)

* 젓가락을 잡는 문제는 모니터 내부에 존재
* 모니터 외의 코드에서는 lock에 대한 코드가 필요 없음 




