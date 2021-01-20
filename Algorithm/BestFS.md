# BestFS (최선 우선 탐색)
어떤 값이 최선인지(최선은 내가 결정)를 따라서 탐색<br>
힙 기반(우선순위 큐)<br>
dfs와 모양은 모두 같으나 queue대신 priority_queue를 사용<br>
priority_queue를 만들 때 뒤에 넣는 ‘비교 함수’를 잘 구현해야 한다.<br>
```c++
priority_queue <int> pq;

void bfs(int v) {
	pq.push(v);
	visit[v] = 1;
	while (!q.empty()) {
		int f = pq.top();
		pq.pop();
		for (int i = 0; i < MAP[f].size(); i++) {
			if (visit[MAP[f][i]] == 1) continue;
			pq.push(MAP[f][i]);
			visit[MAP[f][i]] = 1; 
			// visit[MAP[f][i]] = visit[f]+1 // level을 넣는 방법
		}
	}
}
```