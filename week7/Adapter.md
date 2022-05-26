# Adapter
작성자 : 김다인

---
### 어댑터 패턴
*구조* 패턴의 일부인 어댑터 패턴(Adapter pattern)은 적응자, Wrapper 패턴이라고도 불린다.  
**클래스 인터페이스를 사용자가 기대하는 다른 인터페이스로 변환**하는 패턴으로, 호환성 없는 인터페이스 때문에 함께 동작할 수 없는 클래스들이 함께 동작할 수 있도록 한다.  
쉽게 말하자면 사용자가 쓰려는 어떤 인터페이스나 메소드 등이 다른 이름으로 제공되고 있어 어댑터를 만들어 간접적으로 끌어다쓰는 것이라고 이해할 수 있다.  
예를 들어, 110V 충전기를 갖고 있고 '전기'를 써야 하지만 충전기 단자는 220V일 때, 돼지코(어댑터)를 사용하면 '전기'를 사용할 수 있게 된다.  

### Object Adapter in Python
사용자는 request라는 메소드를 사용해야 하는데 정작 사용해야 하는 Target(Adaptee라고도 한다)은 specific_request라는 메소드만 제공할 때, 어댑터 패턴을 사용해 다음과 같이 해결할 수 있다.  
Object Adapter의 경우 Adaptee 객체를 만들어줘야 사용 가능하다.
```python
class Target(object):
    def specific_request(self):
        return 'Hello Adapter Pattern!'

class Adapter(object):
    def __init__(self, adaptee):
        self.adaptee = adaptee

    def request(self):
        return self.adaptee.specific_request()

client = Adapter(Target())
print(client.request())
```

### Class Adapter in Java
다음은 내부적으로 DList의 메소드를 사용하지만 겉으로는 Stack 인터페이스의 메소드를 사용하는 코드이다. 이 때 Target(Adaptee라고도 한다) 클래스는 DList이다.  
Class Adapter의 경우 상속을 이용하기 때문에 다중 상속이 지원되는 언어에서만 사용 가능하다.  
```java
/* the client class should instantiate adapter objects */
/* by using a reference of this type */
interface Stack<T>
{
  void push (T o);
  T pop ();
  T top ();
}

/* DoubleLinkedList is the adaptee class */
class DList<T>
{
  public void insert (DNode pos, T o) { ... }
  public void remove (DNode pos) { ... }

  public void insertHead (T o) { ... }
  public void insertTail (T o) { ... }

  public T removeHead () { ... }
  public T removeTail () { ... }

  public T getHead () { ... }
  public T getTail () { ... }
}

/* Adapt DList class to Stack interface is the adapter class */
class DListImpStack<T> extends DList<T> implements Stack<T>
{
  public void push (T o) {
    insertTail (o);
  }

  public T pop () {
    return removeTail ();
  }

  public T top () {
    return getTail ();
  }
}
```

---
* [위키백과](https://ko.wikipedia.org/wiki/%EC%96%B4%EB%8C%91%ED%84%B0_%ED%8C%A8%ED%84%B4)
* [어댑터 패턴 (Adapter Pattern)](https://johngrib.github.io/wiki/pattern/adapter/) -> 정말 좋은 글입니다. 