# Python

# 변수

## 전역변수
```python
x = 10

def func():
    y = 5
    global z = 7
    global b    # 선언과 동시에 초기화하면 에러남
    b = [0 for _ in range(5)]

    print(x, y, z)  # 10, 5, 7

func()
print(x, y, z)      # 10, 에러, 7  > 에러
```

# 자료형

## int

### 반올림, 내림
```python
import numpy as np
np.around(a)    # 0.5 기준으로 올림/내림
np.round_(a, N) # N 소수점 자리까지 반올림 
np.rint(a)      # 가장 가까운 정수로 반올림

np.ceil(a)      # 올림
np.trucn(a)     # 버림

np.fix(a)       # 0 반향으로 가장 가까운 정수로 올림/내림
```

## INF
```python
max_val = float('inf')
min_val = float('-inf')
```
### 형변환
int("3")<br>
str(3)<br>

## string

### string > int
```python
s = "123"
n = int(s)
```

## list

### list 원소추가
```python
a.append(1)     # 원소 마지막에 1 추가
a.insert(2, 5)  # index 2의 위치에 값 5 추가, 뒤에 값들은 밀림
c = a + b       # list 합치기
a.extend([1,2,3])   # 기존 a의 뒤에 해당 리스트 추가하기

```
### list 원소삭제
```python
del a[1]    # list a의 index 1 삭제
a.remove(3) # list a에서 값 3을 찾아 가장 먼저 발견된 3을 제거
            # 3 값이 없으면 ValueError 발생
del a[a.index(3)] # remove(3)과 동일한 효과
```

### 특정 값이 있는지 체크하기
```python
if item in list:        # item이 list에 있으면 ~
if item not in list:    # item이 list에 없으면 ~
```

### 특정 값으로 초기화
```python
l = [0 for i in range(n)]   # n크기만큼 0으로 초기화한 리스트 생성
matrix = [[0 for col in range(c)] for row in range(r)]  # r * c 인 2차원 배열 생성
```

### list 정렬하기

#### <list>.sort()
```python
l.sort([reverse=<True|False>][, key=<function>])
``` 
**원본 리스트가 변경**됨, 반환값은 None
새로운 리스트를 생성하지 않기 때문에 **sorted()보다 빠름**

- 2차원 배열 정렬
```python
l.sort(key=lambda x:x[0])   # x[0] : 첫 번째 인자로 sort
                            # x[1]...등 다른 인자로 sort 가능
i.sort(key=lambda x: (x[0], -x[1])) # 첫 번째 인자값이 동일하면 두번째 값을 비교하여 내림차순으로 정렬, -붙이면 내림차순
```

#### sorted(<list>)
```python
sorted(iterable[, key=<function>][, reverse=<True|False>])
a = sorted(d.items(), key=lambda x:x[0]) # d.items() > [(key, value)] 형태로 반환
``` 
원본 리스트 영향X, **정렬된 새로운 리스트 반환**
모든 iterable(list, tuple, dict, 문자열 등등)에 동작 가능

### 1차원 배열 순서 바꾸기
#### reverse()
```python
seqList = [0,10,20,40]
seqList.reverse()  # [40, 20, 10, 0]
```
#### reversed()
```python
seqList = [1, 2, 4, 3, 5]
seqList = list(reversed(seqList)) # [5, 3, 4, 2, 1]
```

### 2차원 배열 행, 열 바꾸기
#### for문 사용
```python
re = [[0]*n for _ in range(n)]
for i in range(n):
    for j in range(n):
        re[i][j] = scores[j][i]
```
#### zip() 사용
```python
mylist = [[1, 2, 3], [4, 5, 6], [7, 8, 9]]
new_list = list(map(list, zip(*mylist)))
```

