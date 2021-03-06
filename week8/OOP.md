# 객체 지향 프로그래밍 (OOP, Object Oriented Programming)
작성자: 장수현

현실세계의 사물을 객체로 보고 각자의 역할을 지닌 객체들끼리 서로 메시지를 주고받으며 동작할 수 있도록 프로그래밍 하는 것

- 장점
    - 객체를 중심으로 프로그래밍하기 때문에, 사람의 관점에서 프로그램을 이해하고 파악하기 쉽다.
    - 강한 응집력과 약한 결합력을 가진다.
    - 재사용성, 확장성, 융통성이 높다.
- 단점
    - 객체 간의 정보 교환이 모두 메시지 교환을 통해 일어나므로 실행 시스템에 많은 오버헤드가 발생한다.
    - 객체가 상태를 갖기 때문에 예상치 못한 부작용이 발생할 수 있다. 변수가 존재하고 이 변수를 통해 객체가 예측할 수 없는 상태를 갖게 되어 애플리케이션 내부에서 버그를 발생시킬 수 있다.

<br>

## 객체 지향의 특징
**1. 추상화 (Abstraction)**
- 필요로 하는 속성이나 행동을 추출하는 작업
- 추상적인 개념에 의존하여 설계해야 유연함을 갖출 수 있다
- 즉, 세부적인 사물들의 공통적인 특징을 파악한 후 하나의 집합으로 만들어내는 것

**2. 캡슐화 (Encapsulation)**
- 낮은 결합도를 유지할 수 있도록 설계하는 것
- 한 곳에서 변화가 일어나도 다른 곳에 미치는 영향을 최소화 시킨다
- 즉, 객체가 내부적으로 기능을 어떻게 구현하는지 감추는 것

**3. 상속 (Inheritance)**
- 여러 개체들이 지닌 공통된 특성을 부각시켜 하나의 개념이나 법칙으로 성립하는 과정
- 자식 클래스를 외부로부터 은닉하는 캡슐화의 일종이라고 말할 수 있다

**4. 다형성 (Polymorphism)**
- 서로 다른 클래스의 객체가 같은 메시지를 받았을 때 각자의 방식으로 동작하는 능력
- 즉, 부모 클래스의 메소드를 자식 클래스가 오버라이딩해서 자신의 역할에 맞게 활용하는 것