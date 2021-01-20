# C++

## cin, cout
```c++
ios::sync_with_stdio(false);	// 속도를 좀 더 빨리 해줌
cin.tie(0); cout.tie(0);	    // 왜 하는 지? 알아보기

cout << endl;       // endl 되게 느림 \n 사용해라
cout << '\n';
```
위 2개를 쓰면 printf, scanf를 쓰는 건 조심! 

## 변수
웬만하면 전역변수 사용 -> 자동으로 0으로 초기화됨
|영역|설명|
|--|--|
|데이터영역|데이터영역이 스택영역보다 훨씬 큼. 전역변수 저장|
|스택영역|지역변수 저장|

## 자료구조

### stack
top은 보기
pop은 빼기(볼 수 없음)
empty는 사이즈 있으면 0
임의접근 불가

### heap 
덩어리.. 원소들이 들어있는 뭉텅이

### queue
임의접근 불가

### deque
deque만 임의접근 가능, 근데 쓸일이 별로 없음

### priority_queue
기본이 최대힙
priority_queue<int, vector<int>, less<int> > pq	: 최대힙이 나옴
priority_queue<int, vector<int>, greater<int> > pq	: 최소힙

### set
집합

### map
key값으로 value찾는 hashmap 같은 것

### vector 
메모리 용량 줄이기 가능

### pair<T, T> p
operator< : first 가 같을 때 second 비교
first를 먼저 비교

### tuple
pair 보다 여러 개를 묶을 때 사용
쓸 바엔 다른거 써


## 문자열처리
\<string> vs \<string>

### \<string>
string 형 쓰려면 \<string>
\<string>
```c++
str.length()
str.c_str()         // string을 char 배열로
str.compare(str2)   // 같은거 인지 아닌지
atoi(str.c_str())   // cstdlib에 존재
```
임의 접근 가능 : (예시 str[3] : 그러나 char가 아님 주의)

### \<string>
char배열
임의 접근 가능
```c++
strtok(어려워)      // null일때까지 앞에 토큰 반환
strcmp(str1, str2)  // (-) str1에서 str2를 빼는 형식, -1,0,1(뒤에 문자가 크면 마이너스)
strcpy(str1, str2)  // (=) str1이 str2로 바뀜
strcat(str1, str2)  // (+=) str1에 str2가 추가. (abc\n, def\n) > abcdef\n 
strlen(str)         // str 길이. strlen쓸때마다 for문이 수행되니까 안좋음
for(int i=0;i<strlen(str);i++) {}   // 사용하지 말것
len = strlen(str);                  // 대안
for(int i=0;i<len;i++) {}
str[i] !=0          // null의 아스키코드 값은 0

atoi("123")         // 123  문자열을 숫자로
atoi("-123")        // -123
atoi("123abc")      // 123
atoi("abc123")      // 0    앞에서부터 문자를 처리하기 때문에 앞의 값이 문자면 0으로 return됨
```



















