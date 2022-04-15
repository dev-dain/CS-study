# Queue

### **작성자 강수지** <br><br>

큐는 선형 자료구조의 일종으로 먼저 들어온 원소가 먼저 나가는 **FIFO(First-In-First-Out)** 특징을 가진다

큐는 줄 서기 라고 생각하면 이해가 쉽다 ^ㅁ^

파이썬에서는 기본 클래스 list 와 내장모듈 Queue를 통해 구현할 수 있다

하지만 리스트를 사용할 경우 추가의 복잡도는 O(1) 이며 삭제는 O(N) 이기 때문에

데이터 처리속도가 O(1)인 내장 모듈로 구현하는 것이 좋다

---

### Queue 구현

- queue 초기화 ( Queue 모듈 사용 예시 )
```python
# 빈 큐 초기화
import queue

q = queue.Queue()
```
- queue 원소 삽입 enqueue
```python
# append 메소드를 이용해 리스트의 가장 마지막에 4라는 원소 추가
q.put(4)
```
- queue 원소 제거 dequeue
```python
# pop 메소드를 이용하여 가장 앞 원소 제거하고 리턴받을 수 있다
print(q.get())
```
---
# Deque ( 양방향 큐 )
덱은 앞과 뒤에서 모두 삽입과 삭제가 가능한 양방향 자료구조이고 스택과 큐가 합쳐진 자료구조이다 !
 

덱은 시간 복잡도가 O(1) 매우 빠른데 이는 내부적으로 doubly linked list 로 구현되어 있기 때문이다

아래 코드는 덱의 구현이다
```python
from collection import deque

d = deque([1,2,3])

# 삽입
d.appendleft(0)  # 앞에 삽입
d.append(4) # 뒤에 삽입

# 삭제
d.popleft() # 앞에 삭제
d.pop() # 뒤에 삭제

# rotate
d.rotate(-2) # 왼쪽으로 밀기
d.rotate(2) # 오른쪽으로 밀기

# 가장 앞에 있는 원소와 가장 뒤에 있는 원소 반환
print(d[0],d[-1])
```

---
### 큐의 활용
- 우선순위 같은 작업의 예약 ( 프린트 출력 )
- 대기열 ( 주문 대기열 )
- 너비우선탐색 ( BFS ) 구현
- 프로세스 관리