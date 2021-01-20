# DFS (깊이 우선 탐색)
그저 재귀 + 포문<br>
스택기반<br>
완전 탐색에서 많이 사용 -> 이유 : 코드의 간편함<br>
v : 정점 번호<br>
```c++
vector <int> MAP[]

void dfs(int v) {
	if (visit[v] == 1) { return ;}	// 이미 방문한 정점이다.
	visit[v] = 1;					// 이제 방문한다.
	for (int i = 0; i < MAP[v].size(); i++) {
		dfs(MAP[v][i]);
	}
}

int main(void) {
	dfs(1);
}
```