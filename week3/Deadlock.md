
  

# DeadLock.md

작성자 : 김다인

  

---

### 동시성 제어
DBMS는 다수 사용자를 가정하며, 동시에 작동하는 다중 트랜잭션 상호 간섭 작용에서 데이터베이스를 보호할 수 있어야 한다. 이를 **동시성 제어(Concurrency Control)** 개념이라고 한다. 동시성 제어를 위해 모든 DBMS가 lock(잠금) 기능을 제공한다.

  

### 다중 버전 동시성 제어 (MVCC)
다중 버전 동시성 제어(Multi Version Concurrency Control)이란, 동시 접근을 허용하는 데이터베이스에서 동시성 제어를 위해 사용하는 방법 중 하나이다.
MVCC 모델에서 데이터에 접근하는 유저는 접근한 시간 DB의 **snapshot**을 읽고, 이 데이터에 대한 변경이 완료될 때까지 만들어진 모든 변경 사항은 **트랜잭션이 commit될 때까지 다른 DB 사용자가 볼 수 없다.**
MVCC 모델은 **lock이 필요없어서** RDBMS보다 빠르게 작동한다. 하지만 하나의 데이터에 대한 여러 버전의 데이터를 허용하기 때문에 버전 충돌이 발생할 수 있다.

  

### 교착상태

운영체제와 프로세스 처리에서 말하는 교착상태(deadlock)란 2개 이상의 작업이 서로 상대방의 작업이 끝나기를 기다리기 때문에 결과적으로 아무것도 완료되지 못하는 상태이다.
![image](https://akasai.space/static/4af8e9db0873cc641ede7e6fd96c5f75/533c1/deadlock.png)
이는 데이터베이스에서도 비슷한 개념이다. 2개 이상의 트랜잭션이 특정 테이블이나 레코드의 lock을 획득한 채 다른 트랜잭션이 소유 중인 lock을 요구하는 경우 아무것도 완료되지 못한 채 무한정 기다리게 되는데 이것을 **교착상태**라고 부른다.
MVCC 모델이 아닌 일반 동시성 제어 환경 아래에서는 트랜잭션에 갱신 연산(Insert, Update, Delete)을 실행하면 lock을 얻게 된다. 트랜잭션을 commit하지 않은 채 서로 잠금을 요청하면 교착상태가 발생한다.
교착상태 해결을 위한 방법은 다음과 같다.
* 예방 : 트랜잭션 실행 전에 필요한 데이터를 모두 locking. (다만, 이 경우 트랜잭션 병행성을 보장하진 못하며 몇몇 트랜잭션은 기아 상태에 빠질 수 있음)
* 회피 : 자원 할당 시 Time Stamp를 사용해 교착상태가 일어나지 않도록 함.
	* Wait-Die : 다른 트랜잭션이 데이터를 점유할 때 기다리거나 포기
	* Wound-Wait : 다른 트랜잭션이 데이터를 점유할 때 빼앗거나 기다림
* 낙관적 병행 제어 : 트랜잭션이 실행되는 동안 아무 검사도 하지 않고 트랜잭션이 전부 실행된 뒤 검사해 문제가 있다면 되돌림

  

---

* [안경잡이개발자 : 데이터베이스 교착 상태(Dead Lock)](https://blog.naver.com/PostView.nhn?blogId=ndb796&logNo=221243161017&parentCategoryNo=&categoryNo=1&viewDate=&isShowPopularPosts=false&from=postView)
* [MVCC - Multiversion concurrency control](https://www.joinc.co.kr/w/man/12/MVCC)
* [구루비스터디 제3절 동시성 제어](http://www.gurubee.net/lecture/2398)
* [한재엽님](https://github.com/JaeYeopHan/Interview_Question_for_Beginner/tree/master/Database#%EA%B5%90%EC%B0%A9%EC%83%81%ED%83%9C)