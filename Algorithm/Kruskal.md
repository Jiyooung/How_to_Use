# Kruskal 알고리즘
최소 스패닝 트리 (Minimum Spanning Tree, MST)<br>
Greedy 알고리즘을 이용하여 네트워크(가중치를 간선에 할당한 그래프)의 모든 정점을 최소비용으로 연결하는 최적 해답을 구하는 것<br>

## Kruskal 알고리즘의 동작
1. 그래프의 간선들을 가중치의 오름차순으로 정렬한다.
2. 정렬된 간선 리스트에서 순서대로 사이클을 형성하지 않는 간선을 선택한다.
- 즉, 가장 낮은 가중치를 먼저 선택한다.
- 사이클을 형성하는 간선을 제외한다.
3. 해당 간선을 현재의 MST(최소 비용 신장 트리)의 집합에 추가한다

## UnoinFind 활용 코드

```python
# n : 노드 개수
# cost : [start, end, cost]
import collections
answer = 0
costs.sort(key=lambda x: x[2])  # 비용 오름차순으로 정렬
parent = collections.defaultdict(list)
for i in range(n):
    parent[i] = i

# 최상위 부모 찾기
def find(index):
    if parent[index] != index:
        parent[index] = find(parent[index])
    return parent[index]

# 크기 비교해서 큰 집합에 작은 집합을 추가해야 더 효율적
# 단순히 부모의 숫자가 더 작은 곳에 추가함
def union(x, y):
    if parent[x] > parent[y]: parent[x] = y
    else: parent[y] = x

for c in costs:
    x, y = c[0], c[1]
    x_p, y_p = find(x), find(y)   # 정점의 부모 찾기

    if  x_p != y_p :        # 부모가 같지 않으면
        union(x_p, y_p)     # 집합 합치기
        answer += c[2]

print(answer)
```