# Design Pattern
작성자 : 김다인

---
### 디자인 패턴
디자인 패턴(design pattern)은 소프트웨어 공학의 소프트웨어 디자인에서 **특정 문맥에서 공통적으로 발생하는 문제에 대해 재사용 가능한 해결책**이다. 상황에 맞게 사용될 수 있는 문제들을 해결하는 데에 쓰이는 서술, 템플릿을 말한다.  
GoF(Gang of Four : Erich Gamma, Richard Helm, Ralph Johnson, John Vissides)가 쓴 책이 1994년 출판된 이후 인기를 끌게 되었다. GoF는 23가지의 디자인 패턴을 정리하고 각각의 패턴을 **생성, 구조, 행위** 3가지로 분류했다.  

### 디자인 패턴의 분류
1. 생성
	* 객체 생성에 관련된 패턴으로, 객체 생성과 조합을 캡슐화해 특정 객체가 생성되거나 변경되어도 프로그램 구조에 영향을 크게 받지 않도록 유연성 제공
	* 종류
		* Abstract Factory(추상 팩토리)
		* Builder(빌더)
		* Factory Methods(팩토리 메서드)
		* Prototype(프로토타입)
		* Singleton(싱글턴)
2. 구조
	* 클래스, 객체를 조합해 더 큰 구조를 만드는 패턴으로, 객체들을 서로 묶어 새로운 기능을 제공하는 등의 쓰임
	* 종류
		* Adapter(어댑터)
		* Bridge(브리지)
		* Composite(컴포지트)
		* Decorator(데코레이터)
		* Facade(퍼사드)
		* Flyweight(플라이웨이트)
		* Proxy(프록시)
3. 행위
	* 객체, 클래스 간 알고리즘이나 책임 분배에 관련된 패턴으로, 한 객체가 혼자 수행할 수 없는 작업을 여러 객체로 분배하면서 동시에 객체 간 결합도를 최소화하는 데에 쓰임
	* 종류
		* Chain of Responsibility(책임 연쇄)
		* Command(커맨드)
		* Interpreter(인터프리터)
		* Iterator(반복자)
		* Mediator(중재자)
		* Memento(메멘토)
		* Observer(옵서버, 발행-구독 모델)
		* State(상태)
		* Strategy(전략)
		* Template Method(템플릿 메소드)
		* Visitor(비지터)

---
* [위키백과](https://ko.wikipedia.org/wiki/%EC%86%8C%ED%94%84%ED%8A%B8%EC%9B%A8%EC%96%B4_%EB%94%94%EC%9E%90%EC%9D%B8_%ED%8C%A8%ED%84%B4)
* [tech-interview](https://github.com/WeareSoft/tech-interview/blob/master/contents/designpattern.md)