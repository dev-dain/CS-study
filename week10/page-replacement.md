# Page-replacement
### **작성자 강수지** <br><br>

## 페이지교체알고리즘

<img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FpWjtY%2FbtrFFsCzNQ6%2FrzxohoKg80uoAeQqAciZgK%2Fimg.png">


> 페이징 기법으로 메모리를 관리하는 운영체제에서 필요한 페이지가 주기억장치에 적재되지 않았을시 ( 페이지의 부재가 발생했을때 ) 어떤 페이지 프레임을 선택하여 교체할 것인지 결정하는 방법을 말한다

## 페이지 교체 알고리즘 종류

**시간기반알고리즘**

- FIFO ( First In First Out )

가장 먼저 들어온 가장 오래된 페이지를 교체하는 기법으로 각 페이지가 주기억장치에 들어올때마다 타임스탬프를 찍어 기억하는 방식이다

- LRU ( Least Recently Used )

최근에 가장 오랫동안 사용하지 않은 페이지를 교체하는 기법으로 각 페이지마다 카운터나 스택을 두어 현 시점에서 가장 오랫동안 사용하지 않은 ( 가장 오래전에 사용된 ) 페이지를 교체한다

- LFU ( Least Frequently Used )

사용빈도가 가장 적은 페이지를 교체하는 기법으로 호출된 횟수가 가장 적은 페이지를 교체하게된다 이 방법은 바로 불러온 페이지가 교체될 수 있다는 단점이 존재한다

---

**빈도기반알고리즘**
- NUR ( Not Used Recently ) 

LRU 와 비슷한 방식으로 최근에 사용하지 않은 페이지를 교체한다

LRU 의 단점인 시간 오버헤드를 적게하는 방법으로 최근 사용여부를 확인하기 위해서는 각 페이지마다 두개의 참조비트와 변형비트를 사용하게 된다

- MFU ( Most Frequently Used )

가장 많이 사용된 페이지가 앞으로는 사용되지 않을것이라 가정하고 교체하는 방식이다

---

**Random**
무작위로 페이지를 교체하는 방식으로 빈도나 시간 기반의 알고리즘은 아니다 !