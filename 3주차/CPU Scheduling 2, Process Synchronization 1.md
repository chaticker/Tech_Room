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
  - 
* Multilevel Feedback Queue
