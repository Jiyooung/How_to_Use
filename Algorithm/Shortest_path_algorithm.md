# 최단 경로 알고리즘 (Shortest path algorithm)

## 다익스트라(Dijkstra)
하나의 정점에서 출발. 다른 모든 정점까지의 최단 경로 구하는 알고리즘<br>
가장 적은 비용을 하나씩 선택<br>
음의 가중치를 가진 간선 불가능<br>

### 동작
1. 출발 노드 선정
2. 출발 노드와 연결된 노드의 최소 비용 저장
3. 방문하지 않은 노드 중 가장 적은 비용의 노드 선택

우선순위큐 활용 시 O(NlogN)
<br>

## 플로이드 와샬 알고리즘(Floyd-Warshall)
모든 정점에서 모든 정점으로의 최단 경로<br>
음의 가중치를 가진 간선 가능<br>
모든 정점에 대한 경로를 계산하므로 거리를 저장할 2차원 배열 구조 필요<br>

### 2개의 테이블
1. 모든 경로에 대한 가중치를 저장하는 테이블(n*n)<br>
2. 각 정점까지 가기 직전의 정점을 저장한 테이블(n*n)<br>

```python
    INF = float('inf')
    node = [[INF] * n for _ in range(n)]
    for i in range(n):  # 대각선
        node[i][i] = 0

    # node에 그래프 정보 추가 필요

    for k in range(n):  # 중간 노드
        for i in range(n):
            for j in range(n):
                if node[i][j] > node[i][k] + node[k][j]:
                    node[i][j] = node[i][k] + node[k][j]
```
<br>

## 벨만포드 알고리즘(Bellman-Ford)
하나의 정점에서 출발. 다른 모든 정점까지의 최단 경로 구하는 알고리즘<br>
가장 적은 비용을 하나씩 선택<br>
음의 가중치를 가진 간선 가능<br>


### 음수 싸이클 혹은 음의 싸이클(negative cycle)
가중친 합이 0보다 작은 싸이클 발생 가능

### 동작
1. 출발 노드 선정
2. 출발 노드와 연결된 노드의 최소 비용 저장
3. 2번 과정을 V - 1번 반복
4. 이후에도 거리가 갱신되는 경우가 있다면 음수 사이클 존재


```python 

```







