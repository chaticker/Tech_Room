## 스케줄링 성능 척도
* 시스템 입장에서의 성능 척도
  - 이용률: 전체 시간 중에서 cpu가 놀지 않고 일한 시간의 비율-> CPU는 가능한 바쁘게 일을 시켜라!!
  - 처리량: 주어진 시간동안의 몇 개의 작업을 완료했는가?를 나타냄 -> 많이 처리 할수록 좋음

* 프로그램 입장에서의 성능 척도(고객 입장의 성능 척도)
  - 소요시간, 반환시간: CPU를 쓰러 들어와서 다 쓰고 나갈 때까지의 걸린 시간
  - 대기 시간: CPU를 쓰고자 기다리는 시간(CPU burst가 발생해서 대기하는 시간의 총 합)
  - 응답 시간: CPU를 얻겠다고 들어와서, **처음으로** CPU를 얻기 까지의 시간

## 비선점형(nonpreemptive)/ 선점형(preemptive) 스케줄링 알고리즘
* FCFS(First-Come First Served) - 비선점(별로 안 좋음)
  - 프로세스가 도착한 순서대로 처리
  - 단점: 실행시간이 짧은 프로세스가 실행시간이 긴 프로세스를 기다리는 상황이 발생
  
* SJF(Shortest-Job-First)
  - CPU burst가 가장 짧은 프로세스를 제일 먼저 처리
  - 방식
    * 비선점형: 일단 cpu를 잡으면 이번 cpu burst가 완료될 때까지 cpu를 선점 당하지 않음 
    * 선점형: 현재 수행중인 프로세스의 남은 burst time보다 더 짧은 cpu burst time을 가지는 새로운 프로세스가 도착하면 cpu를 빼앗김
  - 선점형 방식은 주어진 프로세스에 대해 **짧은 평균 대기 시간을 보장**
  - 단점
    * 기아현상: 극단적으로 짧은 것만 선호 -> 사용시간이 긴 프로세스는 처리가 안될 수 있음
    * cpu 사용시간을 미리 알 수 없음 -> 추정은 할 수 있음(과거 cpu 사용 흔적을 통해 예측)
  
* SRTF(Shortest-Remaining-Time-First)
  - 
  
* Priority Scheduling
* RR(Round Robin)
* Multilevel Queue
* Multilevel Feedback Queue
  
