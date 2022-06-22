# Scheduling
작성자: 김다인

---

## Scheduling
스케줄링은 **다중 프로그래밍을 가능하게 하는 운영 체제의 동작 기법**이다. 운영 체제는 CPU 등의 자원을 프로세스들에게 적절히 배분함으로써 시스템 성능을 개선할 수 있다.  
스케줄러는 아래 목록 중 하나 혹은 그 이상을 목표로 한다.  
* throughput(산출량) 최대화 -> 사용률 최대화
* fairness(공평성) 최대화 -> 기아 현상 최소화
* wait time(대기시간) 최소화
* latency(지연), response time(응답시간) 최소화 -> 오버헤드 최소화

### 스케줄링의 유형
#### 장기 스케줄링
* 1단계로, 작업 스케줄링이라고도 함
* **어느 작업부터** 시스템 자원들을 사용하게 할지, **ready queue로 보낼지를 결정**
* 작업들이 시스템에 진입하는 것을 승인하는 것이기 때문에 승인 스케줄링(Admission scheduling)이라고도 함
* 프로세스는 **new -> ready 상태**가 됨

#### 중기 스케줄링 (Swapper)
* 2단계로, 어느 프로세스부터 CPU를 차지할 수 있게 할지 결정
* **프로세스들을 보류시키고 다시 활성화**시키는 기법을 사용해 시스템에 대한 단기적 부하 조절
* 작업 승인(1단계)과 CPU 배당(3단계) 사이 완충 역할
* 프로세스는 **ready -> suspended** 상태가 됨

#### 단기 스케줄링 (CPU Scheduler)
* 3단계로, CPU가 사용 가능한 경우 **ready queue의 프로세스들 중 어느 프로세스에게 CPU를 할당할지 결정**
* CPU와 메모리 사이 스케줄링 담당
* 프로세스는 **ready -> running -> waiting -> ready** 상태가 됨


### 정적 스케줄링과 동적 스케줄링
프로세스 **우선순위 변동 여부**에 따라 정적 스케줄링과 동적 스케줄링으로 구분할 수도 있다.  
**정적** 스케줄링은 프로세스에 부여된 **우선순위가 변경되지 않는 고정**우선순위 스케줄링이며, *동적* 스케줄링은 스케줄링 과정에서 프로세스의 *우선순위를 변동시키는 유동*우선순위 스케줄링이다.  

### 프로세스 상태 전이
<img src="https://www.researchgate.net/publication/332546783/figure/fig3/AS:749937696464896@1555810488119/Process-state-transition-diagram.png">
<br>

* 승인 (admitted)
	* 프로세스 생성 가능하여 승인
* 스케줄러 디스패치
	* ready(준비) 상태 프로세스 중 하나를 선택해 실행
* 인터럽트
	* 예외, 입출력, 이벤트 발생 등으로 실행 중인 프로세스를 준비 상태로 변경 후 해당 작업을 먼저 처리
* 입출력 또는 이벤트 대기 (I/O or Event Wait)
	* 실행 중인 프로세스가 입출력, 이벤트를 처리해야 하는 경우 입출력/이벤트가 끝날 때까지 대기 상태로 만듦
* 입출력 또는 이벤트 완료 (I/O or Event Completion)
	* 입출력/이벤트가 끝난 프로세스를 준비 상태로 전환해 스케줄러에 의해 선택될 수 있도록 만듦

### 스케줄링 결정 시점
1. running -> waiting (수행 -> 대기)
2. running -> ready (수행 -> 준비)
3. waiting -> ready (대기 -> 준비)
4. running -> terminated (수행 -> 종료)

### 비선점형과 선점형
**스케줄링 적용 시점**에 따라 비선점형과 선점형 2가지로 구분할 수 있다. 비선점형은 위의 결정 시점 중 1번, 4번 상황에서만 수행되고 선점형은 모든 상황에서 수행된다.  

#### 비선점형 스케줄링
어떤 **프로세스가 CPU를 할당 받으면 해당 프로세스가 종료되거나 입출력 요구가 발생해 자발적으로 중지될 때까지 계속 실행**되도록 한다.  
장점으로는 순서대로 처리되는 **공정성**, 다음에 처리할 프로세스와 관계 없이 **예상할 수 있는 응답 시간**, **낮은 스케줄러 호출** 빈도, **적은 오버헤드**가 있다. 이 스케줄링은 일괄 처리 시스템에 적합하다.  
단점으로는 CPU 사용 시간이 긴 한 프로세스가 다른 사용 시간이 짧은 프로세스들을 기다리게 할 수 있으므로, *처리율(throughput)이 저하*될 수 있다.  

#### 선점형 스케줄링
어떤 프로세스가 CPU를 할당받아 실행 중이라도 **다른 프로세스가 실행 중인 프로세스를 중지하고 CPU를 강제로 점유**할 수 있다.  
장점으로는 모든 프로세스에게 CPU 사용 시간을 동일하게 부여할 수 있어 **기아 현상을 막을 수 있다**는 점이다. 이 스케줄링은 빠른 응답 시간을 요구하는 대화식 시분할 시스템에 적합하다.  
*처리 시간을 예측하기 어렵다*는 단점이 있다.  
  
언뜻 볼 때 비선점형과 선점형의 설명이 바뀐 듯한데, 이 '선점'이라는 것은 프로세스 입장에서 선점이 아니라 **운영체제 입장**에서 쓴 것이다.  
**운영체제가 CPU 자원을 선점**하고 있다가 각 프로세스 요청이 있을 때 특정 요건들을 기준으로 자원을 배분하는 방식이 선점형 스케줄링이다.  

