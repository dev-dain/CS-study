# Strategy
작성자: 장수현

```
어떤 동작을 하는 로직을 정의하고, 이것들을 하나로 묶어(캡슐화) 관리하는 패턴
```

행위를 클래스로 캡슐화해 동적으로 행위를 자유롭게 바꿀 수 있게 해주는 패턴이다. 
같은 문제를 해결하는 여러 알고리즘이 클래스별로 캡슐화되어 있고 이들이 필요할 때 교체할 수 있도록 함으로써 동일한 문제를 다른 알고리즘으로 해결할 수 있게 한다.

<br>

<img src="https://gmlwjd9405.github.io/images/design-pattern-strategy/strategy-pattern.png">

<br>

**Strategy**
- 인터페이스나 추상 클래스로 외부에서 동일한 방식으로 알고리즘을 호출하는 방법을 명시

**ConcreteStrategy**
- Strategy 패턴에서 명시한 알고리즘을 실제로 구현한 클래스

**Context**
- Strategy 패턴을 이용하는 역할을 수행
- 필요에 따라 동적으로 구체적인 전략을 바꿀 수 있도록 setter 메서드(‘집약 관계’)를 제공한다.

<br><br>

## 예시 - 로봇 만들기

<br>

<img src="https://gmlwjd9405.github.io/images/design-pattern-strategy/strategy-solution.png">

<br>

상황: 로봇의 종류는 TaekwonV, Atom, Sungard 이고 동작은 이동과 공격이다

Strategy: Robot 클래스

ConcreteStrategy: TaekwonV 클래스, Atom 클래스, Sungard 클래스

Context: MovingStrategy 인터페이스, AttackStrategy 인터페이스

<br>

- Robot 클래스가 이동 기능과 공격 기능을 이용하는 클라이언트 역할을 수행
- 구체적인 이동, 공격 방식이 MovingStrategy와 AttackStrategy 인터페이스에 의해 캡슐화되어 있다
- 새로운 기능의 추가(새로운 이동, 공격 기능)가 기존의 코드에 영향을 미치지 못하게 하므로 OCP를 만족 하는 설계가 된다