# Heap & 우선순위 큐

### **작성자 강수지** <br><br>

힙는 비선형 자료구조의 일종으로 최소값과 최대값을 빠르게 찾기 위한 **이진트리 구조**이다

우선순위 큐는 들어간 순서에 상관없이 우선순위가 높은 데이터가 먼저 나온다

힙은 heapq 내장 모듈로 구현할 수 있고 우선순위 큐는 힙으로 구현이 가능하다 !
<br><br>
최소 힙은 각 노드의 키 값이 그 자식노드의 키 값보다 크지 않은 힙을 의미하고

최대 힙은 각 노드의 키 값이 그 자식노드의 키 값보다 작지 않은 힙을 의미한다

힙은 완전이진트리의 성질을 갖고 1차원 배열로 표현이 가능하다

아래를 참고하면 root index 에 따라 chlid index 를 계산할 수 있다
```
root index = 0

left index = index * 2 + 1
right index = index * 2 + 2
```
힙의 복잡도는 O(log n) 이다

데이터 삽입은 트리의 leaf node( 자식이 없는 ) 부터 시작하고

데이터 삭제는 우선순위가 가장 큰 것은 root node 를 삭제한다

---

### Heap 구현

- heap 초기화 & 삽입 ( heapq 내장 모듈을 최소힙이 기본 )
```python
import heapq

heap = []
heapq.headppush(heap, 1) # 노드 추가

heapq.heapify(heap) # 기존의 리스트를 힙으로 변환할 때 시간복잡도는 O(n)
```
- heap 노드 삭제
```python
# heappop 메소드 이용하여 가장 작은 원소를 꺼내 리턴한 후 그다음 작은 원소가 루트노드가 된다
return heap.heappop(heap)

# 최소값을 꺼내지 않고 리턴만 하려면 인덱스로 접근
print(heap[0])
```
- 최대 힙 만들기
```python
# 우선순위가 포함된 튜플 이욯 !
import heapq

nums = [4,1,7,3,8,5]
heap = []

for num in nums:
	heapq.heappush(heap, (-num, num)) # 우선순위, 값
```
