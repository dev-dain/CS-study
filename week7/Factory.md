# Factory

### **작성자 강수지** <br><br>

## Factory Method
 

팩토리 메서드 패턴은 객체지향 디자인 패턴이다. 

상위 클래스에 알려지지 않은 구현체 클래스를 생성하는 패턴이며 하위클래스가 어떤 객체를 생성할지를 결정하도록 하는 패턴이기도 하다.

다양한 구현체 ( product ) 가 있고 그 중 특정한 구현체를 만들 수 있는 다양한 팩토리를 제공하는 패턴이다

---

## Factory Method Pattern & Abstract Factory Pattern
 

팩토리 패턴에는 팩토리 메서드 패턴과 추상 팩토리 패턴이 있다

공통점은 **객체의 생성부를 캡슐화하여 결합을 느슨하게 한다는 점**과 **구체적인 타입에 의존하지 않도록 한다는 점**이다


차이는 **팩토리 매서드 패턴은 상속을 통해 서브 클래스에서 팩토리 매서드를 오버라이딩하여 구현**한다

**추상 팩토리 패턴은 객체의 집합을 생성하기 위한 정의를 추상체에 위치시키고 하위의 구현체에서 세부적인 집합 생성 과정을 구현**한다

---

팩토리 매서드는 기존의 인스턴트를 만드는 과정을 수정하지 않고 새로운 인스턴스를 다른 방법으로 생성하도록 확장이 가능하다 ( 객체 지향 원칙 )

하지만 클래스가 많아지면 클래스의 계층이 커지고 제품 클래스가 바뀔때마다 새로운 서브 클래스를 생성해야한다는 단점이 있다