### 스케줄링 알고리즘
스케줄링 알고리즘 작성에는 시스템이 일괄 처리(batch)인지 대화형인지와, CPU와 I/O 사용 비율, 우선 순위 부여 여부와 부여할 경우 프로세스 선점 정도, page fault 정도가 고려된다.

#### 비선점형 알고리즘
* FCFS (First Come First Served)
	* 흔히 FIFO라고 알고 있는 형태. **먼저 자원 사용을 요청**한 프로세스에게 자원을 할당해 주는 방식
	* **큐에 도착한 순서**대로 CPU 할당
	* CPU를 할당받으면 CPU 점유 시간 완료 시까지 CPU를 반환하지 않음
	* 실행 시간이 긴 프로세스가 먼저 도착하면 뒤의 실행 시간이 짧은 프로세스들의 대기 시간이 늘어나 결국 *평균 대기 시간의 연장*을 초래할 수 있음
* SJF (Shortest Job First)
	* 평균 대기 시간을 최소화하기 위해 **다른 프로세스가 먼저 도착했어도 CPU 점유 시간이 짧은 프로세스에게 먼저 CPU 할당**
	* 장기 스케줄링 및 짧은 작업에 더 유리한 방식
	* 요구 시간이 긴 프로세스는 요구 시간이 짧은 프로세스에게 항상 양보되어 *기아 현상*이 일어날 수 있음
* HRRN (Highest Response-Ratio Next)
	* 프로세스 처리 **우선 순위를 CPU 처리 시간과 해당 프로세스의 대기 시간을 동시에 고려**해 선정
	* SJF의 단점 보완
	* 우선순위 = (대기시간 + 실행시간) / 실행시간

#### 선점형 알고리즘
* RR (Round Robin)
	* 시분할 시스템을 위해 설계된 선점형 스케줄링. 프로세스들 간 **우선순위를 두지 않고 순서대로 시간 단위(time quantum)로 CPU를 할당**
	* 시간 단위 동안 수행한 프로세스는 준비 큐의 끝으로 다시 들어감
	* context switching의 오버헤드는 크지만 응답 시간이 짧아져 사용 시간이 제각각인 프로세스들이 섞여 있는 경우 및 실시간 시스템에 유리함
	* 설정한 시간 단위가 너무 커지면 FCFS와 다를 바가 없어지지만, 너무 작으면 잦은 문맥 교환으로 오버헤드가 커지기 때문에 적절한 시간 단위를 설정해야 함
* SRTF (Shortest Remaining Time First)
	* SJF 스케줄링을 선점 형태로 수정한 알고리즘
	* 현재 **작업 중인 프로세스의 남은 CPU 사용 시간보다 더 짧은 CPU 사용 시간을 갖는 프로세스가 도착하면 현재 프로세스를 중단시키고 새로 들어온 프로세스 처리를 시작**
	* SJF와 마찬가지로 *기아 현상* 우려
	* 새로운 프로세스가 도착할 때마다 다시 스케줄링하기 때문에 *CPU 사용 시간을 제대로 측정할 수 없음*
* 다단계 큐
	* 커널 내의 **준비 큐를 여러 큐로 분리해 큐 사이에도 우선순위 부여**
	* 각각의 큐에 대해 서로 다른 스케줄링 알고리즘을 적용하기도 함
	* 우선순위가 낮은 큐에서 프로세스 실행이 안 되는 것을 방지하고자 큐마다 다른 시간 단위를 설정 (우선순위가 높을수록 작은 시간 단위)
* 다단계 피드백 큐
	* 다단계 큐에서 발전된 형태로, **프로세스들이 큐를 갈아탈 수 있음**
	* 작업들이 서로 다른 유형의 작업들로 분류될 경우 사용됨
	* 짧은 작업과 입출력 관련 프로세스에 우선권을 주며, CPU 사용량에 따라 프로세스 분류
	* 처리 시간이 짧은 프로세스를 먼저 처리하기 때문에 **평균 반환 시간 절약**

### 스케줄링 알고리즘의 평가
* CPU 사용률 (CPU Utilization)
	* 전체 시스템 시간 중 CPU가 작업을 처리하는 시간 비율
* 처리량 (Throughput)
	* CPU가 단위 시간당 처리하는 프로세스 개수
* 응답 시간 (Response Time)
	* 대화식 시스템에서 요청 후 응답이 오기 시작할 때까지의 시간
* 대기 시간 (Waiting Time)
	* 프로세스가 준비 큐에서 대기하는 시간의 합
* 반환 시간 (Turnaround Time)
	* 프로세스가 시작해서 끝날 때까지 걸리는 시간

---
* [위키백과 : 스케줄링 (컴퓨팅)](https://ko.wikipedia.org/wiki/%EC%8A%A4%EC%BC%80%EC%A4%84%EB%A7%81_(%EC%BB%B4%ED%93%A8%ED%8C%85))
* [위키백과 : Scheduling (computing)](https://en.wikipedia.org/wiki/Scheduling_(computing))
* [tech-interview-for-developer/CPU Scheduling](https://github.com/gyoogle/tech-interview-for-developer/blob/master/Computer%20Science/Operating%20System/CPU%20Scheduling.md)
* [Part 1-4 운영체제](https://github.com/JaeYeopHan/Interview_Question_for_Beginner/tree/master/OS#%EC%8A%A4%EC%BC%80%EC%A4%84%EB%9F%AC)