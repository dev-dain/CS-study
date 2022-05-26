# Singleton
작성자 : 김다인

---
### 싱글턴 패턴
*생성* 패턴의 일부인 싱글턴 패턴(Singleton pattern)을 따르는 클래스는 생성자가 여러 번 호출되더라도 실제로 생성되는 객체는 하나이며, 최초 생성 이후에 호출된 생성자는 최초 생성자가 생성한 객체를 반환한다. 즉, **객체는 한 번만 만들며** 생성자를 여러 번 호출하더라도 처음 만들어둔 것을 돌려준다. 이렇게 생성된 객체는 어디서든 참조 가능하다.  
싱글턴 패턴은 주로 공통된 객체를 여러 개 생성해 사용하는 DBCP(Database Connection Pool) 등의 상황에서 많이 사용된다.  
메모리 낭비를 방지할 수 있다는 장점이 있으나, 싱글턴 객체의 역할이 복잡하다면 다른 객체 간 결합도가 높아져 개방-폐쇄 원칙에 어긋나게 된다.  

### Singleton in Java
```java
public class Singleton {
	// 인스턴스를 미리 만들어둠
    private static final Singleton INSTANCE = new Singleton();
    
    // 생성자가 private인 것에 주목
    private Singleton() {}	
    public static Singleton getInstance() {
        return INSTANCE;
    }
}
```

### Singleton in Python
```python
class Singleton:
    __instance = None

    def __new__(cls, *args):
        if cls.__instance is None:
            cls.__instance = object.__new__(cls, *args)
        return cls.__instance
```

---
* [위키백과](https://ko.wikipedia.org/wiki/%EC%8B%B1%EA%B8%80%ED%84%B4_%ED%8C%A8%ED%84%B4)
* [Java에서 싱글톤(Singleton) 패턴을 사용하는 이유와 주의할 점](https://elfinlas.github.io/2019/09/23/java-singleton/)