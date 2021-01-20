# BFS (너비 우선 탐색)
재귀 + 포문*2 + 큐<br>
큐 기반 : 앞에 있는 것이 팝이 되면서 그 노드와 연결된 노드를 큐에 추가<br>
level이 중요할 때 : level 에 따라 값이 변할 때 주로 사용<br>
```c++
queue <int> q;

void bfs(int v) {
	q.push(v);
	visit[v] = 1;
	while (!q.empty()) {
		int f = q.front();
		q.pop();
		for (int i = 0; i < MAP[f].size(); i++) {
			if (visit[MAP[f][i]] == 1) continue;
			q.push(MAP[f][i]);
			visit[MAP[f][i]] = 1; 
			// visit[MAP[f][i]] = visit[f]+1 // level을 넣는 방법 -> “root”로 부터의 최단 거리가 저장됨.
		}
	}
}
```
bfs가 필요한 경우 중 level이 중요한 경우(트리의 깊이가 중요한 경우)<br>
예시) root로 부터의 거리가 중요한 경우<br>
해결 방법 : visit에 level을 넣어주기 (true,false값이 아닌 level값 넣기)<br>