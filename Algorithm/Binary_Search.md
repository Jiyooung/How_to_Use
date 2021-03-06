# 이분법
시초 : 이분 검색(binary search)<br>
시간복잡도 : log(n) 정렬되어 있다는 가정. (안되어있으면 nlogn)
배열안에서 값은 탐색<br>

## parametric search
이분 검색의 응용(중요)<br>
어떤 수들 안에서 정답을 찾는 것.<br>
예시)<br>
어떤 문제에서 최대값을 찾는 다고 가정<br>
4만이 답으로 가능하다면 0부터 4만까지는 전부다 답으로 가능<br>
어떤 수들이 문제의 규칙에는 맞는데 최대값일지는 모르는 것. <br>
최대값을 이 문제의 규칙에 맞는 여러 수 중 찾아내야 한다.<br>
<br>
예시 문제) 백준 2805번 나무 자르기<br>
15~0까지 모두 답의 조건에는 만족하지만, 가장 많은 나무길이를 남기는 것은 15!<br>
숫자를 모두 이분법으로 검색을 한다.<br>
예시로 설명!<br>
10부터 검색을 해봤는데, 10이 만족-> 그렇다면 10보다 크게 남길수 있음<br>
15를 선택 -> 18을 선택 -> 불가능… ->... 15가 답.<br>
시간복잡도 nlog(n)<br>

```c++
// 최대값을 찾는 함수로 구현. 작은 것은 가능하다는 뜻.
int parametric_iter(int MIN, int MAX) {
	int ret = 0;
	int l = MIN, r = MAX;

	while (l < r) {
		int mid = (l + r + 1) / 2;
		int c = check(mid)

		if ( c ){
			l = mid;	// 정답이 되는 것은 계속 포함해서 해야 함
			ret = mid;
		} else {
			r = mid - 1;
		}
	}
	return ret;
}
	
// 최소값을 찾는 함수로 구현. 큰 것은 가능하다는 뜻.
int parametric_rec(int l, int r){
	int ret = 0;

	if (l == r)	return l;

	int mid = (l + r) / 2;
	int c = check(mid);

	if ( c ) {
		parametric_rec(mid + 1, r);
	} else {
		ret = parametric_rec(l, mid);
	}

	return ret;
}
```
주의 : 정답이 되는 것은 포함을 하여 돌려야 한다.<br>

### (l + r) vs (l + r + 1)
1,2,3,4 로 가정해보고 어떤 것으로 할 지 생각해보면 편함<br>


## python의 bisect 모듈 
python의 내장 라이브러리<br>
`from bisect import bisect_left`
이 라이브러리는 별도의 타입이나 클래스를 요구하지 않으면서 몇 가지 함수를 이용해서 기본 리스트에 대해서 이진 탐색을 수행하는 api들을 제공<br>

### bisect_left(arr, x, lo=0, hi=len(arr))
주어진 리스트 arr과 값 x 가 있을 때, x 가 위치해야 할 인덱스를 구하는 함수<br>
return : index<br>
- arr[index] 값이 x가 아닐 수도 있음 -> 동일 여부 필요<br>
- arr의 모든 원소가 x보다 작을 경우 return len(a)<br>
arr의 특정 범위 내에서만 탐색을 원할 때 lo, hi 사용<br>
_left : `all(val <= x for val in a[lo:i])`<br>
_right : `all(val > x for val in a[i:hi])`<br>

#### _left vs _right
주어진 값 x와 같은 값이 리스트 내에 있을 때, x의 위치가 동일한 값으로부터 왼쪽에 있을지 오른쪽에 있을지를 결정<br>
default : _right<br>

### insort_left(arr, x)
bisect()로 구해진 위치에 x 값을 삽입<br>
default : _right<br>
`a.insert(bisect.bisect_left(a, x, lo, hi), x)`<br>
