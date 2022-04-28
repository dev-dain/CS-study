
# SQLInjection.md
작성자 : 김다인

---
### SQL 인젝션
SQL 삽입은 프로그램 보안상의 허점을 의도적으로 이용해, 악의적인 SQL문을 실행되게 함으로써 데이터베이스를 비정상적으로 조작하는 코드 주입 공격 방법이다.  

### 공격
* 인증 우회 (Auth Bypass)
	* 예를 들어, username과 password를 받아 로그인하는 프로그램이 있다고 할 때, 제대로 보안이 되어 있지 않은 프로그램의 경우 다음의 공격을 받을 수 있다.  
	* 1=1은 항상 참이므로 공격자는 이 방법으로 로그인할 수 있다.
```sql
SELECT * FROM users WHERE username='admin' and password='password' OR 1=1 --'
```  
* 데이터 노출 (Data Disclosure)
	* 타겟 시스템의 데이터 탈취를 목적으로 한다. DB에서 발생하는 오류 메시지로 DB 구조를 유추한다. 
* 원격명령 실행 (Remote Command Execute)

    
### 방어
* 특수문자 여부 검사와 화이트리스트 체크
* 서버 오류 발생 시 에러 메시지 숨기기
* Prepared Statement 사용
	* 사용자 입력이 쿼리문으로부터 분리되어 SQL 인젝션을 방어할 수 있다. 쿼리 자체에 조건이 들어가는 Dynamic SQL이 사용된다.
	* 사용자 입력 값은 플레이스홀더로 표시되고, DBMS가 쿼리문을 분석한 다음 최적화한다. 플레이스홀더에 입력할 사용자 입력 값이 전송되고, DBMS가 쿼리문을 실행하는 방식이다.
* 이스케이프
	* SQL에서 특별한 의미를 갖는 문자들을 이스케이프해서 SQL 삽입을 방어한다. 
* hash function (암호화) 사용
	* 사용자 입력값을 해시함수로 해싱한 후 저장하면 데이터베이스가 누출되더라도 평문이 들어있지 않기 때문에 그나마 낫다.

--- 
* [<SQL>SQL 인젝션 방어하는 방법중 하나](https://rh-cp.tistory.com/70)
* [SQL 삽입 위키백과](https://ko.wikipedia.org/wiki/SQL_%EC%82%BD%EC%9E%85)