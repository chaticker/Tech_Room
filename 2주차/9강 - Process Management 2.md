## 프로세스 생성

* copy-on-write: write가 발생했을때, 그 때 copy를 하겠다는 것 -> 그 이전까지는 부모 것을 그대로 공유 함

### fork() 시스템 콜

![KakaoTalk_20201107_112202938](https://user-images.githubusercontent.com/23302973/98429682-870b4c00-20eb-11eb-90fa-9200e2114e5f.jpg)

### exec() 시스템 콜

