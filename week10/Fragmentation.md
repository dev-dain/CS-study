# 단편화 (Fragmentation)
작성자: 장수현

<br>

프로세스들이 메모리에 적재되고 제거되는 일이 반복되다보면, 프로세스들이 차지하는 메모리 틈 사이에 사용 하지 못할 만큼의 작은 자유공간들이 늘어나게 되는데, 이것이 단편화이다.

## 외부 단편화

<br>

<img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FA2ebn%2Fbtrnv29ql8l%2FbUHpFVuDT0hLGJTgLWeDqk%2Fimg.png">

<br>

외부단편화는 메모리 공간 중 사용하지 못하게 되는 일부분이다. 메모리에서 남는 공간들을 모두 합치면 충분한 공간이 되는 부분들이 분산되어 있을때 발생한다.

위와 같이 남아있는 메모리 공간은 50MB + 50MB = 100MB 로 요청한 메모리 공간 80MB보다 크지만, 남아있는 공간이 연속적이지 않아 Process C를 할당할 수가 없게 된다. 따라서 남아있는 메모리 공간이 낭비되게 되는 문제가 발생한다.

<br>

**해결 방법 - 압축**

<br>

<img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2F02zPc%2FbtrnypW32GS%2F6cZQCyTGFKlNtkll6UMCKk%2Fimg.png">

<br>

압축 기법은 메모리 내 분산되어 있는 단편화된 공간들을 통합하여 하나의 커다란 빈 공간을 만드는 작업을 의미한다.

위와 같이 흩어져 있던 공간을 연속된 공간, 즉 하나의 공간으로 만들면 기존에 할당할 수 없던 프로세스를 할당할 수 있게 된다.

<br>

## 내부 단편화

<br>

<img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FxDLav%2Fbtrnv3mVrDl%2FnjIwszyMkwGjfC3MDCHNRk%2Fimg.png">

<br>

내부 단편화란 메모리 공간 내 프로그램의 사용 공간을 할당 후 사용되지 않고 남게 되는 현상을 말한다. 

위와 같이 100MB의 메모리에 80MB 크기의 프로세스를 올리게 되면, 20MB의 내부 단편화가 발생하게 된다. 즉, 작은 크기의 잔여 메모리가 발생해 해당 메모리를 사용할 수 없게 된다.