# Template Method

### **작성자 강수지** <br><br>

## Template Method
GoF 디자인 패턴에 의하면 Template Method 란 !

알고리즘의 구조를 메소드에 정의하고 하위클래스에서 알고리즘의 구조의 변경없이 알고리즘을 재정의하는 패턴이다 

알고리즘이 단계별로 나누어지거나 같은 역할을 하는 메소드지만 여러 곳에서 다른형태로 사용이 필요한 경우 유용한 패턴이다


즉 하위 클래스에서 사용되지만 변하지 않는 기능은 상위클래스에 저장해두고 확장할 기능을 서브 클래스에서 만들도록 설계한다는 뜻이다


**전체적인 레이아웃을 통일하지만 상속받은 클래스는 hook 메서드를 이용하여 확장할 수 있도록 유연성을 주는 디자인 패턴** 으로 이해하면된다

( *전체적으로는 동일하면서 부분적으로는 다른 구문으로 구성된 메서드의 코드 중복을 최소화 할 때 유용한 패턴* )

---

<img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FefZpxm%2FbtrDd1moNwQ%2F9Fq1ojGwpeySrt9g7W72vK%2Fimg.png">

## AbstractClass
템플릿 메서드를 정의하는 클래스

상위 클래스에 공통 알고리즘을 정의하고 하위 클래스에서 구현될 기능을 primitive 메서드 또는 hook 메서드로 정의하는 클래스

## ConcreteClass
물려 받은 primitive 메서드 또는 hook 메서드를 구현하는 클래스

상위 클래스에 구현된 템플릿 메서드의 일반적인 알고리즘에서 하위 클래스에 적합하게 primitive 메서드나 hook 메서드를 오버라이드하는 클래스




