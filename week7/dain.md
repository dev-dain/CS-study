
# Design Pattern & Adapter & Singleton

### **작성자 김다인** <br><br>

✔ 디자인 패턴의 3가지 분류를 말씀해주시고, 분류별로 한 가지 사례를 설명해주세요.

---

✔ 어댑터 패턴의 2가지 방식과 각 방식의 한계를 설명해주세요.

---

✔ 다음은 싱글턴 패턴을 간단히 구현한 자바 코드입니다.
```java
public  class  Singleton {
	// 인스턴스를 미리 만들어둠
	private  static  final  Singleton  INSTANCE = new  Singleton();

	// 생성자가 private인 것에 주목
	private  Singleton() {}
	public  static  Singleton  getInstance() {
		return INSTANCE;
	}
}
```
여기서, (1) 인스턴스가 private인 이유와 (2) 생성자가 private인 이유를 설명해주세요.