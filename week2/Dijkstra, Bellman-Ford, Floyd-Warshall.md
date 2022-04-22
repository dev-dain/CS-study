# 다익스트라(Dijkstra)
```
가중치가 음이 아닌 그래프에서 한 정점에서부터 다른 모든 정점으로의 최단경로를 구하는 알고리즘
```
우선순위 큐 사용, 시간 복잡도는 O(ElogV)

<br>

<img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FvYBE1%2FbtqVvOEim4p%2FewKblH9yeOcRL2AbS6K7UK%2Fimg.jpg">

<br>

[ 과정 ]
1. 시작 노드는 0, 나머지 노드들은 무한으로 경로 초기화
2. 시작 노드를 우선순위 큐에 담는다
3. 우선순위 큐에서 pop한 후 해당 노드와 이어진 노드를 확인한다
4. 그 경로의 거리가 기존 경로의 거리보다 작은 경우, 경로를 갱신하고 우선순위 큐에 넣는다
6. 우선순위 큐가 빌 때까지 3-4번을 반복한다.

<br>

# 벨만포드(Bellman-Ford)
```
가중치가 음수이고 음수 사이클이 없는 그래프에서 한 정점에서부터 다른 모든 정점으로의 최단경로를 구하는 알고리즘
```
시간 복잡도는 O(VE)

<br>

<img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FbshYHY%2FbtqVsxDhqWi%2F40JLHdxOIBObZHD0MMrjK0%2Fimg.png">

<br>

[ 과정 ]
1. 시작 노드는 0, 나머지 노드들은 무한으로 경로 초기화
2. 그래프 내에 모든 간선에 대해 3번을 시행한다
3. 각 정점마다 모든 인접 정점을 탐색한다. 기존 인접 정점까지의 거리가 기존 현재 정점까지 거리 + 현재 정점부터 인접 정점까지 거리인 경우 경로와 거리를 갱신한다.
4. 이를 경로와 거리의 갱신이 일어나지 않을 때까지 반복해준다. 만약, 정점의 수만큼의 시행 이후에도 경로와 거리의 갱신이 일어날 경우, 음수 사이클이 존재한다고 판단한다.

<br>

# 플로이드워셜(Floyd-Warshall)
```
모든 정점에서 모든 정점으로 가는 최단경로를 구하는 알고리즘
```
2차원 배열 사용, 시간 복잡도는 O(V^3)

<br>

<img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FchI5Ge%2FbtqVyVXp1gV%2FP9aCujknpey3CtnitFlULK%2Fimg.jpg">

<br>

[ 과정 ]
1. 인접행렬을 저장할 2차원 배열을 만들고 무한대로 초기화
2. 간선 정보를 저장하고 제자리는 0으로 초기화
3. 경유지를 기준으로, 해당 경유지를 거쳐가는게 빠르다면 갱신
4. 모든 정점을 경유지로 선정해 3번 반복