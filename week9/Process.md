
# Process
작성자: 김다인

---

## 프로그램
프로그램은 컴퓨터에서 실행될 때 특정 작업을 수행하는 일련의 **명령어들의 모음**이다. 대부분의 프로그램은 하드디스크 등의 매체(저장장치)에 **바이너리 형식의 파일**로 저장되어 있다가 사용자가 실행시키면 메모리로 적재되어 실행된다.

## 프로그램과 프로세스
프로그램은 일반적으로 저장장치에 **저장된 실행 코드**를 뜻하고, 프로세스는 프로그램을 구동해 **프로그램 자체와 프로그램의 상태가 메모리에서 실행**되는 작업 단위를 지칭한다. 

## 프로세스
프로세스는 **컴퓨터에서 연속적으로 실행되는 프로그램**을 말한다. 운영체제로부터 CPU, 주소 공간, 메모리 영역 등의 시스템 자원을 할당받는 작업 단위를 뜻하기도 한다. 프로세스는 메인 스레드를 포함해 최소 1개의 스레드를 소유한다.    
프로세스는 그 프로세스만의 **고유한 공간과 자원을 할당받아 사용**한다. 이것이 스택 외 다른 영역을 공유하는 스레드와의 차이점으로 꼽히기도 한다.  
프로세스가 할당받는 주소 공간은 *코드, 데이터, 스택*으로 나뉜다.
* 코드 : 프로그램 소스 코드
* 데이터 : 전역/정적 변수, 배열 등
* 스택 : 함수, 지역 변수
* 힙 : 동적 할당 시 사용

### 프로세스의 상태
<br>
<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/8/83/Process_states.svg/330px-Process_states.svg.png">
<br>
커널 내에 있는 준비 큐, 대기 큐, 실행 큐 등으로 프로세스 상태를 관리하게 된다.  

* 생성 : create. 프로세스 생성 중.
* 실행 : running. 프로세스가 CPU를 차지해 명령어들이 실행되는 중.
* 준비 : ready. CPU를 사용할 수 있는 상태의 프로세스로 CPU 할당을 대기 중.
* 대기 : waiting. 보류(block)라고 부르기도 함. 프로세스가 입출력 완료, 시그널 수신 등 사건을 기다리는 상태.
* 종료 : terminate. 프로세스 실행 종료.

위와 같은 상태에서 프로세스는 다음과 같이 **상태 전이**를 하게 된다.  

* 디스패치 (ready -> running)
	* 준비 큐의 맨 앞 프로세스가 CPU를 점유
* 보류 (running -> waiting)
	* 실행 중인 프로세스가 허가된 시간을 다 쓰기 전 입출력 동작을 해야 하는 경우 CPU를 스스로 반납
* wake up (waiting -> ready)
	* 입출력 작업 종료 등 기다리던 사건이 일어났을 때 보류 상태에서 준비 상태로 전이
* timeout (running -> ready)
	* 실행 중이던 프로세스가 할당받은 일정 시간(time slice)이 끝나 준비 큐로 들어감

### 프로세스 제어 블록
PCB(Process Control Block)는 특정 **프로세스에 대한 메타 정보를 저장**하는 운영체제의 자료구조이다.  
운영체제는 프로세스 관리를 위해 프로세스를 생성하면서 PCB도 함께 생성한다. PCB는 프로세스의 중요한 정보를 포함하기 때문에 보호된 메모리 영역 안에 남는다.  
PCB는 연결 리스트 방식으로 관리하며, PCB가 생성될 때마다 PCB 리스트 헤드에 붙게 된다.   
프로세스는 CPU 시간을 할당받아 작업하다가도 시간을 다 쓰면 진행하던 작업을 PCB에 저장한 후 CPU를 반납한다. 이후 해당 프로세스가 다시 CPU를 점유하게 되면 PCB에 저장된 내용을 불러 이전에 종료된 시점부터 다시 작업을 수행한다. 즉, **앞으로 다시 수행할 프로세스에 관한 저장 값을 PCB에 저장**하는 것이다.  

#### 포함 정보
* 프로세스 식별자 (Process ID, PID)
* 프로세스 상태 (create, ready, running, waiting, terminated)
* 프로그램 카운터(Program Counter) : 프로세스가 다음에 실행할 명령어 주소를 담음
* CPU 레지스터 및 일반 레지스터
* CPU 스케줄링 정보 (우선 순위, 최종 실행시각, CPU 점유시간 등)
* 메모리 관리 정보 (해당 프로세스의 주소 공간 등)
* 프로세스 계정 정보 (페이지 테이블, 스케줄링 큐 포인터, 부모 등)
* 입출력 상태 정보 (프로세스에 할당된 입출력 장치들과 열린 파일 목록)

