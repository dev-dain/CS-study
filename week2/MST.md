# 최소 신장 트리 (MST, Minimum Spanning Tree)

## Spanning Tree 란?
```
그래프 내의 모든 정점을 포함하는 트리, 그래프의 최소 연결 부분 그래프
```

<br>

<img src="https://gmlwjd9405.github.io/images/algorithm-mst/spanning-tree.png">

<br>

최소 연결 = 간선의 수가 가장 적다. n개의 정점을 가지는 그래프의 최소 간선의 수는 (n-1)개이고, (n-1)개의 간선으로 연결되어 있으면 필연적으로 트리 형태가 된다. 이것이 바로 Spanning Tree가 된다.

즉, 그래프에서 일부 간선을 선택해서 만든 트리

<br>

## MST 란?
```
Spanning Tree 중에서 사용된 간선들의 가중치 합이 최소인 트리
```

<br>

<img src="https://velog.velcdn.com/images%2Ffldfls%2Fpost%2Fe1e29196-3896-41c2-89ce-7856697443d6%2Fimage.png">

<br>

각 간선의 가중치가 동일하지 않을 때 단순히 가장 적은 간선을 사용한다고 해서 최소 비용이 얻어지는 것은 아니다. MST는 간선에 가중치를 고려하여 최소 비용의 Spanning Tree를 선택하는 것을 말한다.

즉, 그래프에 있는 모든 정점들을 가장 적은 수의 간선과 비용으로 연결하는 것이다.

<br>

[ 특징 ]

간선의 가중치의 합이 최소여야 한다.

n개의 정점을 가지는 그래프에 대해 반드시 (n-1)개의 간선만을 사용해야 한다.

사이클이 포함되어서는 안된다.