## 비선점형(nonpreemptive)/ 선점형(preemptive) 스케줄링 알고리즘
* FCFS(First-Come First Served) - 비선점(별로 안 좋음)
  - 프로세스가 도착한 순서대로 처리
  - 단점: 실행시간이 짧은 프로세스가 실행시간이 긴 프로세스를 기다리는 상황이 발생
  
* SJF(Shortest-Job-First)
  - CPU burst가 가장 짧은 프로세스를 제일 먼저 처리(cpu사용 시간이 가장 적은 = 우선순위가 높은)
  - 방식
    * 비선점형: 일단 cpu를 잡으면 이번 cpu burst가 완료될 때까지 cpu를 선점 당하지 않음 
    * 선점형: 현재 수행중인 프로세스의 남은 burst time보다 더 짧은 cpu burst time을 가지는 새로운 프로세스가 도착하면 cpu를 빼앗김
  - 선점형 방식은 주어진 프로세스에 대해 **짧은 평균 대기 시간을 보장**
  - 단점
    * 기아현상: 극단적으로 짧은 것만 선호 -> 사용시간이 긴 프로세스는 처리가 안될 수 있음 -> aging으로 해결: 우선 순위를 높여주는 기법
    * cpu 사용시간을 미리 알 수 없음 -> 추정은 할 수 있음(과거 cpu 사용 흔적을 통해 예측)
  
* SRTF(Shortest-Remaining-Time-First)
  - 
  
* Priority Scheduling
  - 우선순위가 제일 높은 프로세스에게 cpu를 준다(정수로 우선순위를 표현: 작을수록 우선순위 높은 것)
  - 방식
    * 비선점형
    * 선점형
    
* RR(Round Robin)
  - 현대에서 쓰는 스케줄링은 RR에 기반
  - 각 프로세스는 동일한 크기의 할당 시간을 가짐 -> 할당 시간이 지나면 프로세스는 선점 당하고 ready queue의 제일 뒤에 가서 다시 줄을 선다
  - 장점: 응답시간이 빨라짐, 대기 시간이 본인이 사용하는 cpu burst 시간과 비례함 / 짧은 프로세스와 긴 프로세스가 섞여있는 경우, SJF보다 효율적임
  
* Multilevel Queue
  ![KakaoTalk_20201112_225212793](https://user-images.githubusercontent.com/23302973/98948431-c4336c00-2539-11eb-8dc8-cb3465a65f93.jpg)
  - 프로세스를 어느 줄에 넣을 것인가?
  - 우선순위가 높은 것에만 cpu를 주는가?
  
  * ready queue를 여러 개로 분할
    - foreground(interactive)
    - background(batch- no human interaction)
    
  * 각 큐는 독립적인 스케줄링 알고리즘을 가짐
    - foreground: RR
    - background: FCFS
    
  * 큐에 대한 스케줄링이 필요
    - Fixed priority scheduling
    - time slice
      * 전체의 80%는 우선순위가 높은 줄에 주고, 나머지 20%는 낮은 줄에 주는 것

* Multilevel Feedback Queue(Multilevel Queue 보완)
  - 처음 들어오는 프로세스는 우선순위가 가장 높은 큐에 넣음 
  ![KakaoTalk_20201112_230356103](https://user-images.githubusercontent.com/23302973/98949709-67d14c00-253b-11eb-8015-00c0e3665f0e.jpg)


## Multiple-processor Scheduling(별로 안 중요함)
* CPU가 여러 개 있는 상태에서의 스케줄링

  - Load sharing이 잘 되어야 함
    * 일부 프로세서에 job이 몰리지 않도록 부하를 적절히 공유하는 메커니즘이 필요 
    * 별개의 큐를 두는 방법 vs 공동 큐를 사용하는 방법
    
  - Symmetric Multiprocessing(SMP)
    * 각 프로세서가 각자 알아서 스케줄링 결정 (모두가 대등함)
    
  - Asymmetric Multiprocessing
    * 하나의 프로세서가 시스템 데이터의 접근과 공유를 책임지고, 나머지 프로세서는 거기에 따르는 방식
    
## Real-Time Scheduling(**정해진 시간** 안에 반드시 실행이 되어야 함)
* Hard real-time systems
  - Hard real-time task는 정해진 시간 안에 **반드시** 끝내도록 스케줄링 해야 함
  
* Soft real-time computing
  - Soft real-time task는 일반 프로세스에 비해 높은 우선순위를 갖도록 해야 함
  
## Thread Scheduling
* Local Scheduling
  - User level thread(운영체제가 스레드의 존재를 모르는 경우)의 경우 사용자 수준의 thread library에 의해 어떤 스레드를 스케줄링할지 결정
  
* Global Scheduling
  - Kernel level thread(운영체제가 스레드의 존재를 아는 경우)의 경우 일반 프로세스와 마찬가지로 커널의 단기 스케줄러가 어떤 스레드를 스케줄링 할지 결정
  
## 어떤 알고리즘이 좋은지 평가하는 방법
![KakaoTalk_20201112_232637139](https://user-images.githubusercontent.com/23302973/98952233-8f75e380-253e-11eb-888a-84369e33d431.jpg)



# Process Synchronization
* 데이터의 접근
  ![KakaoTalk_20201112_232856879](https://user-images.githubusercontent.com/23302973/98953396-fcd64400-253f-11eb-985c-84319d3bb408.png)

* Race Condition(경쟁 상태)
  ![KakaoTalk_20201112_233807894](https://user-images.githubusercontent.com/23302973/98953566-2c854c00-2540-11eb-992b-f9c12c371737.jpg)

  - os에서 race condition은 언제 발생?
    * 커널 수행 중 인터럽트 발생 시
    ![KakaoTalk_20201112_234629831](https://user-images.githubusercontent.com/23302973/98954671-5f7c0f80-2541-11eb-9d84-00b1f0c18483.jpg)

    * 프로세스가 시스템 콜을 하여 커널 모드로 수행 중인데, 문맥교환이 일어나는 경우
    ![KakaoTalk_20201112_235329704](https://user-images.githubusercontent.com/23302973/98955541-5b042680-2542-11eb-871e-c6dc6b0917ef.jpg)
    
    * 멀티프로세서에서 공유 메모리 내의 커널 데이터
    ![KakaoTalk_20201112_235813463](https://user-images.githubusercontent.com/23302973/98956083-f72e2d80-2542-11eb-966a-fe583219f4c3.jpg)
    
* Process Synchronization 문제

    
