
# UnionFind.md

작성자 : 김다인

---

### Union-Find, 유니온 파인드
유니온 파인드란 단순히 번역하자면 '합집합 찾기'이다. Disjoint-set이라고도 불린다. 여러 노드가 존재할 때, 어떤 노드들을 합치고 부모(루트)를 찾아 서로소 집합을 찾는 알고리즘이다. 그래프 알고리즘이라고 되어 있지만 트리 구조를 활용한다.  
Find 연산(루트 노드 찾기)과 Union 연산(서로 다른 두 집합 합치기)으로 이뤄져 있다.
* Find 연산 : 부모 노드를 찾을 때까지 재귀적으로 호출하는 연산이다. 어떤 원소 x가 속한 집합의 부모를 찾는 연산이다.
* Union 연산 : 어떤 두 노드의 부모 노드를 찾고, 번호가 큰 노드가 번호가 작은 노드의 부모를 가리키도록 하는 연산이다. 즉 두 집합을 합치는 연산이다.

### 코드로 확인
```python
def find(x):
  if parent[x] != x:
    return find(parent[x])
  return parent[x]

def union(a, b):
  a = find(a)
  b = find(b)
  if a < b:
    parent[b] = a
  else:
    parent[a] = b

v, e = map(int, input().split()) 
parent = [0] * (v + 1) # 부모 테이블 초기화  

# 부모 테이블상에서, 부모를 자기 자신으로 초기화  
for i in range(1, v + 1): 
  parent[i] = i # Union 연산을 각각 수행  

for i in range(e): 
  a, b = map(int, input().split()) 
  union(a, b) 

# 각 원소가 속한 집합 출력하기 
print('각 원소가 속한 집합: ', end='')

for i in range(1, v + 1):
  print(find(i), end=' ') 
print()  

print('부모 테이블: ', end='') 
for i in range(1, v + 1): 
  print(parent[i], end=' ')
```

  

### 예제 문제

* [백준 1976 여행 가자](https://www.acmicpc.net/problem/1976)

---
[Python 유니온 파인드 알고리즘 (Union Find Algorithm)](https://0x15.tistory.com/34)  
[이코테 유니온 파인드](https://www.youtube.com/watch?v=AMByrd53PHM)