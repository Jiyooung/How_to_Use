# 그래프
- 완전 그래프<br>
모든 노드가 서로 연결<br>
- 이분 그래프<br>
자신의 그룹에서는 서로 연결 되어서는 안 됨 <br>
예시) 홀수 짝수는 연결되어 있지만, 홀수끼리 혹은 짝수끼리는 연결되어 있지 않음.<br>
- 트리 : 사이클이 없는 형태<br>

### 그래프 탐색 방법 (엣지만 연결되어 있다면 어떤 그래프 든 탐색 가능)
1. [DFS](./DFS.md)
2. [BFS](./BFS.md)
3. [BestFS(first search)](./BestFS.md)

## 좌표 탐색 (중요)
그래프 탐색에서 대부분 사용<br>
```c++
dy = {-1, 1, 0, 0}; // 상하좌우
dx = {0, 0, -1, 1};
for (int i = 0; i < 4; i++) {
	int xx = x + dx[i];
	int yy = y + dy[i];

	if (xx, yy 가 올바른 범위 안에 있는지 확인) {
		dfs(xx, yy);
	}
}
```