### Context Switching
<img src="https://t1.daumcdn.net/cfile/tistory/994590345BB1B4DB2F" />
<br>
Context Switch, 문맥 교환은 하나의 프로세스가 CPU를 사용 중인 상태에서 다른 프로세스가 CPU 사용을 위해 이전 프로세스 상태(문맥)를 보관하고 새로운 프로세스 상태를 적재하는 작업을 말한다. 수행 중인 프로세스가 변경될 때 CPU 레지스터 정보가 변경되는 것이기도 하다.  
CPU가 이전 프로세스 상태를 PCB에 보관하고, 다른 프로세스 정보를 PCB에서 읽어 레지스터에 적재하는 과정으로, 인터럽트가 발생하거나, 실행 중인 프로세스가 CPU 사용 시간을 모두 소비하거나, 입출력을 위해 대기해야 하는 경우에 발생한다.   
한 프로세스의 문맥은 해당 프로세스의 PCB에 기록된다.  

### 멀티 프로세스
멀티 프로세스는 **하나의 컴퓨터에 여러 CPU를 장착해 하나 이상의 프로세스들을 동시에 처리**하는 병렬 구조를 말한다.  
이 경우 한 프로세스에 문제가 생겨도 다른 프로세스에 영향을 주지 않기 때문에 안전하지만, 각각 독립된 메모리 영역을 가지므로 작업량이 많을수록 오버헤드가 발생한다는 단점이 있다. 또한 Context Switching으로 성능 저하가 발생할 수 있다.  

### 프로세스 동기화
**동일한 자원을 동시에 접근하는 작업을 실행하는 코드 영역**을 임계 영역(Critical Section, 공유 변수 영역)이라고 한다. 멀티 프로세스 환경이나 멀티 스레드 환경에서 프로세스(혹은 스레드)들이 임계 영역을 함께 사용할 수 있는 프로토콜을 설계하는 것이 중요하다.  
임계 영역으로 지정되어야 할 코드 영역이 제대로 지정되지 않는다면, *임계 영역 문제*가 발생한다. 이 문제의 예시로 입출금 문제, 생산자-소비자 문제 등이 알려져 있다.  
문제 해결을 위해서는 다음과 같은 조건이 필요하다.
* 상호 배제
	* 어떤 프로세스가 임계 영역에서 실행 중이라면 다른 프로세스들은 임계 영역에서 실행될 수 없음
* 진행
	* 임계 영역에서 실행 중인 프로세스가 없고, 별도 동작이 없는 프로세스들만 임계 영역 진입 후보가 될 수 있음
* 한정된 대기
	* 어떤 프로세스가 임계 영역에 진입을 신청하고 수락될 때까지, 다른 프로세스들이 임계 영역에 진입하는 횟수에는 제한이 필요함. 즉, 해당 프로세스가 무한정 대기해서는 안 됨

문제 해결법은 뮤텍스 락 혹은 세마포어가 있다. (다른 문서에서 설명)

---
* [위키백과 : 컴퓨터 프로그램](https://ko.wikipedia.org/wiki/%EC%BB%B4%ED%93%A8%ED%84%B0_%ED%94%84%EB%A1%9C%EA%B7%B8%EB%9E%A8)
* [위키백과 : 프로세스](https://ko.wikipedia.org/wiki/%ED%94%84%EB%A1%9C%EC%84%B8%EC%8A%A4)
* [위키백과 : 프로세스 제어 블록](https://ko.wikipedia.org/wiki/%ED%94%84%EB%A1%9C%EC%84%B8%EC%8A%A4_%EC%A0%9C%EC%96%B4_%EB%B8%94%EB%A1%9D)
* [위키백과 : 문맥 교환](https://ko.wikipedia.org/wiki/%EB%AC%B8%EB%A7%A5_%EA%B5%90%ED%99%98)
* [위키백과 : 임계 구역](https://ko.wikipedia.org/wiki/%EC%9E%84%EA%B3%84_%EA%B5%AC%EC%97%AD)
* [tech-interview github repository](https://github.com/WeareSoft/tech-interview/blob/master/contents/os.md)
* [Interview_Question_for_Beginner github repository](https://github.com/JaeYeopHan/Interview_Question_for_Beginner/tree/master/OS)
* [프로세스의 주소 공간](https://github.com/gyoogle/tech-interview-for-developer/blob/master/Computer%20Science/Operating%20System/Process%20Address%20Space.md)
* [PCB & Context Switching](https://github.com/gyoogle/tech-interview-for-developer/blob/master/Computer%20Science/Operating%20System/PCB%20%26%20Context%20Switcing.md)