
# Adjacency_Matrix_List.md

작성자 : 김다인

  

---

### 그래프를 표현하는 방법, 인접 행렬과 인접 리스트

그래프는 노드와 엣지로 구성된 비선형 자료구조이다. 프로그래밍 언어로 그래프를 구현할 때는 인접 행렬을 사용하거나 인접 리스트를 사용할 수 있다.

![그래프를 인접 행렬과 인접 리스트로 나타낸 예시](https://algorithmtutor.com/images/graph_representation_directed.png)

* 인접 행렬 : Adjacency Matrix로 불리며, 그래프에 존재하는 노드의 개수가 V일 때 V*V 크기의 2차원 정방 배열이 만들어진다. 배열의 각 원소는 노드 간 연결 상태, 가중치 그래프일 경우 가중치를 나타낸다. 예를 들어 graph[1][2]의 값은 1번 노드에서 2번 노드로 가는 경로가 있는지를 나타내는 값이다.
  * 주로 간선 정보를 표현한다. n번 노드에서 m번 노드로의 경로가 있다면 graph[n][m]은 1이며, 없다면 0으로 나타내는 경우가 많다. 만약 무방향 그래프라면 graph[n][m]과 graph[m][n]은 항상 같다.
  * 구현이 쉽고, 노드 간 경로가 존재하는지 확인할 때는 항상 O(1) 시간복잡도로 확인이 가능하다. 또한, 그래프에 노드 간 경로가 많은 dense(빽빽)한 그래프 구현에 사용하면 이점이 있다. sparse(듬성듬성)한 그래프라면 인접 리스트가 더 좋은 선택지가 될 수도 있다.
  * 듬성듬성한 그래프 구현에 인접 행렬이 불리한 이유는, 전체 노드 개수를 V라고 할 때, 노드 n에 연결된 모든 노드들에 방문하려는 경우 O(V) 시간이 걸리기 때문이다.

* 인접 리스트 : Adjacency List로 불리며, 연결 리스트를 사용해 그래프를 구현한다. 노드 개수가 V일 때 V개만큼의 노드를 만들고 해당 노드와 연결되는 다른 노드를 포인터로 연결시키는 방식이다. 이 때 어떤 노드가 먼저 연결될 것인지는 상관없다.
  * 인접 행렬과 달리 실제로 어떤 노드로 통하는 경로가 있는 다른 노드들만 저장되기 때문에 메모리를 절약할 수 있다. 간선 개수를 E라고 할 때, 노드 n에 연결된 모든 노드들에 방문할 때는 O(E) 시간이 걸린다.
  * 하지만, 노드 n이 노드 m과 연결되어 있는지 확인해야 할 때는 노드 n에 연결된 모든 간선을 확인해야 한다는 단점이 있다. 인접 행렬의 장점이 인접 리스트의 단점인 셈이다.
  * 이 같은 특징들 때문에 sparse한 그래프의 경우 인접 리스트로 구현하는 것이 좋은 선택일 수 있다.