## set
```python
s1 = set('abcd')    # {'a', 'b', 'c', 'd'}
len(s1)             # 4
s2 = {'c','f','g'}
s1 - s2             # {'a', 'b', 'd'} 차집합
s1 & s2             # {'c'} 교집합
s1 | s2             # {'a', 'b', 'c', 'd', 'f', 'g'} 합집합

s = set()
s.add(2)            # 추가
s.remove(2)         # 삭제. 요소 없을 시 에러
s.discard(3)        # 삭제. 요소 없을 시 무시
a = s.pop()         # 임의의 값 삭제 & 리턴
s.clear()           # 모든 값 삭제
s3 = s.copy()       # 집합 복제해 리턴

# is로 시작하는 함수는 True or False 리턴
s1.isdisjoint(s2)   # 공통 원소가 없는가?
s1.issubset(s2)     # 부분집합인가?
s1.issuperset(s2)   # 확대집합인가?

# update가 붙은 함수는 원본 데이터를 변경
s3 = s1.union(s2)           # 합집합 만들어 리턴
s1.update(s2)               # 합집합 만들어 s1 수정
s3 = s1.difference(s2)      # 차집합 만들어 리턴
s1.difference_update(s2)    # 차집합 만들어 s1 수정

s3 = s1.intersection(s2)            # 교집합 만들어 리턴
s1.intersection_update(s2)          # 교집합 만들어 s1 수정
s3 = s1.symmetric_difference(s2)    # 대칭차 만들어 리턴
s1.symmetric_difference_update(s2)  # 대칭차 만들어 s1 수정

```
### 대칭차
둘 중 한 집합에는 속하지만 둘 모두에는 속하지 않는 원소들의 집합<br>
합집합에서 교집합 뺀 부분<br>


# ASCII 코드 변경
- ascii -> char<br>
```python 
chr(45)
```
- char -> ascii<br>
```python
ord("A")
```



# 자료구조

## heapq
```python
import heapq
room = []
heapq.heappush(room, num)   # num 추가
room[0]                     # minheap
heapq.heappop(room)         # 제일 작은 값 return
```

## queue
queue는 동기화를 위해 만들어져서 deque에 비해 느림
queue 대신 colletions.deque 사용 권장

## deque

```py
import collections
deq = collections.deque()
deq.append(1)       # 우측에 추가
deq.appendleft(1)   # 좌측에 추가
# extend()는 append()와 다르게 iterable 각 요소를 하나씩 추가
deq.extend(iterable)    # iterable : list, tuple, dictionary, str
deq.extendleft(iterable) 
deq.pop()           # 우측 요소 제거 및 반환
deq.popleft()       # 좌측 요소 제거 및 반환
deq.rotate(n)       # deq의 요소들을 n만큼 회전, 음수면 좌측, 양수면 우측으로 회전
```


# 입출력

## map
```py
map(<function>, <iterable>) # iterable : list, tuple, dictionary, str
```
\<iterable> 의 요소를 \<function> 을 적용하여 변환

## 입력
```py
a, b, c = map(int,input().split())  # 1 2 3 입력 > a = 1, b = 2, c = 3
N, M = map(int, sys.stdin.readline().split())       # 자동으로 \n 없이 들어감
li = list(map(int, sys.stdin.readline().rstrip()))  # list에 \n 없이 넣기 위해 rstrip() 사용

```

## split
default : 공백
```py
x = "Hello World"
b = x.split(" ")  
print(b)    # ['Hello', 'World']
```

## rstrip()
right 오른쪽 공백을 제거  
- 여러줄의 입력을 받을때, \n도 같이 들어오게 되는데 이때 사용하면 편리

## lstrip()
left 왼쪽 공백을 제거

## strip()
양쪽 공백을 제거


## 출력
```python
return "%02d:%02d:%02d"%(h,m,s)
return f"{h:02d}:{m:02d}:{s:02d}"
```


# 연산자

## 산술 연산자
|Operator|Description|Example|
|---|---|---|
|+|더하기|a + b = 30|
|-|빼기|a - b = -10|
|*|곱하기|a * b = 200|
|/|나누기|b / a = 2.0|
|%|나머지|b % a = 0|
|**|제곱|a ** c = 1000|
|//|몫|a // c = 3|

