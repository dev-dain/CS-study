# Composite
작성자: 장수현

```
여러 개의 객체들로 구성된 복합 객체와 단일 객체를 클라이언트에서 구별 없이 다루게 해주는 패턴
```

전체-부분의 관계를 갖는 객체들 사이의 관계를 정의할 때 유용하다. 또한, 클라이언트는 전체와 부분을 구분하지 않고 동일한 인터페이스를 사용할 수 있다.

<br>

<img src="https://gmlwjd9405.github.io/images/design-pattern-composite/composite-pattern.png">

<br>

**[역할이 수행하는 작업]**

**Component**
- 구체적인 부분의 일반화
- Leaf 클래스와 전체에 해당하는 Composite 클래스에 공통 인터페이스를 정의

**Leaf**
- 구체적인 부분 클래스
- Composite 객체의 부품으로 설정

**Composite**
- 전체 클래스
- 복수 개의 Component를 갖도록 정의
- 복수 개의 Leaf, 심지어 복수 개의 Composite 객체를 부분으로 가질 수 있음

<br><br>

## 예시 - 컴퓨터 장치 지원하기 

<br>

<img src="https://gmlwjd9405.github.io/images/design-pattern-composite/composite-solution1.png">

<br>

상황: 컴퓨터가 키보드, 본체, 모니터, 스피커 장치를 지원하고 있다

Component: ComputerDevice 클래스

Leaf: Keyboard 클래스, Body 클래스, Monitor 클래스, Speaker 클래스

Composite: Computer 클래스

<br>

- 구체적인 부품들을 일반화한 ComputerDevice 클래스를 정의
- 구체적인 부품 클래스들(Keyboard, Body 등)은 ComputerDevice의 하위 클래스로 정의
- Computer 클래스도 ComputerDevice 클래스의 하위 클래스로 정의 (Computer 클래스도 ComputerDevice 클래스의 일종)
- ComputerDevice 클래스를 이용하면 Client 프로그램은 Keyboard, Body 등과 마찬가지로 Computer를 상용할 수 있다