## 삼항 연산자
```python
a if 조건식 else b 
```
조건식이 참이면 a, 거짓이면 b

# 반복문

## for문

### for문 하나 한 줄로 작성하기
```python
for i in list1 :
    list2.append(i + 1)

# 한 줄에 작성
list2 = [i + 1 for i in list1]
```

### 이중 for문 한줄로 작성하기
```python
list1 = [1, 2, 3]
list2 = [1, 1, 1]
list3 = []

for i in list1 :
    for j in list2 :
        if i == 1 :
            list3.append(i + j)
        else:
            list3.append(0)

# 한 줄에 작성
list3 = [i + j if i == 1 else 0 for i in list1 for j in list2]

# else문 없다면
list3 = [i + j for i in list1 for j in list2 if i == 1]
```
바깥 for문 먼저 쓰기

### enumerate()
```python
for index, data in enumerate(list):
```
index와 data가 동시에 필요할 때 사용
- list \> [(index1, data1), (index2, data2), ..]
- dict \> {index1: data1, index2: data2, ..}


# sys 모듈
```python
import sys
```

## stdin
```python
from sys import stdin
input = stdin.readline
```

## 재귀
```python
from sys import getrecursionlimit, setrecursionlimit
getrecursionlimit()         # 최대 재귀 깊이 확인, 백준 기본 1000
setrecursionlimit(100000)   # 최대 재귀 깊이 변경
```


# collections 모듈
```python
import collections
```

## defaultdict()


# itertools 모듈
```python
import collections
```
## Counter(str|list|값=개수) 클래스
인자에서 동일한 문자/요소의 개수를 세주는 클래스<br>
결과는 dictionary 형태, 개수 내림차순으로 전달 { 값:개수 }
인자로 값=개수를 넣을 시 list를 반환
```python
collections.Counter(a=2, b=3, c=2) # ['a', 'a', 'b', 'b', 'b', 'c', 'c']
```

### most_common(n)
```python
Counter('hello').most_common(1) # [('l', 2)]
```
가장 개수가 많은 n개의 데이터만 리턴<br>
리스트 안의 튜플 형태로 반환

### update()
Counter결과에 인자의 결과 추가하여 갱신
```python
a = collections.Counter()
a.update("abcdefg")
a.update({'f':3, 'e':2})
```

### elements()
모든 요소들 반환



# functools 모듈
```python
import functools
```

## reduce() 함수
여러 개의 데이터를 대상으로 주로 누적 집계를 내기 위해 사용
```python
reduce(집계 함수, 순회 가능한 데이터[, 초기값])
reduce(lambda a, b: a + b, list, 0)
```


# re 모듈
```python
import re
```


# 정규 표현식
## 메타 문자
메타 문자 : 기존의 의미가 아닌 특별한 용도로 사용하는 문자<br>
`. ^ $ * + ? { } [ ] \ | ( )`

### 문자 클래스 [ ]
[abc] -> "a, b, c 중 한 개의 문자와 매치"

```python
# 모든 대문자를 대응되는 소문자로 치환
answer = new_id.lower()
# 알파벳 소문자, 숫자, 빼기(-), 밑줄(_), 마침표(.)를 제외한 모든 문자를 제거
answer = re.sub('[^a-z0-9\-_.]','',answer)
# 마침표(.)가 2번 이상 연속된 부분을 하나의 마침표(.)로 치환
answer = re.sub('\.+','.',answer)
# 마침표(.)가 처음이나 끝에 위치한다면 제거
answer = re.sub('^[.]|[.]$', '', answer)
```



# 오류 발생
## 들여쓰기 오류
`IndentationError: unindent does not match any outer indentation level`
들여쓰기에 tab과 space를 섞어서 사용됨!<br>
처음에 tab를 사용했으면 계속 tab으로 들여쓰기를 해야 함<br>


<!-- 
```python

``` -->
